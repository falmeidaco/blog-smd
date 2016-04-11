---
layout: post
title:  "Desenhando a Bandeira do Brasil com Processing"
date:   2016-04-08 13:00:00 -0300
categories: smd matematica-aplicada-multimidia-i
author: Felipe Almeida
tags:
- processing
- brasil
---

Olá mundo!

Como exercício, foi proposto o desenvolvimento de um método no Processing que receba 3 parâmetros, 3 medidas (posição x, posição y, largura). A partir dessas informações, o método deve desenhar na tela a Bandeira do Brasil considerando o padrão descrito na lei federal abaixo:

>**LF 5700, S. II, A. 5 - 01/09/1971**  
I - Para cálculo das dimensões, tomar-se-á por base a altura desejada, dividindo-se esta em 14 partes iguais. Cada uma das partes será considerada uma medida ou módulo.  
II - O largura total será de 20 módulos.  
III - A distância dos vértices do losango ao quadro externo será de um módulo e sete décimos.  
IV - O círculo no meio do losango terá o raio de três módulos e meio.

Deve ser criado também um segundo método *losango* que auxilie no desenho de um losango.

A posição x e y devem ser referentes ao centro da figura desenhada, e não do ponto superior esquerdo, referência padrão do processing para desenhor de um retângulo.  

Abaixo, o resultado final:

{% highlight java %}
//Método para exibição da bandeira do Brasil baseado no padrão definodo na Lei Federal 5700, S. II, A. 5 - 01/09/1971
void mostraBandeiraBrasil(float x, float y, float l) 
{
  //Descobrindo o tamanho do módulo baseado na largura especificada
  float modulo = l/20;
  //Descobrindo a altura baseado no tamanho do módulo encontrado
  float altura = 14*modulo;
  //Descobrindo o raio do círculo central baseado no tamanho do módulo encontrado
  float raio = modulo*3.5;
  //Descobrindo a distância dos vértices do losando com o retângulo externo baseado no tamanho do módulo encontrado
  float distanciaVerticeLosango = modulo*1.7;
  
  fill(0, 168, 89);
  //Desenhando e posicionado o retângulo de acordo com os parâmetro informados.
  rect(x-l/2, y-altura/2, l, altura);
  
  fill(255, 204, 41);
  //Desenhando o losango utilizando o método auxiliar criado
  losango(x,y,l-(distanciaVerticeLosango*2), altura-(distanciaVerticeLosango*2));
  
  fill(62, 64, 149);
  //Desenhando o circulo central da bandeira
  ellipse(x, y, raio*2, raio*2);
}
//Método auxiliar para desenho de um losango, recebendo os parâmetros x e y para posição, l e a para largura e altura respectivamente
void losango(float x, float y, float l, float a) 
{
  quad(x-(l/2),y, x,y-(a/2), x+(l/2),y, x,y+(a/2));
}
{% endhighlight %}

A utilização do método pode ser experimentado no Processing com o código completo abaixo:

{% highlight java %}
//Variáveis necessára para interatividade com o mouse
int lastX,lastY;
//Flag adicionada para exibir ou não a marcação dos módulos na bandeira
Boolean mostraGrade = true;

void setup() {
  size(800, 600);
}

void draw() {
  background(255);
  //Interatividade com o mouse
  if (!mousePressed) {
    //Desenhando a bandeira no centro da tela com largura de 550 pixels.
    mostraBandeiraBrasil(width/2,height/2,550);
  } else {
    //Ao clicar e arrastar o mouse, a bandeira é desenhada com a largura desejada pelo usuário
    mostraBandeiraBrasil(
      lastX+float((mouseX-lastX)/2),
      (((float(mouseX-lastX)/20)*14)/2)+lastY,
      float(mouseX-lastX));    
  }
}

void mostraBandeiraBrasil(float x, float y, float l) 
{
  //Descobrindo o tamanho do módulo baseado na largura especificada
  float modulo = l/20;
  //Descobrindo a altura baseado no tamanho do módulo encontrado
  float altura = 14*modulo;
  //Descobrindo o raio do círculo central baseado no tamanho do módulo encontrado
  float raio = modulo*3.5;
  //Descobrindo a distância dos vértices do losando com o retângulo externo baseado no tamanho do módulo encontrado
  float distanciaLosangoRetangulo = modulo*1.7;
  
  fill(0, 168, 89);
  //Desenhando e posicionado o retângulo de acordo com os parâmetro informados.
  rect(x-l/2, y-altura/2, l, altura);
  fill(255, 204, 41);
  //Desenhando o losango com a posição dos vértices encontrados baseado no tamanho do retângulo externo, da posição do retângulo e a distância padrão dos limites deste com os vértices
  quad((x-l/2)+distanciaLosangoRetangulo, y, 
        x, (y-altura/2)+distanciaLosangoRetangulo,
       (x+l/2)-distanciaLosangoRetangulo, y, 
        x, (y+altura/2)-distanciaLosangoRetangulo);
  fill(62, 64, 149);
  //Desenhando o circulo central da bandeira
  ellipse(x, y, raio*2, raio*2);
  
  //Mostra a marcação dos módulos na baneira
  if (mostraGrade) {
    for (int i = 0; i<20; i++) {
      line((modulo*i)+x-l/2, y-(altura/2), (modulo*i)+x-l/2, y+(altura/2));
    }
    for (int i = 0; i<14; i++) {
      line(x-(l/2), modulo*i+y-altura/2, x+(l/2), modulo*i+y-altura/2);
    }
  } 
}

//Evento necessário para interatividade com o mouse
void mousePressed() {
  lastX = mouseX;
  lastY = mouseY;
}
{% endhighlight %}

Foi acrescentado uma interação básica com o mouse onde é possível, a partir de qualquer ponto da tela, clicar e arrastar o ponteiro para ser gerada uma bandeira com largura personalizada pelo usuário. Além disso, foi acrescentado ao método *mostraBandeiraBrasil* um techo de código que possibilita a exbição da divisão dos módulos da figura quando a mesma é desenhada de forma personalizada segurando a tecla SHIFT.

O resultado pode ser visualizado no gif abaixo:

![Resultado do código](http://i.giphy.com/l3V0dOOW1x2QVC44o.gif)