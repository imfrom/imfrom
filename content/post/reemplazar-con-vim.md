+++
title = "Reemplazar Con Vim. Reemplazos de minúsculas con mayúsculas"
date = "2017-02-08T13:48:53-05:00"
draft = true
tags = ["vim"]
topics = []
description = ""
+++
<p>O como se dice en Inglés: <em>capitalization</em>, se puede lograr fácilmente en <a href="http://www.vim.org/" target="_blank">vim </a> mediante el empleo de mayúsculas al comienzo de oraciones a través del uso de una expresión regular o regex, sin la necesidad de utilizar algún que otro script (que puede causar efectos secundarios en el funcionamiento), para lograr el reemplazo de las minúsculas.</p>

<p>En el website de programadores de superuser.com, <a href="http://superuser.com/questions/737130/automatically-capitalize-the-first-letter-of-sentence-in-vim" target="_blank">superuser.com/questions/737130/automatically-capitalize-the-first-letter-of-sentence-in-vim</a> se hace esta misma pregunta para lograr el reemplazo automático de minúsculas por mayúsculas al principio de cada oración.</p>

<p>Una de las repuestas <a href="#script"><sup id="fnref">1</sup></a> hace énfasis de esto mediante la adición de un unas líneas de script o programa de ejecución.</p>

<p>El problema que esto conlleva, y como uno de los usuarios comentó,</p>

<blockquote>
<p>The only problem is this script seems to add a noticeable lag when typing</p>
</blockquote>

<p>Es que mientras más extenso sea el documento, más se experimenta el lag o el retraso en el ingreso de caracteres. Es decir, la óptima funcionalidad se pierde parcialmente. Solo es necesario en tener un documento que comprenda un número de ciento y algo líneas, (y esto es sin contar que haya encima de ello algunas que otras líneas de código), para notar la diferencia.</p>

<p>Considero que sin tanta complicación que más tarde nos puede afectar, la mínima utilización de un reemplazo de caracteres mediante una expresión regular, tuviese mejores resultados.</p>

<p>Para cambiar la minúscula por mayúscula sería necesario entonces algo como:</p>

<pre><code> $ :%s/\.[a-z]/\U&amp;/g
</code></pre>

<p>e. g.,  si el espacio después de la puntuación fue ingresado, no se te olvide cambiar el código encima con el espacio sobrante correspondiente, tal como</p>

<pre><code> $ :%s/\. [a-z]/\U&amp;/g
</code></pre>

<p>y para lograr el intercambio al comienzo de cada línea, entonces</p>

<pre><code> $ :%s/^[a-z]/\U&amp;/g
</code></pre>

<p>reemplaza la minúscula desde el comienzo.</p>

<p>Para reemplazar múltiples patrones de búsqueda, se debe emplear el sufijo <code>e</code> después de la expresión regular con la que se modificaría la búsqueda,  separado de una barra vertical <code>|</code> que separe los dos grupos, es decir:</p>

<pre><code> $ :%s/^[a-z]/\U&amp;/ge | %s/\. [a-z]/\U&amp;/ge
</code></pre>

<p>Otras de las maneras de emplear esta <em>expresión regular</em> es mediante la substitución de <code>[a-z]</code> por <code>\w</code>. una búsqueda rápida en <code>:help</code> nos indica que <code>\w</code> equivale a <code>[0-9A-Za-z]</code></p>

<p>por lo tanto se pudiese emplear algo tal como</p>

<pre><code> $ :%s/^\w/\U&amp;/ge | %s/\. \w/\U&amp;/ge 
</code></pre>

<p><strong>Footnotes</strong></p>

<p><a href="#fnref"> ↩︎ </a>
   <a name="script"> </a> Respuesta de usuario de vim para el empleo de un script que reemplace minúscula por mayúscula pero que causa lag en documentos <a
href="http://superuser.com/a/737155" target="_blank"> http://superuser.com/a/737155</a>
