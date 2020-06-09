+++
title = "Reemplazos en Vim"
date = "2016-11-07T14:42:55-05:00"
draft = true
tags = ["vim"]
topics = []
description = ""
+++
<p>Estos son algunos de los reemplazos que se pudieran realizar en vim:</p>

<pre><code>:s/\zs/\r/g
</code></pre>

<p>will have this string of characters: abcdefghi</p>

<p>tendrá esta cadena de caracteres: abcdefghi</p>

<p><strong>result</strong>:</p>

<p>a<br>
b<br>
c<br>
d<br>
e<br>
f<br>
g<br>
h<br>
i</p>

<p>Por otra parte la siguiente ejecución:</p>

<pre><code>:s/\s/\r/g 
</code></pre>

<p>will have</p>

<p>esto es una prueba</p>

<p><strong>result</strong>:</p>

<p>esto<br>
es<br>
una<br>
prueba</p>

<p>and <code>:s/\n//g</code></p>

<p>will have something like</p>

<p>a<br>
b<br>
c<br>
d</p>

<p><strong>results</strong>:</p>

<p>abcde</p>

<pre><code>:s/\n/ /g
</code></pre>

<p>will have something like</p>

<p>esto<br>
es<br>
una<br>
prueba</p>

<p><strong>result</strong>: esto es una prueba</p>

<p>por supuesto, se puede ver que en algunos casos se utiliza <code>\n</code>, mientras que en otros se utiliza <code>\r</code>, es necesario recordar que en cada reemplazo y substitución en vim, se logra mediante <code>:s/texto para reemplazar/substituir con</code>.</p>

<p>Primero antes que todo el delimitador de barra oblicua <code>/</code> es la separación de lo que se quiere modificar con lo que se modificaría.</p>

<p>Es decir, por ejemplo, donde <code>texto para reemplazar</code> es la expresión regular que se desea cambiar, o los caracteres del texto que se desean modificar, mientras que <code>substituir con</code> es el nuevo ingreso que tomará lugar.</p>

<p>En este caso, para entender este procedimiento, no hay mejor ayuda en vim, que ir directo a la documentación con <code>:help \n</code> o mediante <code>:h \n</code> para abreviar, y también entender el por qué difiere de <code>:help \r</code></p>

<p>Creo que una de las mejores respuestas sobre esto, se encuentra en <a href="http://stackoverflow.com/a/18961239">http://stackoverflow.com/a/18961239</a> que especifica que “in the syntax <code>s/foo/bar</code>, <code>\r</code> and <code>\n</code> have different meanings depending on context.</p>

<p>En nuestro caso sería <code>s/texto para reemplazar/substituir con</code>.</p>

<p>Por lo tanto esto equivaldría a:</p>

<p>En el caso de <code>texto para reemplazar</code>, es decir, <code>s/&lt;texto para reemplazar&gt;</code> antes del segundo delimitador <code>/</code>:<br>
<code>\n</code> sería una newline  o un salto de línea.<br>
<code>\r</code> en este caso sería CR que es la tecla <code>Enter</code>, tecla de retorno o de regreso.</p>

<p>En el caso de <code>substituir con</code>, es decir, <code>s/&lt;texto para reemplazar&gt;/&lt;substituir con&gt;</code>, o los caracteres que se encuentren después de la segunda barra <code>/</code>:<br>
<code>\n</code> seria un octeto nulo<br>
<code>\r</code> en este caso es una <code>newline</code> o un salto de línea.</p>
