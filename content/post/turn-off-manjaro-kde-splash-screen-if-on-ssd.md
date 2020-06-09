+++
title = "Turn Off Manjaro Kde Splash Screen if on Ssd"
date = "2017-02-15T04:02:19-05:00"
draft = true
tags = ["arch", "manjaro", "ssd"]
topics = []
description = ""
+++

<p>Posicionado desde hace meses en el quinto escalafón de la lista de las distribuciones basadas en <a href="http://distrowatch.com/" target="_blank">Linux</a>, la distribución <a href="https://manjaro.org/" target="_blank">Manjaro </a>, basada en la impresionante distribución <a href="http://archlinux.org/" target="_blank">Arch Linux</a>, y que hace uso del magnífico sistema de administración de paquetes <strong>Pacman</strong> de este último, emplea los últimos e innovadores temas de interfaz gráficos en muchas de las ediciones, tanto de la comunidad, como aquellas que son aprobadas oficialmente. <a href="#man"><sup id="manref">1</sup></a></p>

<p>No tuve problema alguno con la instalación del sistema operativo. Todo parecía funcionar sin problemas. La tarjeta gráfica del ordenador se había identificado apropiadamente durante el proceso de instalación, al igual que la tarjeta inalámbrica que permite el acceso al Internet para la continuación de cualquier actualización que se necesitaría llevar a cabo más tarde.</p>

<p>El mayor problema recaía en el tiempo que tomaba antes que el escritorio gráfico de este sistema operativo estuviera disponible.</p>

<p>Después de reinicializar las sesiones en varias ocasiones, me di cuenta que este lapso que estaba experimentando, no era algo necesariamente deseable, y peor aún, porque muchas veces fallaba por completo en cargar el entorno gráfico KDE, mientras que el resto del sistema estaba simplemente congelado. Esto imposibilitaba por ende, el acceso a la línea de intérprete de comandos, al igual que a cualquier operación de revisión de errores. Bajo estas condiciones, el sistema entero se paralizaba y por consiguiente era algo inaceptable.</p>

<p>Aunque el origen de este problema no era tan sencillo de rastrear, me di cuenta que ‘startx’ podía ser el causante. Una búsqueda rápida en Google dio como resultados en su primer hit de búsqueda a una pregunta similar titulada: <em>Plasma desktop 5 boots very slowly</em> que había sido hecha en el boletín de Arch Linux.</p>

<p>La pregunta del op era la siguiente:</p>

<blockquote>
<p>is there any way to debug Plasma-desktop 5 loading process to figure out why it is slow?</p>
</blockquote>

<p>a lo que una respuesta continuaba después que decía:</p>

<blockquote>
<blockquote>
<p>if on ssd, it’s better to turn off splash screen. <a href="#ssd"><sup id="ssdref">2</sup></a></p>
</blockquote>
</blockquote>

<p>Y eso era exactamente lo que estaba ocurriendo, o por lo menos en mi caso.</p>

<p>Después de ello y una vez en el menú gráfico del sistema, se selecciona las configuraciones del sistema o <em>settings</em> . Una vez allí y bajo el tabulador <em>Appearance</em> se selecciona <em>Workspace Theme</em>.</p>

<p><img src="/images/manjaro-workspace.png" alt="manjaro-workspace">
<img src="/images/tema-del-espacio-de-trabajo.png" alt="manjaro-espacio-de-trabajo"></p>

<p>Una vez que se seleccione el <em>Tema</em> y como se mostrará en la siguiente figura, se debe especificar que <em>None</em> o <em>ninguno</em>.</p>

<p><img src="/images/manjaro-splash.png" alt="manjaro-splash">
<img src="/images/no-splash-en-manjaro-kde.png" alt="manjaro-no-splash"></p>

<p><strong>Footnotes</strong></p>

<ol>
<li><p><a name="man"></a><a href="https://manjaro.org/get-manjaro/" target="_blank">Lanzamientos oficiales de Manjaro</a><a href="#manref">&crarr;</a></p></li>

<li><p><a name="ssd"></a>Sugerencia de un usuario en ajustar el valor pre-configurado del espacio de trabajo. Para más información acerca de ello visite el siguiente sitio que ofrece más detalles acerca de la conversación <a href="https://bbs.archlinux.org/viewtopic.php?pid=1557789#p1557789" target="_blank" title="turn off splash if on ssd">turn off splash if on ssd</a> <a href="#ssdref"> ↩︎</a></p></li>
</ol>
