---
layout: post
title: Natural Scrolling in Linux
redirect_from: /2013/02/natural-scrolling-in-linux
---

<!--:en-->This is just a quickie.

Recently I started working at a company where all the devstations are MacMinis. I never used Macs before, but so far so good.
The only thing that was annoying me was my brain farts when moving from natural scrolling (1) to the common people scrolling.

1. Natural Scrolling is how they call the mac osx scrolling, where you roll down your mouse whell to roll up the scrollbar, and roll up the mouse whell to roll down the scrollbar.

I decided to have my Linux use natural scrolling and get rid of this, and it's quite easy!

{% highlight shell %}
echo "pointer = 1 2 3 5 4 7 6 8 9 10 11 12" >> ~/.Xmodmap
xmodmap ~/.Xmodmap
{% endhighlight %}

The synaptics driver uses the buttons 4 and 5 for up and down scrolling, and  with the above xmodmap configuration we're just swapping the two of them!

Extra:  If you'd like to change this on the fly with a GUI, there's the "NaturalScrolling" project on github. But I didn't test it.
https://github.com/cemmanouilidis/naturalscrolling#readme

(PT-BR version below)

-----------------

<!--:--><!--:pt-->Uma rapidinha agora.

Recentemente eu comecei a trabalhar numa empresa em que todas as estações de desenvolvimento são MacMinis. Eu nunca tinha usado Macs antes, mas até agora tudo certo. 
A única coisa que realmente me incomoda é meu cérebro falhando miseravelmente quando eu mudo da rolagem natural (1) pra rolagem "das pessoas comuns".

1. Rolagem Natural é como chamam a rolagem usada no mac osx, em que rolando a roda do mouse pra baixo, rola-se a barra de uma janela pra cima, e rolando a roda do mouse pra cima, rola-se a barra de uma janela pra baixo.

Decidi então colocar a rolagem natural no meu Linux pra não ter mais problemas, e foi bem simples!

{% highlight shell %}
echo "pointer = 1 2 3 5 4 7 6 8 9 10 11 12" >> ~/.Xmodmap
xmodmap ~/.Xmodmap
{% endhighlight %}

O driver do synaptic usa os botões 4 e 5 pra rolagem pra baixo e pra cima, e com a configuração acima do xmodmap estamos apenas trocando o mapeamento dos dois!

Extra:  Se quiser uma interface gráfica pra mudar isso em tempo real, tem um projeto no github chamado "NaturalScrolling", mas eu não testei! https://github.com/cemmanouilidis/naturalscrolling#readme

<!--:-->
