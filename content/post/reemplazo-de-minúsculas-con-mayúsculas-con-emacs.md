+++
title = "Reemplazo De Minúsculas Con Mayúsculas Con Emacs"
date = "2017-02-09T02:31:55-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>Para un simple reemplazo de caracteres al principio de una oración, es decir, de minúsculas por mayúsculas, se puede emplear un simple y eficiente método de expresión regular también en Emacs.</p>

<p>Ya existe un modo de <em>capitalization</em> que logra este reemplazo de una cadena de caracteres o cadena de texto como se dice en inglés: string, y aunque tiene un inigualable mérito para este propósito, de igual manera retrasa el ingreso de caracteres., como es de esperar, el retraso o el lapso que esto conlleva, es una desventaja para una óptima funcionalidad.</p>

<p>Digamos por ejemplo que:</p>

<p>foo bar. foo bar. foo bar.</p>

<p>Para modificar la minúscula por una mayúscula:</p>

<pre><code> M-x replace-regex
 \(\. \w\)
 \,(capitalize \1)
</code></pre>

<p>que nos da como resultado:</p>

<p>foo bar. Foo bar. Foo bar.</p>

<p>pero el comienzo de la oración o de la línea no se ha modificado, entonces:</p>

<pre><code> M-x replace-regex
 \(^\w\)
 \,(capitalize \1)
</code></pre>

<p>logra hacer la modificación restante a:</p>

<p>Foo bar. Foo bar. Foo bar</p>

<p>Si deseas hacer la modificación de una vez y por todas, y abreviando por consiguiente las dos expresiones regulares anteriores, utilizarías en este caso el delimitador <code>|</code> antes de la barra oblicua <code>\</code>. Es decir:</p>

<pre><code> M-x replace-regex
 \(^\w\|\. \w\)
 \,(capitalize \1) 
</code></pre>

<p>Reemplaza el original foo bar. foo bar. foo bar. A Foo bar. Foo bar. Foo bar.</p>

**Notas**

Si por aluna casualidad, Emacs no reconoce y te devuelve como resultado que reemplazó (0) eventos, quizás pudiese tuvieses que palanquear (toggle) `case-replace` a nulo (nil). Vea esta <a href="https://stackoverflow.com/a/25231464" target="_blank">respuesta en Stackoverflow</a>.
