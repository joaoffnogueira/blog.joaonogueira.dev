---
title: Segurança em Jakarta EE
author: João F. F. Nogueira
date: 2021-10-01 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [jakarta, java]
toc: true
---

# Os Principais Conceitos de Segurança

Autenticação: Garante que alguém é realmente quem diz ser;

Autorização: Verifica a possibilidade de acesso de alguém autenticado;

Confidencialidade e Integridade: Garantem que os dados não serão lidos ou alterados durante o tráfego.

## Autenticação

• Garante a identidade de alguém

– Usuário e senha

– Leitura biométrica

– Certificado digital

• Até o Java EE 7, o processo de autenticação não era padronizado

– Cada container implementava da sua forma

• A partir do Java EE 8, foi criada a Java EE Security API

– Padronização no processo de autenticação

## Autorização

• Depois de autenticado, o usuário pode acessar o recurso protegido?

• Em Java EE, a autorização é padronizada na especificação

– Todos os containers seguem o mesmo padrão

## Definindo os Roles de Acesso

• Um role representa um grupo de acesso

• Os roles da aplicação podem ser definidos no arquivo web.xml

```xml
<security-role>
  <role-name>gerente</role-name>
</security-role>
<security-role>
  <role-name>diretor</role-name>
</security-role>
```

• Ou via anotação

```java
@DeclareRoles({ "admin", "guest" })
```

## Protegendo Recursos

• Recursos são protegidos em Java EE com base em mapeamentos de URL e HTTP method feitos no web.xml

```xml
<web-app>
  <security-constraint>
    <web-resource-collection>
      <web-resource-name>admin pages</web-resource-name>
      <url-pattern>/admin/*</url-pattern>
      <http-method>GET</http-method><!--Mapeamento e HTTP method-->
    </web-resource-collection>
    <auth-constraint>
      <role-name>diretor</role-name><!--Roles autorizados-->
    </auth-constraint>
  </security-constraint>
</web-app>
```

## Tipos de Autenticação

• Ao acessar um recurso protegido, o navegador precisa solicitar as credenciais do usuário de alguma forma

• Essas são as 3 formas de autenticação mais usadas:

| Forma       | Descrição                                                                                                                          |
|-------------|------------------------------------------------------------------------------------------------------------------------------------|
| BASIC       | O navegador abrirá uma janela padrão solicitando as credenciais                                                                    |
| FORM        | O usuário será redirecionado para uma página  customizada para fornecer as credenciais                                             |
| CUSTOM FORM | O usuário também fornecerá as credenciais em uma  página customizada, mas o processo de autenticação é  controlado por programação |

### Autenticação BASIC

• O container cuida de todo o processo de autenticação

• Uma janela aberta pelo próprio navegador solicita o usuário e a senha

```java
@BasicAuthenticationMechanismDefinition
  public class Config {
}
```

### Autenticação FORM

• Páginas customizadas para solicitar as credenciais

– Uma página solicitando usuário e senha

– Uma página para que haja o redirecionamento caso os dados digitados sejam inválidos

```java
@FormAuthenticationMechanismDefinition(
  loginToContinue = @LoginToContinue(
    loginPage = "/login.faces",
    errorPage = "/error.faces"
  )
)
public class Config {
}
```

• O formulário de login deve seguir algumas regras

```html
<html>
  <body>
    <form method="POST" action="j_security_check">
    Usuário: <input type="text" name="j_username"><br />
    Senha: <input type="password" name="j_password"><br />
    <input type="submit" value="Login">
    </form>
  </body>
</html>
```

### Autenticação CUSTOM FORM

• Também baseado em páginas customizadas para o fornecimento de credenciais

```java
@CustomFormAuthenticationMechanismDefinition( 
  loginToContinue = @LoginToContinue(
    loginPage = "/login.faces",
    errorPage = "/error.faces"
  )
)
public class Config {
}
```

• O formulário é livre, não precisa seguir nenhuma regra

```html
<html>
  <body>
    <h:form>
      Usuário: <h:inputText value="#{loginBean.userName}" /><br />
      Senha: <h:inputSecret value="#{loginBean.password}" /><br /> 
      <h:commandButton value="Login" action="#{loginBean.login}" />
    </h:form>
  </body>
</html>
```

• O login é feito via programação usando um objeto `SecurityContext`

```java
@Named
@RequestScoped
public class LoginBean implements Serializable {
  @Inject
  private SecurityContext securityContext;
  private String userName;
  private String password;
  public String login() {
    //...
    AuthenticationStatus status = securityContext.authenticate(request, response, authParams);
    //...
  }
}
```

#### O objeto SecurityContext

• A Java EE Security API introduziu o conceito de SecurityContext

– Um objeto onde detalhes do usuário autenticado podem ser obtidos via programação

| Método                   | Descrição                                                              |
|--------------------------|------------------------------------------------------------------------|
| authenticate()           | Autentica um usuário fornecendo suas credenciais                       |
| getCallerPrincipal()     | Retorna o objeto Principal do usuário autenticado                      |
| isCallerInRole()         | Verifica se o usuário autenticado pertence a  determinado grupo        |
| hasAccessToWebResource() | Verifica se o usuário autenticado tem acesso a  determinada página web |

• Um objeto SecurityContext é obtido através de injeção de dependência feita pelo CDI

```java
@Inject
private SecurityContext securityContext;
```

• Ele pode ser obtido em diversos tipos de componentes do Java EE

– EJBs

– Servlets

– Filters

– JSF Beans

## Segurança em EJBs

• A anotação @RolesAllowed controla quem pode acessar os métodos de um EJB

```java
@Stateless
@RolesAllowed("admin")//Apenas usuários do grupo admin podem chamar m1() e m2()
public class MyBean {
  public void m1() {
  }
  public void m2() {
  }
}
```

• A anotação @RolesAllowed também pode ser usada em métodos

```java
@Stateless
@RolesAllowed("admin")
public class MyBean {
  public void m1() {
  }
  @RolesAllowed("guest")//m2() pode ser chamado por usuários do grupo guest
  public void m2() {
  }
}
```

## Confidencialidade e Integridade

• A confidencialidade previne que os dados sejam lidos durante o tráfego na rede

• A integridade garante que os dados não serão alterados enquanto trafegam pela rede

• O HTTPS dá essas garantias

– Hypertext Transfer Protocol Secure

Antes de serem enviados, os dados são criptografados.

Apenas o servidor de destino consegue descriptografar os dados

### HTTPS e Java EE

• Primeiramente, é necessário configurar o servidor para que ele aceite conexões do tipo HTTPS

• Depois, no web.xml, basta definir que o acesso a determinado recurso necessita de HTTPS

```xml
<web-app>
  <security-constraint>
    <web-resource-collection>
      <web-resource-name>admin pages</web-resource-name>
      <url-pattern>/admin/*</url-pattern>
    </web-resource-collection>
    <user-data-constraint>
      <transport-guarantee>CONFIDENTIAL</transport-guarantee><!--Garante o uso de HTTPS sempre que uma URL no padrão /admin/* for acessada-->
    </user-data-constraint>
  </security-constraint>
</web-app>
```

> Baseado nos cursos da Softblue