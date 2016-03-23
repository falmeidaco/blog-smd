---
layout: post
title:  "Experimentando o Processing"
date:   2016-03-18 13:00:00 -0300
categories: smd matematica-aplicada-a-multimidia-i
author: Felipe Almeida
tags:
- processing
---

Como execício, foi proposto a utilização de um dos exemplos existentes do site da linguagem Processing [http://processing.org/examples](http://processing.org/examples), onde o exemplo escolhido deveria ser comentado, modificado e apresentado na aula. Abaixo, o resultado do exercício:

No código original é demostrado a possibilidade de carregar na tela uma imagem da internet. A modificação do exemplo foi a alteração da cor do fundo dinamicamente utilizando uma cor existente na imagem carregada. 

{% highlight java %}
PImage img;
String image_url = "https://fbcdn-profile-a.akamaihd.net/hprofile-ak-xaf1/v/t1.0-1/p160x160/1917949_10209031057153404_8837720743660038304_n.jpg?oh=10b11dab2e1a47dd8a3aef591da2d241&oe=577A7417&__gda__=1469447388_1457612be2a3957e598111e2a24a40f7";
color c; 
int xpos,ypos;

void setup() {
    size(300, 300);
    //Carregando imagem
    img = loadImage(image_url);
    //Definindo cor inicial como 0 (preto)
    c = 0;
    //Definindo posição central relacionado ao tamamho da imagem e da tela
    xpos = ((width/2)-(img.width/2));
    ypos = ((height/2)-(img.height/2));
}

//Evento do Processing
void mouseMoved() {
    //Atualização variável "c" com a o valor da cor do pixel em que o ponteiro do mouse está posicionado
    c = get(mouseX,mouseY);
    println(c);
}

void draw() {
    //Aplicando a cor de fundo
    background(c);
    //Imprimindo a imagem carregada caso ela tenha sido encontrada
    if (img != null) {
        image(img, xpos, ypos, 160, 160);
    }
}

{% endhighlight %}

O resultado pode ser visualizado no gif abaixo:

![Resultado do código](http://i.giphy.com/l2R0cPSv9xjV22j28.gif)

Links úteis:  
[Saiba mais sobre a linguagem Processing](https://processing.org/){:target="_blank"}