# Apostila

A seguinte apostila irá compreender os seguintes tópicos

## Sumário
1) <a href="#1">OpenMP</a><br>
  1.1) <a href="#1.1">O que é o OpenMP?</a><br>
  1.2) <a href="#1.2">Início com OpenMP</a><br>
2) <a href="#2">Algoritmos genéticos</a>
3) <a href="#3">Recozimento simulado</a>
4) <a href="#4">Referências</a>

<div id="1"></div>

## OpenMP

<div id="1.1"></div>

### O que é o OpenMP?

  OpenMP é uma API, portável, baseada no modelo de programação paralela de memória compartilhada para arquiteturas de múltiplos processadores. 
  OpenMP está disponível para uso com os compiladores C/C++ e Fortran, podendo ser executado em ambientes Unix e Windows (Sistemas Multithreads)(UNICAMP, 2014).
  
<div id="1.2">Início com OpenMP</div>

### Início com OpenMP

Vamos começar com um "Hello world". <a href="l1">Listagem 1</a> mostra o código.

<p id="l1">Lista 1. Hello world com o OpenMP</p>

```c++
#include <cstdio>

int main(){
    #pragma omp parallel
    {
    printf("Hello World\n");
    }
    return 0;
}
```

Quando o código acima é compilado e executado com o g++ deverá mostrar apenas uma única vez "Hello World", contudo agora compilando usando a flag -fopenmp iremos obter conforme a <a href="l2">Listagem 2</a>

<p id="l1">Lista 2. Compilando e executando com -fopenmp</p>

```
g++ code1.cpp -fopenmp -o code1
code1
Hello World
Hello World
Hello World
Hello World
Hello World
Hello World
Hello World
Hello World
```

 O que aconteceu foi que internamente, durante a compilação, o GCC gera o código para criar o máximo número de encadeamentos possível no tempo de execução, com base no hardware e na configuração do sistema operacional. A rotina de início de cada encadeamento é o código no bloco após o pragma. Esse comportamento chama-se paralelização implícita. Na sua essência, OpenMP consiste em um conjunto de pragmas eficientes que livram o desenvolvedor da obrigação de incluir muitos códigos repetidos. Notem que a saída pode variar de acordo com seu processador, no meu caso tendo um Intel® Core i7 com 4 núcleos totalizando em 8 threads a saída se adequa pois 8 encadeamentos = 8 núcleos lógicos.
 
<div id="2"></div>

## Algoritmos Genéticos

<div id="3"></div>

## Recozimento Simulado

<div id="4"></div>

## Referências
[0] https://www.cenapad.unicamp.br/servicos/treinamentos/apostilas/apostila_openmp.pdf
[1] https://www.ibm.com/developerworks/br/aix/library/au-aix-openmp-framework/index.html
