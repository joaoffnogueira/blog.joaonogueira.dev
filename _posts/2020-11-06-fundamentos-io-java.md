---
title: Fundamentos de IO em Java
author: João F. F. Nogueira
date: 2020-11-06 09:00:00 -0300
categories: [Português, Estudos]
tags: [java]
toc: true
---

> Baseado nos cursos da Softblue

# API de I/O do Java

* Está localizada no pacote java.io

* A API de I/O gerencia a entrada e saída de dados

– Console, arquivos, sockets, etc.

* Todas as operações de I/O são baseadas em fluxo de dados (streams)

– InputStream: fluxo de entrada

– OutputStream: fluxo de saída

* A API usa polimorfismo para esconder detalhes de onde a informação vem e para onde ela vai

* Pelas streams, trafegam bytes

– InputStream: é capaz de ler bytes de algum lugar

```java
InputStream is = new FileInputStream("entrada.txt");
int b = is.read();

InputStream is = System.in;
int b = is.read();
```

– OutputStream: é capaz de escrever bytes em algum lugar

```java
OutputStream os = new FileOutputStream("saida.txt");
os.write(65);

OutputStream os = System.out;
os.write(65);
```

## Lendo caracteres

* Para lermos caracteres, devemos usar uma “ponte”, que converte bytes em caracteres

InputStream lê bytes - InputStreamReader lê caracteres

```java
InputStream is = new FileInputStream("entrada.txt");
InputStreamReader isr = new InputStreamReader(is);
char c = (char) isr.read();
```

## Lendo Strings

* Para lermos strings, devemos usar um objeto que consegue juntar os caracteres

InputStreamReader lê caracteres - BufferedReader lê strings

```java
InputStreamReader isr = new InputStreamReader(is);
BufferedReader br = new BufferedReader(isr);
String s = br.readLine();
```

## Escrevendo caracteres e strings

OutputStream - OutputStreamWriter - BufferedWriter

```java
OutputStream os = new FileOutputStream("saida.txt");
OutputStreamWriter osw = new OutputStreamWriter(os);
BufferedWriter bw = new BufferedWriter(osw);
bw.write("texto");
```

## Streams em Arquivos

* É possível usar também as classes `FileReader` e `FileWriter` para lermos e escrevermos arquivos texto

```java
Reader r = new FileReader("entrada.txt");//Caracteres
Writer w = new FileWriter("saida.txt");

BufferedReader br = new BufferedReader(r);//Strings
BufferedWriter bw = new BufferedWriter(w);
```

## Scanner e PrintStream

* Servem para facilitar o trabalho de ler e escrever dados em streams

– Scanner: lê dados de uma stream de entrada

```java
Scanner s = new Scanner(new FileInputStream("entrada.txt"));//Pode ser utilizado qualquer InputStream ou Reader

while(s.hasNextLine()) {
	String token = s.nextLine();//Possibilidade de trabalhar com tokens
```

* O Scanner possui facilidades para quebrar strings com base em delimitadores

– PrintStream: escreve dados em uma stream de saída

```java
PrintStream ps = new PrintStream(new FileOutputStream("saida.txt"));//Pode ser utilizada qualquer OutputStream

ps.println("texto");//Os métodos print() e println() facilitam a escrita de dados
```

* System.out é uma PrintStream

# A classe `java.io.File`

* Permite acesso às informações sobre um arquivo ou diretório no sistema de arquivos

– nome, diretório, tamanho em bytes, permissões de escrita e leitura, etc.

* Não representa obrigatoriamente um arquivo existente no sistema de arquivos

```java
File f = new File("C:/Arquivos/arquivo.txt");
```

* Alguns métodos importantes:

| **Método**     | **Descrição**                                    |
|:--------------:|:------------------------------------------------:|
| isDirectory()  | Informa se é um arquivo ou um diretório          |
| exists()       | Informa se o arquivo (ou diretório) existe       |
| getName()      | Obtém o nome do arquivo ou diretório             |
| getPath()      | Obtém o caminho completo do arquivo ou diretório |
| listFiles()    | Lista os arquivos de um diretório                |

# Try-with-resources

* Permite o fechamento automático de recursos (chamada ao método `close()`)

```java
InputStream is = null;
try {
	is = new FileInputStream("entrada.txt");
	...
} finally {
	if (is != null) {
		is.close();
	}
}

try (InputStream is = new FileInputStream("entada.txt")) { //Closeable ou AutoCloseable
	...
}
```
