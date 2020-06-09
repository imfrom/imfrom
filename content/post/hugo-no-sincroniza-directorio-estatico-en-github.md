+++
title = "Hugo No Sincroniza Directorio Estatico en Github"
date = "2016-09-10T10:09:44-05:00"
draft = true
tags = ["git", "hugo"]
topics = []
description = ""
+++
<p>Después de realizar varias pruebas donde traté de evaluar algún que otro theme en Hugo, me di cuenta que el problema era más serio que lo pensaba.</p>

<p>Tenía en mente llevar las pruebas con ciertos temas minimalistas, o como se diría en español: simples, que me permitiesen llevar a cabo flexibles modificaciones locales., y de ahí partir con ello.</p>

<p>La mayoría de los temas en Hugo están constituidos por ciertos paquetes de láminas en estilo de cascadas, o con las siglas en inglés por CSS, y al igual que otros pequeños ficheros en Javascript.</p>

<p>Cabe aclarar que la mayoría, por no decir todos, emplean las últimas tecnologías en gráficos que validen la convención estándar establecida por el consorcio W3C.</p>

<p>Les recomiendo a todos aquellos que estén interesados en generadores estáticos del web, que evalúen a <a href="https://gohugo.io/" title="Hugo" target="_blank">Hugo</a> y de ahí decidir si es o no el motor más eficiente y fiable que hace uso de estas últimas tecnologías. Por supuesto que no sería justo si no se menciona otros como <a href="https://hexo.io/" target="blank">hexo</a>, desarrollado en Javascript por ejemplo, que al igual que el primero, son motores que valen la pena en emplearlos en la producción de sitios web, en la elaboración de blogs, al igual que con cualquier otra documentación.</p>

<p>El motor <a href="https://gohugo.io/" target="blank">Hugo</a>, fue desarrollado en golang - un lenguaje de programación que fue creado en Google - es uno de los más recientes en este campo de generadores estáticos que ha sido recibido con mucho interés por programadores y otros entusiastas en computación. Pero sobre esto hablaré en otro artículo.</p>

<p>Como dije al principio, en esta ocasión me interesaba más la flexible estructuración del blog que más que nada, mediante la evaluación de algunos de los <a href="https://themes.gohugo.io/" target="blank">temas</a> que están disponibles.</p>

<p>Le había hecho algunos que otros cambios a uno de ellos intitulado purehugo y basado mayormente en <a href="https://en.wikipedia.org/wiki/bootstrapCDN" target="blank">bootstrapCDN</a> logré llevar a cabo algunos que otros cambios, me mortificaba la idea que no podía omitir la generación de todos los posts en la raíz del servidor. Por mucho que traté de hacer los cambios, la creación de una página que no sería mostrada en la página principal del servidor, era casi imposible. Tampoco quería emplear más tiempo que el necesario en lograr esto.</p>

<p>Decidí entonces en descargar una plantilla temática que lleva de nombre <a href="https://themes.gohugo.io/shiori/" target="blank">shiori</a>, que fue portado o transferido de la implementación original del tema del mismo nombre por su autor Shusaku Uesugi.</p>

<p>Estaba tratando de implementar en la estructura de la página un tema sencillo y este susodicho tema mostraba llenar los requisitos para ello.</p>

<p>Después de descargarlo en el directorio <code>themes</code></p>

<pre><code>$ git clone https://github.com/chibicode/hugo-theme-shiori shiori
</code></pre>

<p>decidí en ponerlo en práctica</p>

<pre><code>$ hugo server -t shiori 
</code></pre>

<p>y el servidor local en el ordenador mostraba sin problemas la paginación correcta, al igual que todos los posts. No intenté en llevar otros cambios de modificación, porque la primera vez que ejecuté <code>hugo new post/test</code> que proseguiría con la creación de un post en el archivo de contenido, un error acerca del fichero <code>archetypes</code> se había generado.</p>

<p>Traté de encontrar más información acerca de ello. Pero la única explicación acerca de esto tenía que ver con la actualización no solo de <code>hugo</code> sino de todas las dependencias de este:</p>

<pre><code>go get -u -v github.com/spf13/hugo
github.com/spf13/hugo (download)
github.com/fsnotify/fsnotify (download)
Fetching https://golang.org/x/sys/unix?go-get=1
</code></pre>

<p>El servidor local me mostraba las modificaciones.</p>

<p>Una búsqueda más tarde en Google me refirió a <a href="https://github.com/spf13/hugo/issues/1802" target="_blank">iHugo 0.16-DEV (Jan 2016) fails to sync theme’s static directory on Linux</a> el cual trataba este problema.</p>

<p>Aparentemente una de las dependencias tenía que ser actualizada, y por lo tanto la bandera <code>-u</code> tenía que ser especificada apropiadamente para la instalación del motor <a href="https://gohugo.io/" target="blank">Hugo</a>.</p>
