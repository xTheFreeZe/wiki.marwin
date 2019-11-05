V can be used as a platform independent script like language too.

All you have to do is save your file with a .vsh extension.

By doing so, v will make functions inside the os module automatically available to your scripts, without you having to import them manually.

You also will not need to specify the main function (that is a work in progress, for now, please do so ... simple linear examples work, but for now v scripting is more stable with a `fn main(){}` ).

To run your .vsh scripts, on *nix platforms, just run `chmod +x script.vsh` then you can start them like any other script with ./script.vsh . 

On windows, you have to associate the .vsh file extension with v.exe , after that just double click your script.vsh file.

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
#!/usr/local/bin/v
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
#!/usr/local/bin/v
fn main(){
  files := ls('.') or { panic(err) }
  println( files)
}
</pre>
_NB: fn main(){...} is needed only temporarily._
</td>
</tr>

</table>
