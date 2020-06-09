+++
title = "Metadata Irreversible"
date = "2017-12-22T04:13:37-05:00"
draft = true
tags = []
topics = []
description = ""
+++
<p>One of the easiest ways to remove all metadata from a file, is by invoking <a href="https://imfrom.github.io/post/metadata-irreversible/#exiftool"><sup id="refexiftool">1</sup></a></p>

<pre><code> $ exiftool -all= &lt;file&gt;
</code></pre>

<p>However, this has the inconvenience of providing a security risk by reversing it as well with:</p>

<pre><code> $ exiftool -pdf-update:all= &lt;file&gt; 
</code></pre>

<p>which pretty much inserts the metadata back into the file:</p>

<p><img src="/images/exiftool-reversible-metadata-warning.png" alt=""></p>

<p>According to the author of <strong>exiftool</strong> this can be circumvented by issuing <code>qpdf --linearize &lt;file.in&gt; &lt;file.out&gt;</code>. For further info about this see:
<a href="http://owl.phy.queensu.ca/~phil/exiftool/TagNames/PDF.html" target="_blank">PDF tags</a></p>

<p><img src="/images/pdftags-linearized.png" width="700"></p>

<h2 id="references"><strong>References</strong></h2>

<p><a name="exiftool"></a><a href="https://sno.phy.queensu.ca/~phil/exiftool/exiftool_pod.html" target="_blank">exiftool man pages</a> <a href="https://imfrom.github.io/post/metadata-irreversible/#refexiftool">_↩︎</a></p>
