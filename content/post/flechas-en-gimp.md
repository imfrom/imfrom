+++
title = "Flechas en Gimp"
date = "2016-08-10T14:16:59-05:00"
draft = true
tags = ["gimp"]
topics = []
description = ""
+++

<p>Una de las maneras más fáciles en crear <strong>flechas</strong> en Gimp, sería con la adición de un plugin al directorio <code>scripts</code> de Gimp.</p>

<p>En el sitio de <a href="https://graphicdesign.stackexchange.com/questions/44797/how-do-i-insert-arrows-into-a-picture-in-gimp">https://graphicdesign.stackexchange.com/questions/44797/how-do-i-insert-arrows-into-a-picture-in-gimp</a> se puede encontrar más información en cuanto a esto. Solamente mostraré los pasos visuales para lograrlo.</p>

<pre><code> $cd /directorio-de-gimp/scripts/
</code></pre>

<p>Seguido de</p>

<pre><code> $wget http://registry.gimp.org/files/arrow.scm
</code></pre>

<p>or the archived version </p> 
<pre><code> $wget https://web.archive.org/web/20180218220954/http://registry.gimp.org:80/node/20269 </code></pre>

<p>También pudieras hacer uso de una versión modificada del anterior script pero con flechas curvadas.</p>

<p>puedes obtenerlo mediante</p>

<pre><code> $wget https://web.archive.org/web/20180208191139/http://registry.gimp.org:80/node/28566</code></pre>

<p>Y recomienza el programa Gimp.</p>

<p>Digamos por ejemplo, que seleccionas un nuevo documento. En la caja de herramientas de Gimp (recuerda que si no está visible, siempre puedes activarla a través de la combinación en el teclado de <code>Ctrl</code> y <code>b</code>), podrás ver la nueva inclusión de la ventana de herramienta.</p>

<p>Veamos como funciona con la selección de esta misma caja de herramientas.</p>

<p><img src="/images/selecciona-toolbox.png" alt="caja de herramientas toolbox"></p>

<p>El próximo paso sería seleccionar el icono con el que se marcan los dos puntos de la flecha.</p>

<p><img src="/images/click-twice.png" alt="clic dos vecs"></p>

<p>Asegúrate que el color como se muestra en la figura anterior, esté seleccionado apropiadamente en la caja de herramientas (toolbox).</p>

<p>Una vez que los dos puntos hayan sido marcados, selecciona la barra del menú principal de <code>Herramientas/tools</code>, descendiendo hasta el final y dándole clic a <code>Arrows</code>.</p>

<p>Una vez que le des a <code>Arrows</code> del menú principal de la barra, una ventana que es similar a la que se muestra a continuación te permitirá especificar ciertos valores.</p>

<p><img src="/images/select-tools-arrow.png" alt="selecciona el menú principal de arrows"></p>

<p>Una vez que tengas la ventana abierta, ajusta los valores de porcentajes según el grosor, o el ancho que los ángulos de la flecha debiesen tener cuando se le aplique el color configurado. También puedes especificar otros valores como en rellenar a todo color la punta de la flecha.</p>

<p>Clic <code>ok</code> una vez que los valores sean los acordados.</p>

<p><img src="/images/arrow-done.png" alt="flecha finalizadai"></p>

