+++
title = "Modificar Mapa Del Teclado Con Emacs Y Vim"
date = "2016-11-21T14:40:45-05:00"
draft = true
tags = ["emacs", "vim"]
topics = []
description = ""
+++

<p>Estos son algunos de los ejemplos que se pueden utilizar a través de los inmensamente populares editores de programación Emacs <a href="#emacs"><sup>1</sup></a> y Vim <a href="#vim"><sup>2</sup></a>, para cambiar el mapa del teclado.</p>

<h2 id="emacs">Emacs</h2>

<p>El altamente configurable y extensible editor de texto Emacs también nos puede ayudar con modificaciones del teclado, o cambiar la localización de las teclas, sin la necesidad de cambiar todo el diseño, y sin la necesidad de tener que utilizar algún teclado en específico.</p>

<p>Primero se crea una función que se le asigna un nombre determinado. En este caso utilizamos el nombre de “backslash”. Posteriormente a esto, se le atribuye el comando <code>insert</code> seguido de <code>kbd</code> y el mapa del registro del teclado que se desea modificar.</p>

<p>En mi caso, encontré conveniente intercambiar las teclas <code>\</code> por <code>;</code> y viceversa. Por ejemplo:</p>

<pre><code>(defun backslash ()
  (interactive)
  (insert (kbd "\\")))

(global-set-key (kbd "; " ) 'backslash)
</code></pre>

<p>al igual que:</p>

<pre><code>(defun semicolon ()
  (interactive)
  (insert (kbd ";" )))

(global-set-key (kbd "\\" ) 'semicolon)
</code></pre>

<p>Como se puede ver en los ejemplos anteriores, después de esto se le asigna <code>global-set-key</code> a la recién nombrada función. Es decir, en el primer caso, la función se le asignó el nombre <code>backslash</code>, y la cual fue directamente entrelazada con el ya mencionado comando <code>global-set-key</code> seguido de la tecla <code>;</code>.</p>

<p>De esta manera se logra el objetivo deseado. Esto es, que el ingreso de una tecla dada en el mapa del teclado del registro de entrada del sistema operativo, sea interpretado  posteriormente, - mediante la nueva asignación que proveyó la función - con el registro del mapa de otra tecla que haya sido predeterminada, dando lugar con ello a que ese ingreso del mapa del teclado, se registre apropiadamente con los resultados de la salida.</p>

<p>En el primer ejemplo, cada vez que la tecla <code>;</code>sea presionada, la tecla <code>\</code> tomará precedencia. Y viceversa.</p>

<h2 id="vim">Vim</h2>

<p>en el caso de Vim, el editor de texto más utilizado en Unix, y el cual está disponible de fábrica, o en la mayoría de las variaciones de Unix, el modificar el mapa del teclado se obtiene de varias maneras.</p>

<p>Solamente mostraré el comando que lograría esto de la manera más simple y durante el modo de insertar: <code>inoremap</code>, el cual es seguido de la tecla que se desea modificar, con la que tomaría la nueva posición.</p>

<p>Es decir:</p>

<pre><code> inoremap ; \
</code></pre>

<p>lograría lo que en este caso se quisiera. Cada vez que la tecla <code>;</code> se presione, la <code>\</code> tomará su lugar.</p>

<p>De la misma manera, cuando se especifica el anterior comando en el fichero de inicialización, conlleva a especificar el mismo comando, es decir <code>inoremap</code> pero en esta ocasión con los símbolos de manera inversa. De otra manera, ambas teclas tendrán asignadas el mismo mapa en el registro del teclado.</p>

<p>Por lo tanto</p>

<pre><code>inoremap \ ; 
</code></pre>

<p>sería imprescindible para finalizar la modificación de estas teclas.</p>

