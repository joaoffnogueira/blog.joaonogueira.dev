---
title: Anotações sobre Javascript
author: João F. F. Nogueira
date: 2020-12-18 09:00:00 -0300
categories: [Português, Estudos]
tags: [javascript, web]
toc: true
---

**Comentários**

// This is an in-line comment.

/* This is a

multi-line comment */

 

**Declaração de variáveis**

var ourName;

 

Tipos: undefined, null, boolean, string, symbol, bigint, number, and object.

Variable names can be made up of numbers, letters, and $ or _, but may not contain spaces or start with a number.

In JavaScript all variables and function names are case sensitive.

Write variable names in JavaScript in camelCase.

In JavaScript, you can escape a quote from considering it as an end of string quote by placing a backslash (\) in front of the quote.

var sampleStr = "Alan said, \"Peter is learning JavaScript\".";

## Introdução
-   ECMAScript é uma especificação de linguagem script criada pela Ecma International, utilizada por linguagens como: ActionScript, JScript e Javascript.
-   Javascript é uma linguagem de funções de primeira classe e funções de ordem maior, pois é possível atribuir funções a variáveis, retornar funções de outras funções e passar funções como parâmetro para outras funções
Linguagem de programação executada no lado cliente. Código desprotegido. Linguagem interpretada.
Script -- interpretada em tempo de execução
Tipagem fraca e dinâmica
Case Sensitive
Comentários: //linha /* bloco */
Babeljs.io para converter implementações novas em antigas
-   Closure ou escopo léxico é a capacidade da função "lembrar" do seu contexto de criação.
-   Hoisting ou içamento é a capacidade do JavaScript elevar a criação de variáveis e funções ao topo do escopo de suas criações. Existem dois tipos de Hoisting: hoisting de variável e hoisting de função.
Curryng e Imutabilidade

**Dentro do HTML**

```html
<script                                                                      
	function nomeDaFuncao (parametros) {codigo}
</script                                                                     
<script language="javascript" src=""</script                          
<img src="" onmousemove="nomeDaFuncao" onmouseout="" onclick=""</img
```

## Comandos iniciais
```javascript
  window.alert("Olá mundo");                                          
  window.prompt("Olá mundo");                                         
  window.confirm("Olá mundo?");                                       
  document.write("Olá mundo, hoje é dia" + Date());                   
  document.getElementById("").src = "";                             
  console.log('')                                                     
  Number.parseInt(n) //converter string em int                          
  Number.parseFloat(n) //converter string em float                      
  Number(n) //converter string para número com tipo altomático          
  String(n) ou n.toString() //converter número para String              
  typeof var //retorna o tipo da variável                               
  throw new Error ('mensagem de erro') // indica o erro no console   
```

## Atributos e funções internas

+------------------------------------------------------------------------------------------------------------------+
| ** **.length: tamanho da string                                                                                  |
|                                                                                                                  |
| .toUpperCase(): string em letras maiúsculas                                                                      |
|                                                                                                                  |
| .toLowerCase(): string em letras minúsculas                                                                      |
|                                                                                                                  |
| .toFixed(numero de casas).replace('.',','): para definir quantas casas decimais, e trocar ponto por vírgula. |
|                                                                                                                  |
| .toLocaleString('pt-br' , {style: 'currency', currency: 'BRL'}) //para exibir na forma monetária           |
|                                                                                                                  |
| .includes(""):verificação de string, resultado bool                                                            |
|                                                                                                                  |
| .indexOf('busca', posicaoInicial): mapeamento da string para retornar busca                                    |
|                                                                                                                  |
| .lastIndexOf() busca reversa, começando do fim                                                                   |
|                                                                                                                  |
| .substring(,): retornar uma parte da string                                                                      |
|                                                                                                                  |
| .replace(,)                                                                                                      |
|                                                                                                                  |
| .slice(,) para criar um novo array, valor final não incluso                                                      |
|                                                                                                                  |
| .push() inclui um novo elemento no final do array                                                                |
|                                                                                                                  |
| .pop() remove o ultimo item do array                                                                             |
|                                                                                                                  |
| .sort() ordenar elementos                                                                                        |
|                                                                                                                  |
| .filter()                                                                                                        |
|                                                                                                                  |
| .forEach()                                                                                                       |
|                                                                                                                  |
| .getHour()                                                                                                       |
|                                                                                                                  |
| .getFullYear()                                                                                                   |
|                                                                                                                  |
| .innerHTML para editar o html                                                                                    |
|                                                                                                                  |
| .innerText para editar texto simples na página                                                                   |
|                                                                                                                  |
| .createElement                                                                                                   |
|                                                                                                                  |
| .appendChild() adicionar elemento filho                                                                          |
|                                                                                                                  |
| .focus()                                                                                                         |
|                                                                                                                  |
| .disabled = true//false                                                                                          |
|                                                                                                                  |
| new Date()                                                                                                       |
+------------------------------------------------------------------------------------------------------------------+

Tanto as propriedades .value, .textContent, e .innerHTML servem para definir um novo valor ou recuperar o valor atual.

## Tipos de dados

string, number, boolean, null, undefined, symbol, Object, Function, Array.

```javascript
var cria variáveis globais                                   
let cria variáveis locais                                    
var alfa = "strings";                                      
var num = 50.03;                                             
var bol = true;                                              
var objetoarray = new Array("Maçã", "Laranja", "Uva"); 
var objeto = new Object ()                                   
const a = 3.14
Array é um objeto. objeto[0]. objeto[1]. objeto[2]     
```
Nomes de variáveis podem começar com letra, $ ou _. Não podem começar com números, mas podem conter números, acentos e símbolos. Não podem conter espaços e nem usar palavras reservadas.
Template string: uma forma mais fácil de concatenar strings: ${s}

**Valores falsos**

false: the boolean value false
0: the number zero
'': the empty string, a string with no characters
NaN : stands for "Not a Number", usually caused by math errors
undefined: a variable's value before it is assigned a value
null: a blank value that can be assigned to a variable

**Operadores**

 

= atribuição

+ soma ou concatenação de strings

- subtração

* multiplicação

/ divisão real

% resto da divisão inteira

** potenciação

Precedências: () *** / % o que vier antes da esquerda pra direita+-

++ incremento de 1(executado depois de outras operações se estiver do lado direito da variável. pode ser ++x)

-- decremento de 1(igual anterior)

+= soma com o valor a direita e atualiza a variável

-= subtrai o valor a direita e atualiza a variável

*= same

/= same

%= same

**Relacionais**

== mesmo valor mesmo que tipos diferentes

=== mesmo valor e mesmo tipo

!= diferentes em valor

!== diferentes em valor e em tipo

< menor que

> maior que

<= menor igual

>= maior igual

**Lógicos**

! negação

& e

| ou

&& e verificando a primeira condição e já resultando falso se for o caso

|| ou verificando a primeira condição e já resultando verdadeiro se for o caso

Precedência: aritméticosrelacionais!&&||


Comandos de decisão e controle

**Comandos de decisão**

if(condição) {}

else if(condição) {}

else{}

switch(valor){case 0 ...break; default}

 

**Operador ternário substitui if else**

test ? doThisIfTrue : elseDoThis

 

**Comandos de repetição - laços - iterações**

for(inicialização; condição; incremento) {}

for(elemento in array) {}

while(condição) {}

do {} while(condição)

 

**Comandos de controle**

break interrompe repetição

continue interrompe a execução atual da repetição mas permite a continuação do laço

 

 

Funções e exceções


 

**Criando funções**

function nomeDaFuncao(parâmetros) {}

 

**Funções**

Chamada - parâmetro - ação - retorno

Função literal:

function ação (param) {

return res

}

ação(5) //chamada

Funções podem ser tratadas como objetos, e receber atributos. Podem ser anônimas. Podem ser passadas como parâmetro para outras. Todas as funções possuem um atributo .name. Apenas funções criam escopos de variáveis (ECMA antigo). Nas versões novas o let cria variáveis em escopo de função. As funções também possuem o atributo .argument que apresenta os parâmetros que foram passados.

A herança em JavaScript ocorre por meio do seu protótipo.

Funções auto executáveis: Immediately-invoked function expression IIFE:

(function(){

}) {}

Funções que se auto invocam, para não poluirmos o escopo global desnecessariamente. É interessante perceber que esse tipo de função só tem valor quando estamos desenvolvendo para o browser, onde tudo fica "pendurado" no objeto principal chamado window. Se estivéssemos desenvolvendo para NodeJS, por exemplo, essa preocupação não existiria.

 

**Função construtora de objetos personalizados**

+----------------------------+--------------------------------------------------------------------------------------------------------------------+
| function Construtora() {   | funções construtoras com nomes em letra maiúscula, por convenção. Atributos criados com var são locais e privados. |
|                            |                                                                                                                    |
| var atributoPrivado        |                                                                                                                    |
|                            |                                                                                                                    |
| this.atributo = 1;         |                                                                                                                    |
|                            |                                                                                                                    |
| this.metodo = function(){} |                                                                                                                    |
|                            |                                                                                                                    |
| }                          |                                                                                                                    |
+----------------------------+--------------------------------------------------------------------------------------------------------------------+

 

para criar os objetos sempre use o **new** Construtora(), para evitar problemas de referência com o this.

 

**Tratando exceções**

try{

//código a ser testado

} catch(e) {

//tratamento do erro

}

DOM

**Entendendo o DOM**

Document Object Model - apenas no navegador

Árvore DOM: window (location; document; history)

document(html) //// html(head; body)

Métodos de acesso:

-   Por marca: getElementsByTagName('tag')[n]

-   Por ID: getElementById()

-   Por Nome: getElementsByName()[]

-   Por Classe:getElementsByClassName()[]

-   Por Seletor: querySelector('identificação no css') /// querySelectorAll('body.caixa')

-   .[name].value

 

**Acessando atributos no HTML**

Algumas propriedades podem ser acessadas e modificadas usando o DOM 0 e DOM 2

+-----------------------------------------------+
| $elemento.id //0                             |
|                                               |
| $elemento.maxLength = 10 //0                 |
|                                               |
| $elemento.getAttribute('readonly') //2     |
|                                               |
| $elemento.setAttribute('id', 'myId') //2 |
+-----------------------------------------------+

 

 

**Eventos DOM**

Listeners no JavaScript:

a.addEventListener('mouseenter', functionname)

mouseenter

mousemove

mousedown

mouseup

click

mouseout

 

**Caixas de diálogo**

Alerta: exibir mensagem na tela. alert(mensagem)

Confirmação: solicita confirmação do usuário. confirm(mensagem)

Solicitação de informação. prompt(mensagem, valorinicial)

 

**Eventos**

Situações que disparam um código. Chamadas no HTML:

onBlur: foco sai do elemento.

onChange: elemento muda de valor.

onClick: Elemento é clicado.

onFocus: Foco é colocado no elemento.

onLoad: Página é carregada.

onUnload: Usuário clica para destino fora da página.

onMouseOver: Mouse entra na área do elemento.

onMouseOut: Mouse deixa a área do elemento.

onMouseDown: Mouse clica no elemento (ida).

onMouseUp: Mouse clica no elemento (volta).

onKeyPress: Tecla é digitada no elemento.

onKeyDown: Tecla é digitada no elemento (ida).

onKeyUp: Tecla é digitada no elemento (volta).

onSubmit: Elemento é enviado.

 

**Extras**

• Redirecionar para URL

-- location.href(URL)

• Abrir nova janela

-- open(URL)

• Interagindo com marcações HTML

-- Atributo id do HTML

-- document.getElementById(id)

• Agendamento de tarefas

-- setTimeout(funcao, tempoMilisegundos)

 

**Formulários**

• Objeto de acesso ao documento HTML

-- document

• Objeto de acesso aos formulários

-- document.forms[name]

• Acessando campos de um formulário

-- document.forms[name].namedocampo

• Principais propriedades dos campos

-- value: conteúdo do campo

-- length: tamanho do campo

-- checked: informa se o campo está checado

-- selectedIndex: número da opção selecionada

 

DOM level 0 - alguns problemas

  No html                      No JS
---------------------------- ------------------
  <p onclick="função()"  p.onclick=funcao

DOM level 2 - mais recomendado
p.addEventListener("click", funcao, bool capture);

Propagação de eventos: capacidade dos eventos de percorrerem a estrutura do HTML, desde o elemento original até o nível mais alto (body). Bool capture: valor padrão é falso. Altera a propagação dos eventos.

Objeto Event: objeto passado por parâmetro para a função que foi atrelada, nos fornecendo várias informações adicionais sobre o evento em si. Este objeto varia de acordo com o tipo de evento.

+---------------------------------------------------------------------+
| document.addEventListener('click', function (objetoEvento){       |
|                                                                     |
| console.log(objetoEvento);                                          |
|                                                                     |
| console.log(objetoEvento.currentTarget);                            |
|                                                                     |
| console.log(objetoEvento.target);                                   |
|                                                                     |
| objetoEvento.stopPropagation(); //interrompe a propagação do evento |
|                                                                     |
| })                                                                  |
+---------------------------------------------------------------------+

Delegação: técnica que consiste em atrelar o evento a um elemento mais alto e verificar qual foi o elemento clicado.

+------------------------------------------------------------------------+
| ul.addEventListener('click', function (objetoEvento){                |
|                                                                        |
| console.log(objetoEvento.target); //retorna qual li foi clicada        |
|                                                                        |
| console.log(objetoEvento.target.nodeName) //retorna o tipo do elemento |
|                                                                        |
| objetoEvento.stopPropagation(); //interrompe a propagação do evento    |
|                                                                        |
| })                                                                     |
+------------------------------------------------------------------------+

**Variáveis compostas**
Vetores e arrays

**Conjuntos de dados**
Array[]
Objeto{}
Construtor: new Object()
Objetos armazenam atributos e métodos (funções)
É possível criar um array de objetos. [{},{},{}]
Alguns objetos são relativos ao ambiente de hospedagem (ex: window.alert('') só para navegador)

## Strings
Literais var meuTexto = "Olá Mundo!";
Objetos var meuTexto = new String("Olá Mundo!");
Métodos e Propriedades:

+------------------------------------------------------------------------------------+
| .length //tamanho da string                                                        |
|                                                                                    |
| .toUpperCase() //string em letras maiúsculas                                       |
|                                                                                    |
| .toLowerCase() //string em letras minúsculas                                       |
|                                                                                    |
| .replace('.',',') //para substituir caracteres                                 |
|                                                                                    |
| .includes("") //verificação de string, resultado bool                            |
|                                                                                    |
| .indexOf('busca', posicaoInicial) //mapeamento da string para retornar busca     |
|                                                                                    |
| .lastIndexOf() //busca reversa, começando do fim                                   |
|                                                                                    |
| .substring(,) //retornar uma parte da string                                       |
|                                                                                    |
| .slice(,) //para criar um novo array, valor final não incluso - posições ordenadas |
|                                                                                    |
| .split() //retorna um array separando as partes da string original                 |
|                                                                                    |
| .valueOf() //retorna o valor primitivo                                             |
+------------------------------------------------------------------------------------+

## Number

Literais var meuNum = 123;
Objetos var meuNum = new Number("123");
Métodos e Propriedades:

```javascrip
MAX_VALUE //pripriedade estática, do construtor                                                                       
MIN_VALUE //pripriedade estática, do construtor                                                                       
toFixed() //para definir quantas casas decimais são exibidas                                                          
toPrecision() //arredonda para um valor definido de casas decimais                                                    
String(n) ou n.toString() //converter número para String, pode ser usado para converter para hexadecimal, binário etc 
toExponential() //retorna a notação científica do número                                                              
```
## Math

Métodos e propriedades são estáticos, ou seja, pertencem ao próprio construtor.

```javascript
Math.min() //retorna o menor valor    
Math.max() //retorna o maior valor    
Math.round() //arredondar             
Math.floor() //arredondar para menos  
Math.ceil() //arredondar para mais    
Math.pow(,) // retorna a potência     
Math.sqrt() //retorna a raiz quadrada 
Math.cbrt() //retorna raiz cubica     
Math.random() //retorna um aleatorio  
Math.PI //retorna o valor de PI       
```

