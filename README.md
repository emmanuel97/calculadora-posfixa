# Calculadora Posfixa


## Objetivo
- Projetar testes uniários para uma terceira equipe implementar

## Problema
- Receber uma string contendo uma expressão matemática em [notação polonesa](https://pt.wikipedia.org/wiki/Nota%C3%A7%C3%A3o_polonesa) e retornar o valor de resultado da expressão.

- Exemplos
"3 2 5 + *" => 21

- [Calculadora online](https://epxx.co/ctb/hp12c.html)


## Atividades
- segunda-feira 25-09
   1. forkar este repositório
   1. atualizar README.md com
      - equipe (lembrar de colocar link para o github dos membros)
      - tecnologia usada
      - plano de teste (definir se vai usar top-down ou bottom-up)
      - implementar os testes unitários
      - como executar teste
   1. apresentar em sala o plano de teste
- quinta-feira 28-09
   1. sortear repositório e equipe
   1. forkar repositório
   1. desenvolver solução para os testes
   1. apresentar plano de teste e solução
   
   [Polonesa Inversa]https://pt.wikipedia.org/wiki/Nota%C3%A7%C3%A3o_polonesa_inversa
   
 # 3o Plano de teste - Calculadora Polonesa
### Membros: 
- Emmanuel Bulacio
- Juscelino Messias

### Tecnologias: 
- Linguagem de programação:
  - Java 8 Update 141
- SO:
  - Linux (Debian 8.x release Jessie) 
  - Windows 10
- Ambiente de produção:  
  - Netbeans IDE 8.2  
- Ferramenta de Testes:
  - JUnit 4.12  
  
### Plano de teste
- Top-down

# Plano de teste

Entrada | Condição | Classes Válidas | Classes Inválidas
:-----: | :------: | :-------------: | :---------------:
  calculo  | - | primeiro caracter é numero | primeiro caracter não é numero 
   calculo  | calculo é do tipo String    | calculo tem só caracteres("+","-","/","*", espaço e numerais)|calculo tem String difentes de "+","-","/","*", " " e numeros
  calculo  | - | qtdNumeros(calculo) == qtdOperadores(calculo) + 1 | qtdNumeros(calculo) != qtdOperadores(calculo) + 1 
  
  
  public boolean saoOperadoresValidos(String calculo){
       operadores misturados com numeros #expresao invalida -- false
       sequencia de operadores no inicio da string #expresao invalida -- false
       sequencia de operadores no final da string #expresao valida -- true
  }
  
## 1º caso de teste - primeiro caractere e numero - classe valida
calculo= "5 4 +"
char[] c = calculo.toCharArray();
return Character.isDigit(c[0]);  #true

## 2º caso de teste - primeiro caractere e numero - classe invalida
calculo= "+ 5 4"
char[] c = calculo.toCharArray();
return Character.isDigit(c[0]);  #false

## 3º caso de teste - quantia de numeros deve ser igual a quantia de operadores + 1 - classe valida
int a,b;
calculo= "5 4 +";
a=qtdNumeros(calculo);
b=qtdOperadores(calculo);
if(a==b+1)#true
## 4º caso de teste - quantia de numeros deve ser igual a quantia de operadores + 1- classe invalida
int a,b;
calculo= "5 4 + *";
a=qtdNumeros(calculo);
b=qtdOperadores(calculo);
if(a==b+1)#false

## Escrevendo Testes JUnit no NetBeans IDE

Este tutorial apresenta os princípios básicos da escrita e execução de testes de unidade JUnit no NetBeans IDE. O teste de uma aplicação faz parte do ciclo de desenvolvimento, e a escrita e manutenção de testes de unidade podem ajudar a garantir que os métodos individuais em seu código-fonte funcionem corretamente. O suporte integrado do IDE para o framework de teste de unidades JUnit permite que você crie os testes e conjuntos de testes do JUnit de modo fácil e rápido.

- Criando o Projeto
   - Criando o Projeto de Biblioteca de Classe Java
   - Criando as Classes Java 

- Escrevendo Testes JUnit 4
   - Criando uma Classe de Teste para Vectors.java
   - Escrevendo Métodos de Teste para Vectors.java
   - Criando uma Classe de Teste para Utils.java
   - Escrevendo Métodos de Teste para Utils.java
   - Executando os Testes



