---
title: Controle Transacional em EJBs - Jakarta EE
author: João F. F. Nogueira
date: 2021-07-30 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [jakarta, java]
toc: true
---

> Baseado nos cursos da Softblue

# Transações

• Uma transação é um conjunto atômico de operações

– TUDO é executado ou NADA é executado

• O objetivo é manter a consistência das informações

COMMIT: Efetiva as mudanças no BD

ROLLBACK: Desfaz as mudanças anteriores

## Transações em Java EE

• O Java EE tem um serviço de gerenciamento de transações

• Este gerenciamento pode ser de 2 tipos:

– CMT (Container-Managed Transactions)

• Gerenciadas pelo EJB container

– BMT (Bean-Managed Transactions)

• Gerenciadas manualmente, via programação

### Container-Managed Transactions

• São gerenciadas pelo container

• Suportadas por EJBs

– Session Beans e Message-Driven Beans

• A transação começa quando o método inicia e encerra quando o método termina

– O desenvolvedor não precisa demarcar a transação

• É o tipo padrão de gerenciamento dos EJBs

```java
@Stateless
public class MyBean {
  @PersistenceContext
  private EntityManager em;
  public void m1() {//Se o método terminar normalmente: COMMIT
    //OP 1
    //OP 2
    //OP 3
}
public void m2() {//Se o método lançar uma system exception: ROLLBACK
    //OP 1
    //OP 2
    //OP 3
}
}
```

#### Rollback em CMT

• Existem 2 formas de executar um rollback

– Lançar uma system exception a partir do método do EJB

– Chamar o método setRollbackOnly()

```java
@Stateless
public class MyBean {
  @PersistenceContext
  private EntityManager em;
  @Resource
  private EJBContext ejbContext;
  public void m1() {
    //OP 1
    //OP 2
    ejbContext.setRollbackOnly();
  }
}
```

#### Transaction Attributes

• Controlam o escopo da transação

– O que acontece com a transação quando um método chama outro método

• Tipos

– Required

– Requires New

– Mandatory

– Not Supported

– Supports

– Never

• Uso da anotação `@TransactionAttribute`

– Na classe

• Todos os métodos do EJB vão usar este transaction attribute

– No método

• Apenas o método anotado do EJB vai usar este transaction attribute

• Se a anotação existir na classe e no método, o que foi definido no método tem precedência

Attribute: Required

![Attribute: Required](/posts/2021-07-30-2.png){: width="100" height="100" }

Attribute: Requires New

![Attribute: Requires New](/posts/2021-07-30-3.png){: width="100" height="100" }

Attribute: Mandatory

![Attribute: Mandatory](/posts/2021-07-30-4.png){: width="100" height="100" }

Attribute: Not Supported

![Attribute: Not Supported](/posts/2021-07-30-5.png){: width="100" height="100" }

Attribute: Supports

![Attribute: Supports](/posts/2021-07-30-6.png){: width="100" height="100" }

Attribute: Never

![Attribute: Never](/posts/2021-07-30-7.png){: width="100" height="100" }

### Bean-Managed Transactions

• São gerenciadas pelo desenvolvedor, via programação

• Permitem um controle mais fino a respeito do escopo da transação

– Métodos que usam CMT são limitados: ou o método inteiro executa em uma transação ou em nenhuma

```java
@Stateless
@TransactionManagement(TransactionManagementType.BEAN)//Define o bean como BMT
public class MyBean {
  @Resource
  private UserTransaction ut;//Gerenciamento da transação
  public void m1() {
    ut.begin();//Inicia a transação
    try {
      ...
      ...
      ut.commit();//commit() e rollback() encerram a transação
    } catch(Exception e) {
      ut.rollback();
    }
  }
}
```

## Extended Persistence Context

• O manuseio de entidades na JPA é feito de um contexto de persistência

• Por padrão, esse contexto tem o mesmo tempo de duração da transação

```java
@Stateless
public class MyBean {
  @PersistenceContext
  private EntityManager em;
  public void m1() {
    ...
    ...
    ...
  }
}
```

Assim que a transação termina, o contexto de persistência é encerrado

Todas as entidades gerenciadas pela JPA são desatachadas

• Esse comportamento pode ser alterado

```java
@Stateful
public class MyBean {
  @PersistenceContext(type = PersistenceContextType.EXTENDED)
  private EntityManager em;
  public void m1() {
    ...
    ...
    ...
  }
}
```

O ciclo de vida do contexto de persistência é o mesmo do EJB

Chamadas subsequentes de métodos usam o mesmo contexto de persistência

Só tem sentido em Stateful Session Beans

## EJBs & Exceções

• Existem 2 tipos de exceções

– System Exception

  • RuntimeExcetion (ou subclasse)

  • RemoteException (ou subclasse)

– Application Exception

  • As outras que não são system exceptions

• Quando uma exceção é lançada, o que o EJB container faz?

  – System Exception

    • Se houver uma transação ativa

      – Rollback da transação

      – Empacota a exceção em uma exceção do tipo EJBTransactionRolledBackException e lança

    • Se não houver uma transação ativa

      – Empacota a exceção em uma exceção do tipo EJBException ou RemoteException e lança

– Application Exception

  • Lança a exceção (sem empacotar)

• É possível fazer com que uma system exception se comporte como uma application exception

```java
@ApplicationException(rollback = true)
public class MyException extends RuntimeException {
//...
}
```

• Quando um bean lança uma system exception, a instância dele é destruída

  – Session Beans

    • Stateful

    • Stateless

  – Message-Driven Beans
