+++
title = "Configurar El Idioma en Manjaro Kde"
date = "2017-02-26T12:44:42-05:00"
draft = true
tags = []
topics = []
description = ""
+++

<p>Para modificar el idioma que los elementos del menú muestren, al igual que el idioma con el que aparecería la hora, la fecha, y otros valores como los de la representación monetaria, se puede ir hasta las <strong>preferencias del sistema</strong> y después dándole a clic a <strong>Configuración regional</strong>.</p>

<p><img src="/images/modify-regional-language-spanish-manjaro-kde.png" alt="regional-language-spanish"></p>

<p>La ventana siguiente que lleva de título <strong>añadir y configurar la configuración regional</strong>, muestra las configuraciones regionales del sistema que  te permite (a mano derecha) añadir el otro idioma que deseas, a la pre-configurada lista de las regiones en el sistema. Debes notar también que una vez que esto sea especificado, el sistema requiere recomenzar para que los cambios se carguen adecuadamente en el sistema.</p>

<p><img src="/images/modify-regional-language-spanish-manjaro-kde-add.png" alt="regional-language-manjaro-add"></p>

<p>Por supuesto que es posible lograr esto mediante el intérprete de comandos a través de <code>localect</code></p>

<p>según se muestra reflejado en <a href="https://wiki.archlinux.org/index.php/locale" target="_blank">wiki.archlinux.org</a></p>

<p>Es decir,</p>

<pre><code> localectl set-locale LANG=es_US.UTF 
</code></pre>

<p>Para ver la lista de los locales en tu sistema, puedes emplear en este caso el siguiente comando:</p>

<pre><code> localectl list-locales 
</code></pre>

<p>y de ahí seleccionaer el idioma regional que quisieras utilizar:</p>

<p>una vez logrado este paso, es necesario ingresar:</p>

<pre><code>localectl set-locale LANG=es_US.UTF-8 
</code></pre>

<p>o el idioma de tu preferencia. Pongo ese solamente como un ejemplo donde se vea ente procedimiento.</p>

<p>Es bueno recalcar y como lo explica el sitio en <a href="https://wiki.archlinux.org/index.php/locale#Setting_the_system_locale" target="_blank">wiki.archlinux.org</a> que el fichero <code>/etc/locale.gen</code> muestra aquellas variables que se encuentran señaladas y que posteriormente serían cargadas en el fichero del sistema <code>/etc/locale.conf</code>.</p>

<p>Para más información acerca de esto vea la sección <strong>Setting the system locale</strong> en la wiki.</p>

<p><strong>Referencias</strong></p>

<p><a href="https://wiki.archlinux.org/">wiki.archlinux.org</a></p>
