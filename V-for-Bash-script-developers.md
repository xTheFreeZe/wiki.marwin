V can be used as a platform independent script like language too.

All you have to do is save your file with a .vsh extension.

By doing so, v will make functions inside the os module automatically available to your scripts, without you having to import them manually.

You also will not need to specify the main function (that is a work in progress, for now, please do so ... simple linear examples work, but for now v scripting is more stable with a `fn main(){}` ).

To run your .vsh scripts, on *nix platforms, just set the executable bit for your script with for example `chmod +x script.vsh` . After that, you can start the script like any other executable, with `./script.vsh` .

On Windows, you have to associate the `.vsh` file extension with `v.exe` . After that, just double click your `script.vsh` file in Windows Explorer.

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
files := ls('.')?
println(files)
</pre>

</td>
</tr>

</table>
