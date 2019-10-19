Found an error/typo? Or do you want to translate something that hasn't been translated yet? It's very simple to do so.

Go to the V website's repo, modify the translation file (e.g. `de.tr`), and submit a pull request.

https://github.com/vlang/website

You can do this right in your browser by clicking "Edit this file" in the top right corner. Cloning the repo and modifying it locally works too of course.  

The translation files are simple text files, each translation consists of a key and a value:

<table>
<tr>
<td>
<b>en.tr</b>
<br>
&nbsp;
<pre>
examples
Examples
-----
documentation             &nbsp;
Documentation
-----
modules
Modules
-----
</pre>
</td>

<td>
<b>de.tr</b>
<br>
&nbsp;
<pre>
examples
Beispiele
-----
documentation             &nbsp;
Dokumentation
-----
modules
Module
-----
</pre>

</td>
</tr>
</table>

Leave the key unmodified.

Not the entire website has been updated to use the translations. Most of it is plain HTML right now, the entire website will be converted by the end of the year.

An example of updating the website:

`<h2>Documentation</h2>` becomes `<h2>%documentation</h2>`

The `documentation` key must be defined in `en.tr` and other translation files. If it's missing in other translation files, the English value will be used.

Thank you for your contribution!

The documentation will become translatable after V 1.0 release in December.