V can be used as a platform independent script like language too.

All you have to do, is save your file with a .vsh extension.

By doing it, v will make functions inside the os module automatically available to your scripts, without you having to import them manually.

You also will not need to specify a main function (that is a work in progress, for now please do so ... simple linear examples work, but for now it is more stable with a `fn main(){}` ).

<table>
<tr><td colspan="2" align="center">Hello World</td></tr>
<tr>
<td>
<pre class="highlight highlight-source-v">
#!/usr/bin/env bash
echo "Hello world"
</pre>
</td>
<td valign="top">
<pre>
  println('Hello World!')
</pre>
</td>
</tr>


<tr><td colspan="2" align="center">Listing files in current folder</td></tr>
<tr>
<td>
<pre>
#!/usr/bin/env bash
ls
</pre>
</td>
<td valign="top">
<pre>
files := ls('.') or { panic(err) }
println( files)
</pre>
</td>
</tr>

</table>
