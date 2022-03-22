---
title: JavaFX - Conceitos e Fundamentos no Java
author: João F. F. Nogueira
date: 2021-02-26 09:00:00 -0300
categories: [Estudos-faculdade]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# O JavaFX

* JavaFX é uma tecnologia composta por um conjunto de APIs

* Criação de rich client applications

– Ex: formulários, gráficos, multimídia, gráficos 2D e 3D, etc.

* JavaFX é totalmente feito em Java

– Integração com as APIs do Java já conhecidas

– Suporte multiplataforma

# Arquitetura do JavaFX

![Arquitetura do JavaFX](/posts/2021-02-26-1.png){: width="100" height="100" }

# Estrutura de cena

![Estrutura de cena](/posts/2021-02-26-2.png){: width="100" height="100" }

Apenas uma cena pode estar visível por vez

```java
public class MainApp extends Application {
  public static void main(String[] args) {
    launch(args);
  }
  @Override
  public void init() {
    //...
  }
  @Override
  public void start(Stage primaryStage) {
    Button btn = new Button("Aperte aqui");
    StackPane root = new StackPane();
    root.getChildren().add(btn);
    Scene scene = new Scene(root, 400, 300);
    primaryStage.setTitle("JavaFX App");
    primaryStage.setScene(scene);
    primaryStage.show();
  }
} 
```

![Hello World](/posts/2021-02-26-3.png){: width="100" height="100" }

# Layout panes

* Os nós devem ser organizados na tela na montagem da interface gráfica

* A melhor forma de organizá-los é através dos painéis de layout

* Tipos

– HBox

– VBox

– BorderPane

– AnchorPane

– StackPane

– GridPane

– FlowPane

– TilePane

## HBox

* Organiza os nós horizontalmente

![HBox](/posts/2021-02-26-4.png){: width="100" height="100" }

```java
HBox box = new HBox();
box.getChildren().add(node);
```

## VBox

* Organiza os nós verticalmente

![Vbox](/posts/2021-02-26-5.png){: width="100" height="100" }

```java
VBox box = new VBox();
box.getChildren().add(node);
```

## BorderPane

* 5 regiões: top, bottom, left, right, center

![BorderPane](/posts/2021-02-26-6.png){: width="100" height="100" }

```java
BorderPane pane = new BorderPane();
pane.setTop(node1);
pane.setBottom(node2);
pane.setLeft(node3);
pane.setRight(node4);
pane.setCenter(node5);
```

## AnchorPane

* Permite ancorar os nós nos cantos

![AnchorPane](/posts/2021-02-26-7.png){: width="100" height="100" }

```java
AnchorPane pane = new AnchorPane();
pane.getChildren().addAll(node1, node2);
AnchorPane.setRightAnchor(node1, 5.0);
AnchorPane.setTopAnchor(node1, 5.0);
AnchorPane.setLeftAnchor(node2, 5.0);
AnchorPane.setBottomAnchor(node2, 5.0);
```

## StackPane

* Empilha os nós

![StackPane](/posts/2021-02-26-8.png){: width="100" height="100" }

```java
StackPane pane = new StackPane();
pane.setAlignment(Pos.CENTER_RIGHT);
StackPane.setMargin(btn3, new Insets(20, 20, 0, 0));
pane.getChildren().addAll(node1, node2, node3);
```

## GridPane

*  Organiza em linhas e colunas

![GridPane](/posts/2021-02-26-9.png){: width="100" height="100" }

```java
GridPane pane = new GridPane();
pane.add(node1, 0, 0);
pane.add(node2, 0, 1);
pane.add(node3, 1, 0);
pane.add(node4, 1, 1);
```

## FlowPane

* Organiza em linhas ou colunas e faz a quebra se não houver espaço

![FlowPane](/posts/2021-02-26-10.png){: width="100" height="100" }

```java
FlowPane pane = new FlowPane();
pane.setOrientation(Orientation.HORIZONTAL);
pane.getChildren().addAll(
node1, node2, node3, node4, node5, node6);
```

## TilePane

* Organiza os nós como o FlowPane, mas em células com o mesmo tamanho

![TilePane](/posts/2021-02-26-11.png){: width="100" height="100" }

```java
TilePane pane = new TilePane();
pane.setOrientation(Orientation.VERTICAL);
pane.getChildren().addAll(node1, node2, node3, node4, node5, node6);
```

# Controles

![Controles](/posts/2021-02-26-12.png){: width="100" height="100" }

![Controles](/posts/2021-02-26-13.png){: width="100" height="100" }

# Eventos

* Eventos são ações disparadas em resposta a alguma ação do usuário

– Tecla pressionada, mouse clicado, janela redimensionada, etc.

* Alguns exemplos

– KeyEvent

– MouseEvent

– ActionEvent

– WindowEvent

## Event Handlers

* Quando um evento é disparado, determinado código pode ser executado em resposta à ocorrência do evento

* Este código é um event handler

```java
Button btn = new Button("OK");
btn.setOnAction(new EventHandler<ActionEvent>() {
  @Override
  public void handle(ActionEvent event) {
    //...
  }
});
```

* EventHandler é uma interface funcional

* É possível utilizar expressões lambda

```java
Button btn = new Button("OK");
btn.setOnAction(event -> doSomething());
```
