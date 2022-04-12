<table>
<tr><td colspan="2" align="center">Hello World</td></tr>
<tr>
<td>
<pre class="highlight highlight-source-v">
#include &lt;iostream>
int main() {
  std::cout &lt;&lt; "Hello World!" << "\n";
}
</pre>
</td>
<td valign="top">
<pre>
fn main() {
  println('Hello World!')
}
</pre>
</td>
</tr>


<tr><td colspan="2" align="center">Vector initialization</td></tr>
<tr>
<td>
<pre>
std::vector&lt;int> numbers = {1, 2, 3, 4};
</pre>
</td>
<td valign="top">
<pre>
numbers := [1, 2, 3, 4]
</pre>
</td>
</tr>

<tr><td colspan="2" align="center">Add an element to a vector</td></tr>
<tr>
<td>
<pre>
numbers.push_back(5);
</pre>
</td>
<td valign="top">
<pre>
numbers &lt;&lt; 5
</pre>
</td>
</tr>

<tr><td colspan="2" align="center">Printing a vector</td></tr>
<tr>
<td>
<pre>
std::copy(numbers.begin(), numbers.end(),
    std::ostream_iterator<int>(std::cout, " "));
std::cout << '\n';
</pre>
</td>
<td valign="top">
<pre>
println(numbers)
</pre>
</td>
</tr>


<tr><td colspan="2" align="center">Filtering a vector</td></tr>
<tr>
<td>
<pre>
std::copy_if(numbers.begin(), numbers.end(),
  std::back_inserter(bar), 
  [](int i){ return i % 2 == 0; });

</pre>
</td>
<td valign="top">
<pre>
numbers.filter(it % 2 == 0)
</pre>
</td>
</tr>



<tr><td colspan="2" align="center">Reading a file</td></tr>
<tr>
<td>
<pre>
#include &lt;iostream>
#include &lt;fstream>
std::ifstream f("path");
std::string text;
  text.assign(std::istreambuf_iterator<char>(f), {});
  if (!f)
    std::cerr << "error reading from file\n";
</pre>
</td>
<td valign="top">
<pre>
import os
text := os.read_file(path) or {
  eprintln(err)
}
</pre>
</td>
</tr>




</table>


