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
a=qtdNumeros("5 4 +");
b=qtdOperadores("5 4 +");
if(a==b+1)#true

## 4º caso de teste - quantia de numeros deve ser igual a quantia de operadores + 1- classe invalida
int a,b;
a=qtdNumeros("5 4 + *");
b=qtdOperadores("5 4 + *");
if(a==b+1)#false

## 5º caso de teste - a string deve ser uma expressao polonesa - classe valida

verificarExp"5 4 3 + *"); #true

## 6º caso de teste - a string deve ser uma expressao polonesa - classe invalida

verificarExp("5 + 4 * 3"); #false

## 7º caso de teste - a string não deve só deve conter letras e carateres - classe valida
int a,b,c;
calculo= "5 4 +";      
a=qtdNumeros(calculo);   #2
b=qtdOperadores(calculo);#1
x=calculo.length();      #3
a+b==c?               #true

## 8º caso de teste - a string não deve só deve conter letras e carateres - classe invalida
int a,b,c;
calculo= "5 4 + e";      
a=qtdNumeros(calculo);   #2
b=qtdOperadores(calculo);#1
x=calculo.length();      #4
a+b==c?               #false

## Escrevendo Testes JUnit no NetBeans IDE

Este tutorial apresenta os princípios básicos da escrita e execução de testes de unidade JUnit no NetBeans IDE. O teste de uma aplicação faz parte do ciclo de desenvolvimento, e a escrita e manutenção de testes de unidade podem ajudar a garantir que os métodos individuais em seu código-fonte funcionem corretamente. O suporte integrado do IDE para o framework de teste de unidades JUnit permite que você crie os testes e conjuntos de testes do JUnit de modo fácil e rápido.

- Criando o Projeto
   - Criando o Projeto de Biblioteca de Classe Java
   - Criando as Classes Java 

- Escrevendo Testes JUnit 4
   1. Criando uma Classe de Teste para Vectors.java
   2. Escrevendo Métodos de Teste para Vectors.java
   3. Criando uma Classe de Teste para Utils.java
   4. Escrevendo Métodos de Teste para Utils.java
   5. Executando os Testes
   
- Para executar as etapas neste tutorial, instale o plug-in do JUnit na Central de Atualização. Você poderá instalar o plug-in do JUnit no gerenciador de Plug-ins se não tiver instalado o plug-in quando instalou o IDE.

- Criando o Projeto de Biblioteca de Classe Java
   1. Escolha Arquivo > Novo Projeto no menu principal.
   2. Selecione Biblioteca de Classe Java em Categoria Java e clique em Próximo.
   3. Insira JUnit-Sample para o projeto e defina a localização do projeto.
   4. Desmarque a opção Usar Pasta Dedicada, se ela estiver selecionada.

    Para este tutorial, há pouco motivo para copiar as bibliotecas de projeto em uma pasta dedicada, pois você não precisará compartilhar bibliotecas com outros usuários ou projetos.
    Clique em Finalizar.
    
    Na primeira vez em que você criar um teste JUnit, o IDE solicita que você selecione uma versão e, em seguida, adiciona o nó Testar Bibliotecas e a biblioteca do JUnit.

- Escrevendo Testes JUnit 4
Você usará os assistentes do IDE para criar esqueletos de teste com base nas classes em seu projeto. Na primeira vez em que você usar o IDE para criar esqueletos de teste, o IDE solicitará que você escolha a versão da JUnit. 

   1. Clique com o botão direito do mouse em Vectors.java e selecione Ferramentas > Criar Testes.
   2. Modifique o nome da classe de teste para VectorsJUnit4Test na caixa de diálogo Criar Testes. Quando você alterar o nome da classe de teste, será exibido uma advertência sobre a alteração do nome. O nome default é baseado no nome da classe que você está testando, com a palavra Teste acrescentada ao nome. Por exemplo, para a classe MyClass.java, o nome default da classe de teste é MyClassTest.java. Diferente da JUnit 3, na JUnit 4, o teste não precisa ser finalizado com a palavra Teste. Normalmente, é melhor manter o nome default, porém, como você está criando todos os testes da JUnit no mesmo pacote neste tutorial, os nomes das classes de teste devem ser exclusivos.
   3. Selecione JUnit na lista drop-down Framework.
   4. Desmarque Inicializador de Teste e Finalizador de Teste. Clique em OK.
   5. Selecione a JUnit 4.x na caixa de diálogo Selecionar a Versão da JUnit. Clique em Selecionar.

