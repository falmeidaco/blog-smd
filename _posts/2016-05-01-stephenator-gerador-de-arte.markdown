---
layout: post
title:  "Stephenator: gerador de arte"
date:   2016-05-01 13:00:00 -0300
categories: smd matematica-aplicada-multimidia-i
author: Felipe Almeida
tags:
- processing
- javscript
- html5
- canvas
- arte
- stephen westfall
---

O resultado do trabalho pode ser visualizado nesse link: [http://falmeidao.github.io](http://falmeidao.github.io)

Sobre o site
------------

###Objetivo

Este site é o resultado do desenvolvimento do trabalho para a disciplina de Matemática Aplicada à Multimídia I (Universidade Federal do Ceará, semestre II). Selecionando uma série de obras de algum artista, deve ser desenvolvido um recurso que possibilite a reprodução visual da série escolhida. Deve ser analisado os detalhes das obras, seus padrões de formas, cores, ângulos e quaisquer outras características que possam ser usadas como variáveis a serem utilizadas para a reprodução da imagem. 

###Desenvolvimento

Inicialmente foi analisado as características e padrões da obra. É possível perceber que ela é composta por uma repetição de quadrados. Estes quadrados possuem um número de divisões padrão para todos eles, e para cada divisão é aplicada uma cor, resultando em um quadrado colorido diagonalmente listrado. Cada quadrado é composto por trapézios. Quando o número de divisões de cada quadrado é ímpar, é gerada uma exceção para o elemento central, que acaba virando um hexágono.

Foi desenvolvido um algoritmo em Processing para o estudo do comportamento desses elementos. O primeiro passo foi a simplificação da obra, desenhando um único quadrado utilizando a função *quad* do Processing para o desenho dos trapézios. É importante notar que para a regra de divisões ímpares citada no parágrafo cima, foi utilizado o seguinte método: o desenho hexágono central é composto por dois trapézios. A razão disso é que no Processing não existe uma função básica para o desenho de formas com mais de 4 vértices.

###Recursos

Concluído o algoritmo, este foi reproduzido e adaptado para página da web utilizando o recurso canvas do HTML5. Para este site, também foi utilizado a biblioteca css [Bootstrap](http://getbootstrap.com/) com os elementos customizados, biblioteca javascript [JQuery](https://jquery.com/) para o desenvolvimento dos controles de variáveis, e a biblioteca javascript [Perfect-Scrollbar](https://noraesae.github.io/perfect-scrollbar/) para a customização da barra de rolagem da área de conteúdo. 

Sobre o artista
---------------

Stephen Westfall é um artita e crítico que se descreve como "Popista, pós-minimalista de pinturas geométricas.  Seus trabalhos, como do de 2009 

###Sobre as obras
