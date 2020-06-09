+++
title = "Manjaro Announces Password Weakness en Los Instaladores De Dvd/usb"
date = "2017-06-27T13:20:54-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>Recientemente en <a href="http://distrowatch.com/" target="_blank">DistroWatch</a> se publicó el anuncio del lanzamiento de la última versión de <a href="https://manjaro.org/" target="_blank">Manjaro</a> que incluye importantes actualizaciones.</p>

<p><img src="/images/2017-06-27-manjaro-announcement.png" alt=""></p>

<p>Entre estas actualizaciones se encuentran las nuevas versiones de los instaladores gráficos tanto como <strong>thus</strong> al igual que <strong>calamares</strong>.</p>

<p>También se anuncia la fragilidad en la generación de la contraseña o la clave que tanto el programa <strong>thus</strong> como <strong>calamares</strong> emplean durante el proceso de instalación a través tanto del ya mencionado <strong>thus</strong> o de <strong>calamares</strong> que en hashtag con modo predecible se utiliza durante la creación de estas contraseñas. <a href="https://imfrom.github.io/post/manjaro-announces-password-weakness/#shadow"><sup id="shadowref">1</sup></a></p>

<p>Las versiones más recientes de <strong>thus</strong> y de <strong>calamares</strong> no están afectadas.</p>

<p>Por lo tanto es recomendable acceder al fichero que contiene estos errores y verificar si tu sistema está afectado.</p>

<p>Primero antes que todo para recordarnos quiénes somos - si por casualidad se nos olvidó el nombre de usuario, en la terminal:</p>

<pre><code> $ whoami
</code></pre>

<p>Que nos imprime el nombre de usuario</p>

<p>Una vez con esta información y con privilegios de usuario, es decir, mediante <code>sudo</code>  accede al fichero <code>/etc/shadow</code> mediante tu editor de texto.</p>

<p>Desde la terminal selecciona uno de los siguientes:</p>

<pre><code> sudo emacs /etc/shadow 
</code></pre>

<p>o</p>

<pre><code> sudo vim /etc/shadow 
</code></pre>

<p>o</p>

<pre><code> SUDO_EDITOR=kate sudoedit /etc/shadow 
</code></pre>

<p>Ingresa tu contraseña de usuario después para leer el fichero y verificar si la contraseña necesita ser regenerada.</p>

<p>La penúltima línea del fichero comienza con tu nombre de usuario, es decir, con el valor que <code>whoami</code> devolvió anteriormente, seguido de <code>$6$</code>, pero si la penúltima línea del fichero <code>/etc/shadow</code> contiene tu nombre de usuario encerrado por dos signos <code>$</code>, entonces lo más probable es que necesitas crear nuevas contraseñas. Recuerda que tu nombre de usuario es el valor que <code>whoami</code> devolvió en la terminal. Este nombre de usuario no debe estar encerrado por los dos signos <code>$</code>.</p>

<p>Si necesitas corregir este error, y desde la terminal:</p>

<pre><code> $ passwd 
</code></pre>

<p>cuyo comando invocará</p>

<pre><code> $ Current password:
</code></pre>

<p>Necesitas ingresar tu actual contraseña, y después especificar tu nueva contraseña, lo cual generará el hashtag correcto en el fichero <code>/etc/shadow</code>.</p>

<p>Antes de cerrar el archivo <code>/etc/shadow</code> que tenía estos errores, asegúrate que <strong>root</strong> no tiene los mismos problemas que el usuario. En este caso, <strong>root</strong> es la primera línea del archivo <code>/etc/shadow</code> lo cual es más fácil de revisar.</p>

<p>Por ejemplo, si aparece:</p>

<pre><code> root: $6$ 
</code></pre>

<p>y después de ello aparece tu <code>whoami</code> encerrado entre dos signos <code>$</code>, también tienes que arreglarlo con la generación de una <code>passwd</code> para <strong>root</strong>.</p>

<p>Para acceder <strong>root</strong>:</p>

<pre><code> $ sudo su
</code></pre>

<p>que por consiguiente estarás ejerciendo todos los comandos con los máximos privilegios desde la terminal. Si por casualidad no requiere la contraseña porque por ejemplo, haz accedido anteriormente con privilegios administrativos que utilizaste para cambiar la clave de usuario, asegúrate en ingresar en la línea de comando el ya mencionado:</p>

<pre><code> # passwd 
</code></pre>

<p>el cual invocará que especifiques tu contraseña de root. Acto seguido a ello ingresa tu nueva contraseña.</p>

<p>En el caso de <strong>shadow-</strong> no hay que hacer ninguna modificación. Es decir, el fichero <strong>shadow-</strong> que es seguido de un diptongo, es un archivo de copia del original.</p>

<p>Para más detalles acerca de esto vea la página en <a href="https://forum.manjaro.org/t/manjaro-installers-password-weakness/26322" target="_blank">Manjaro installers - password weakness</a></p>
