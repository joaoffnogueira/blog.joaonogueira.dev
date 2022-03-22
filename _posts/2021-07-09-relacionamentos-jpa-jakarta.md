---
title: Relacionamentos na JPA - Jakarta EE
author: João F. F. Nogueira
date: 2021-07-09 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [jakarta, java]
toc: true
---

> Baseado nos cursos da Softblue

# Relacionamentos em JPA

• O JPA é capaz de trabalhar com relacionamentos entre entidades

– Em orientação a objetos, um relacionamento existe quando um objeto da classe A possui um atributo que referencia um objeto B, de outra classe

– No modelo relacional, um relacionamento existe quando uma tabela A referencia uma tabela B através de uma chave estrangeira (foreign key)

![Exemplo na Orientação a Objetos](/posts/2021-07-09-2.png){: width="100" height="100" }

![Exemplo na Orientação a Objetos](/posts/2021-07-09-3.png){: width="100" height="100" }

![Exemplo no Modelo Relacional](/posts/2021-07-09-4.png){: width="100" height="100" }

## Definindo Relacionamentos

• Os relacionamentos são definidos nas entidades através de anotações

| Annotation  | Tipo de Relacionamento |
|-------------|------------------------|
| @OneToOne   | Um-para-Um             |
| @OneToMany  | Um-para-Muitos         |
| @ManyToOne  | Muitos-para-Um         |
| @ManyToMany | Muitos-para-Muitos     |

• Outras anotações utilizadas em relacionamentos

| Annotation  | Tipo de Relacionamento        |
|-------------|-------------------------------|
| @JoinColumn | Coluna para chave estrangeira |
| @JoinTable  | Tabela auxiliar para o join   |

pedido.java

```java
@OneToOne
@JoinColumn(name = "pagamento_id")
private Pagamento pagamento;

@ManyToOne
@JoinColumn(name = "cliente_id", nullable = false)
private Cliente cliente;

@ManyToMany
@JoinTable(name = "PEDIDO_PRODUTO", 
  joinColumns = @JoinColumn(name = "pedido_id"),
  inverseJoinColumns = @JoinColumn(name = "produto_id"))
private List<Produto> produtos;
```

## Navegabilidade dos Relacionamentos

• Relacionamentos unidirecionais

– É possível navegar do lado A para o B

– Não é possível navegar do lado B para o A

• Relacionamentos bidirecionais

– É possível navegar do lado A para o B

– É possível navegar do lado B para o A

![Relacionamento Bidirecional](/posts/2021-07-09-5.png){: width="100" height="100" }

![Relacionamento Unidirecional](/posts/2021-07-09-6.png){: width="100" height="100" }

## Dono do Relacionamento

• Em relacionamentos bidirecionais, um dos lados do relacionamento é o dono do relacionamento (relationship owner)

| Tipo               | Dono                                              |
|--------------------|---------------------------------------------------|
| Um-para-Um         | Lado que possui a chave estrangeira (foreign key) |
| Um-para-Muitos     |  Lado “muitos”                                    |
| Muitos-para-Um     | Lado “muitos”                                     |
| Muitos-para-Muitos | A critério da aplicação                           |

![Dono do Relacionamento](/posts/2021-07-09-7.png){: width="100" height="100" }

![Muitos-Para-Muitos](/posts/2021-07-09-8.png){: width="100" height="100" }

## Relacionamentos Eager e Lazy

• Quando uma entidade que possui relacionamentos é carregada, a JPA permite duas abordagens

– Carregar automaticamente as entidades dos relacionamentos (EAGER)

– Carregar os relacionamentos apenas quando eles forem necessários (LAZY)

– A JPA assume um padrão 

• @OneToOne e @ManyToOne = EAGER

• @OneToMany e @ManyToMany = LAZY

```java
public class Pedido {
  @OneToOne(fetch = FetchType.EAGER)//O pagamento será carregado automaticamente
  private Pagamento pagamento;

public class Pedido {
  @OneToOne(fetch = FetchType.LAZY)//O pagamento não será carregado automaticamente, Será carregado apenas quando for utilizado
  private Pagamento pagamento;

public class Cliente {
  @OneToMany(fetch = FetchType.EAGER)//Os pedidos serão carregados automaticamente
  private List<Pedido> pedidos;

public class Cliente {
  @OneToMany(fetch = FetchType.LAZY)//Os pedidos não serão carregados automaticamente. Serão carregados apenas quando forem utilizados
  private List<Pedido> pedidos;
```

• Entre EAGER ou LAZY, não existe uma opção melhor ou pior

– Vai depender de cada situação

• EAGER

– Reduz o acesso ao banco de dados para leitura de dados

– Ocupa mais memória

• LAZY

– É preciso fazer vários acessos ao banco de dados para obter os dados conforme a necessidade

– Ocupa menos memória
