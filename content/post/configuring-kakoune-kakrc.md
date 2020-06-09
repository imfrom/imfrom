+++
title = "Configuring Kakoune Kakrc"
date = "2017-12-06T12:50:38-05:00"
draft = true
tags = []
topics = []
description = ""
+++

<p>Configuring the <a href="https://github.com/mawww/kakoune" target="_blank">kakoune text editor</a> initialization file has been nothing short of a chore, as it requires the path environment to be correctly set, before any changes on the <code>kakrc</code> take ahold of the settings.</p>

<p>As the tutorial suggests, see <a href="https://github.com/mawww/kakoune#configuration-autoloading" target="_blank">Configuration and autoloading</a>, if it is launched with the <code>-n</code> switch, kakoune will source the <code>../share/kak/kakrc</code>, but on a unrelated issue but nonetheless relevant about the correct location for the initialization file, the developer clearly stated that:</p>

<blockquote>
<p>The kakrc file in share is Kakounes init script, it is not intended to be user edited. It is actually that script that will load your user configuration in ~/.config/kak/kakrc.</p>
</blockquote>

<p><img src="/images/dont-use-share-kakrc.png" alt=""></p>

See <a href="https://github.com/mawww/kakoune/issues/1102"
target="_blank">clang completion #1102</a>

<p>Thus, it is necessary to set the environment first on any Unix system. The command <code>setenv</code> is used for the <strong>csh</strong> shell, whereas in <strong>bash</strong>, this is accomplished through the <code>export</code> command.</p>

<p>To find out whether for example, <code>XDG_CONFIG_HOME</code> was set, is necessary to invoke on the terminal:</p>

<pre><code> printenv XDG_CONFIG_HOME
</code></pre>

<p>which if it does not return a value, the environment has not been set yet.</p>

<p>To set the environment across sessions, note it accordingly on your <code>bashrc</code> file with the <code>export</code> command:</p>

<pre><code> export XDG_CONFIG_HOME=$HOME/.config
</code></pre>

<p>create a directory <strong>kak</strong> under that environment, and further create your init file <strong>kakrc</strong></p>

<p>Most of the available settings will be available without further modifications. That is, some of the commands that are loaded by not using a <code>kakrc</code> file, will not have to be further tweaked with.</p>

<pre><code> colorscheme &lt;tab completion&gt; &lt;name of theme&gt;
</code></pre>

<p>can be identified without a problem.</p>

<p>There are, however, a handful of those that would have to be further tweaked with, in order to load the <strong>kakrc</strong> init file correctly.</p>

<p>Take for example, <code>autowrap-enable</code>, which normally applies soft wrap manipulation to the lines.</p>

<p>According to the developer,</p>

<blockquote>
<p>autowrapping is provided by the autowrap.kak script (which should be loaded by default), enable it for a buffer with the autowrap-enable command, that you probably want to put in a hook (for example if you want to always enable autowrap, add hook global WinCreate .* %{ autowrap-enable } in your kakrc. the autowrap_column option controls the column on which to autowrap.</p>
</blockquote>

<p>See <a href="https://github.com/mawww/kakoune/issues/419" target="_blank">Noob questions</a></p>

<p><img src="/images/autowrap-kakrc.png" alt=""></p>

<p>Further customizations to map certain keys are also necessary.</p>

<p>For example, to map the <code>\</code> backslash key to say the <code>;</code> semicolon., it’s imperative to precede the *<em>*</em> key with the <code>%</code> percent sign and further enclose the <code>\</code> backslash key within curly brackets <code>{}</code>, so the final code would be something like:</p>

<pre><code> map buffer insert %{\} ';' 
</code></pre>

<p>of course, if the settings are desirable to be loaded globally, then</p>

<pre><code> map global insert %{\} ';'
</code></pre>

<p>needs to be specified accordingly on the initialization file.</p>

<p>See for example this issue: <a href="https://github.com/mawww/kakoune/issues/419" target="_blank">can’t map to backslash</a>, which touched upon the problem, and further linked <a href="https://github.com/mawww/kakoune/issues/1049">https://github.com/mawww/kakoune/issues/1049</a> and <a href="https://github.com/mawww/kakoune/issues/1221">https://github.com/mawww/kakoune/issues/1221</a></p>

<p>It’s certainly two-fold that by specifying:</p>

<pre><code> map buffer insert ';' \ 
</code></pre>

<p>the behavior to have the <code>\</code> inserted, is easily accomplished, as shown on the example above, but the same is not true, by having the same characters inversed within the strings, that would yield the correct results.</p>

<p>for example whereas</p>

<pre><code> map buffer insert ';' \ 
</code></pre>

<p>is correct, a simple <code>map buffer insert '\' ;</code></p>

<p>throws an error with the message <code>parse error: unterminated string '...'</code></p>

<p>It’s therefore necessary to have:</p>

<pre><code> map buffer insert %{;} \
</code></pre>

<p>the same is true if one were to <code>map buffer insert '\' %{;}</code></p>

<p>one of the methods that would work across buffers, is to have such characters enclosed within curly brackets and further preceded by the <code>%</code> sign</p>

<pre><code> map buffer insert %{\} %{;} 
</code></pre>

<p>and</p>

<pre><code> map buffer insert %{;} %{\} 
</code></pre>
