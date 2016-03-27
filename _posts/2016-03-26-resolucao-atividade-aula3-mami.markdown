---
layout: post
title:  "Resoluçao da atividade da terceira aula de Matematica Aplicado a Multimidia I"
date:   2016-03-26 13:00:00 -0300
categories: smd matematica-aplicada-a-multimidia-i
author: Felipe Almeida
tags:
- processing
- desafio
---
*Obs.: As teclas de acentuacao nao estao funcionando.*

**Atividade**  
*Posicionar horizontalmente 5 imagens de 20x30px, estando 2 na horizontal e 3 na vertical, em uma janela de 180px de largura com espaços iguais entre as imagens e as extremidades da janela.*  
Considerando a situaçao acima, desenvolver uma funçao que receba 2 parametros, sendo o o primeiro para o numero de fuguras X por Y px q ser exibidas horizontalmente e o segundo para o numero de figuras das mesmas proporcoes a serem exibidas verticalmente.

{% highlight java %}
/**
  * Descriçao: Resuluçao do desafio da aula 3
  * Disciplina: Matemática Alplicada a Multimida I
  * Curo: Sistemas e Mídias Digitais (Universidade Federal do Ceará)
  * Autor: Felipe ALmeida
  */

//Iniciando variavel que armazena as dimensoes da figura
int quadradoLargura, quadradoAltura;

void setup() {
  //Iniciando tela com tamanho predefinido
  size(180,200);
  //Defindo dimensoes da figura
  quadradoLargura = 21;
  quadradoAltura = 23;
}

void draw() {
  //Resetando 
  background(255);
  //Desenhando figuras (n figuras horizontais, n figuras verticais)
  organizar(2,3);
}

/**
  * Funçao para organizar horizontalmente as imagens na tela de acordo
  * com os parametros passados (figuras horizontais e verticais) e com
  * a distancia igual entre elas e os limites da tela;
  */
void organizar(int h, int v) {
  
  //Numero de figuras a sem exibidas na tela
  int numQuadrado = h+v;
  //Resgatando o tamanho do lado maior da figura
  int ladoMaior = Math.max(quadradoLargura, quadradoAltura);
  //Resgatando o tamanho do lado menor da figura
  int ladoMenor = Math.min(quadradoLargura, quadradoAltura);
  //Calculando a largura total das figuras na horizontal
  int totalLarguraHorizontal = h*ladoMaior;
  //Calculando a largura total das figuras na vertical
  int totalLarguraVertical = v*ladoMenor;
  //Calculando a distancia entre as figuras considerando 
  int distanciaFiguras = (width-(totalLarguraHorizontal+totalLarguraVertical))/(numQuadrado+1);
  //println(distanciaFiguras);
  
  //Defindo o preenchimento das figuras
  fill(0);
  
  //Variavel auxilidar para defnir posiçao x das figuras
  int proxPosicao = 0;
  
  //Repeticao relacionada ao numeo de figuras
  for (int i = 0; i < numQuadrado; i++) {
    //Verifica se existe figuras para ser exibidas na horizontal
    if (i<h) {
      //Desenhando figura horizontal
      rect(proxPosicao+distanciaFiguras, 20, ladoMaior,ladoMenor);
      //Atualizando variavel auxiliar para ser usada na posicao da proxima figura
      proxPosicao += ladoMaior+distanciaFiguras;
    //Caso nao exista mais imagens na horizontal a serem exibidas, exibir imagen na vertical
    } else {
      //Desenhando figura horizontal
      rect(proxPosicao+distanciaFiguras, 20, ladoMenor,ladoMaior);
      //Atualizando variavel auxiliar para ser usada na posicao da proxima figura
      proxPosicao += ladoMenor+distanciaFiguras;
    }
  }
  
}
{% endhighlight %}

Links úteis:  
[Saiba mais sobre a linguagem Processing](https://processing.org/){:target="_blank"}
