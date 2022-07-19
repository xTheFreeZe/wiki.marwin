<table>
<tr><td colspan="2" align="center">Hello World</td></tr>
<tr>
<td>
<pre class="highlight highlight-source-v">
#include &lt;iostream>
int main() {
  std::cout &lt;&lt; "Hello World!" &lt;&lt; "\n";
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
std::cout &lt;&lt; '\n';
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
    std::cerr &lt;&lt; "error reading from file\n";
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

<tr><td colspan="2" align="center">Monomorphic function</td></tr>
<tr>
<td>
<pre>
template &lt;typename T&gt;
auto simple_fn(T param) {
  return param;
}
auto value = simple_fn&lt;int&gt;(1);
</pre>
</td>
<td valign="top">
<pre>
fn simple_fn&lt;T&gt;(param T) T {
  return param
}

value := simple_fn(1)
</pre>
</td>
</tr>


<tr><td colspan="2" align="center">Monomorphic struct</td></tr>
<tr>
<td>
<pre>
template &lt;typename T&gt;
struct generic_struct {
  T value;
  void generic_method();
};

template &lt;typename T&gt;
generic_struct&lt;T&gt;::generic_method() {
  return;
}
</pre>
</td>
<td valign="top">
<pre>
struct GenericStruct&lt;T&gt; {
  value T
}


fn (g GenericStruct&lt;T&gt;) generic_method() {
  return
}
</pre>
</td>
</tr>


<tr><td colspan="2" align="center">Type reflection</td></tr>
<tr>
<td>
<pre>
#include &lt;iostream&gt;
using Number = int;

template &lt;typename T&gt;
consteval bool is_number(T data) {
  if constexpr (std::is_same&lt;T, Number&gt;()) {
    return true;
  } else {
    return false;
  }
}

std::cout << is_number&lt;Number&gt;(0) << "\n";
</pre>
</td>
<td valign="top">
<pre>

type Number = int

fn is_number&lt;T&gt;(data T) bool {
  &#36;if T is Number {
    return true
  } &#36;else {
    return false
  }
}


println(is_number(Number(0)))
</pre>
</td>
</tr>

<tr><td colspan="2" align="center">Standard map</td></tr>
<tr>
<td>
<pre>
#include &lt;iostream&gt;
#include &lt;map&gt;
std::map<std::string, int> my_map {
  {"KEY_1", 0},
  {"KEY_2", 10},
};

for (const auto &[key, value] : my_map) {
  std::cout << key << ": " << value << ", ";
}
std::cout << "\n";
</pre>
</td>
<td valign="top">
<pre>


my_map := map {
  'KEY_1': 0
  'KEY_2': 10
}

println(my_map)
</pre>
</td>
</tr>


</table>


