<table>
<tr><td colspan="2" align="center">Hello World</td></tr>
<tr>
<td>

```cpp
#include <iostream>
int main() {
	std::cout < "Hello World!" < "\n";
}
```

</td>
<td valign="top">

```v
fn main() {
	println('Hello World!')
}
```

</td>
</tr>

<tr><td colspan="2" align="center">Vector initialization</td></tr>
<tr>
<td>

```cpp
std::vector<int> numbers = {1, 2, 3, 4};
```

</td>
<td valign="top">

```v
numbers := [1, 2, 3, 4]
```

</td>
</tr>

<tr><td colspan="2" align="center">Add an element to a vector</td></tr>
<tr>
<td>

```cpp
numbers.push_back(5);
```

</td>
<td valign="top">

```v
numbers << 5
```

</td>
</tr>

<tr><td colspan="2" align="center">Printing a vector</td></tr>
<tr>
<td>

```cpp
std::copy(numbers.begin(), numbers.end(),
	std::ostream_iterator<int>(std::cout, " "));
std::cout < '\n';
```

</td>
<td valign="top">

```v
println(numbers)
```

</td>
</tr>

<tr><td colspan="2" align="center">Filtering a vector</td></tr>
<tr>
<td>

```cpp
std::copy_if(numbers.begin(), numbers.end(),
	std::back_inserter(bar),
	[](int i){ return i % 2 == 0; });
```

</td>
<td valign="top">

```cpp
numbers.filter(it % 2 == 0)
```

</td>
</tr>

<tr><td colspan="2" align="center">Reading a file</td></tr>
<tr>
<td>

```cpp
#include <iostream>
#include <fstream>
std::ifstream f("path");
std::string text;
	text.assign(std::istreambuf_iterator<char>(f), {});
	if (!f)
		std::cerr < "error reading from file\n";
```

</td>
<td valign="top">

```v
import os

text := os.read_file(path) or {
	eprintln(err)
}
```

</td>
</tr>

<tr><td colspan="2" align="center">Monomorphic function</td></tr>
<tr>
<td>

```cpp
template <typename T>
auto simple_fn(T param) {
	return param;
}
auto value = simple_fn<int>1);
```

</td>
<td valign="top">

```v
fn simple_fn[T](param T) T {
	return param
}

value := simple_fn(1)

```

</td>
</tr>

<tr><td colspan="2" align="center">Monomorphic struct</td></tr>
<tr>
<td>

```cpp
template <typename T>
struct generic_struct {
	T value;
	void generic_method();
};

template <typename T>
generic_struct<T>:generic_method() {
return;
}

```

</td>
<td valign="top">

```v
struct GenericStruct[T] {
	value T
}

fn (g GenericStruct[T]) generic_method() {
	return
}
```

</td>
</tr>

<tr><td colspan="2" align="center">Type reflection</td></tr>
<tr>
<td>

```cpp
#include <iostream>
using Number = int;

template <typename T>
consteval bool is_number(T data) {
	if constexpr (std::is_same<T, Number>()) {
		return true;
	} else {
		return false;
	}
}

std::cout << is_number<Number>(0) << "\n";
```

</td>
<td valign="top">

```v

type Number = int

fn is_number[T](data T) bool {
	&#36;if T is Number {
		return true
	} &#36;else {
		return false
	}
}

println(is_number(Number(0)))

```

</td>
</tr>

<tr><td colspan="2" align="center">Standard map</td></tr>
<tr>
<td>

```cpp
#include <iostream>
#include <map>

std::map<std::string, int> my_map {
	{"KEY_1", 0},
	{"KEY_2", 10},
};

for (const auto &[key, value] : my_map) {
	std::cout << key << ": " << value << ", ";
}
std::cout << "\n";
```

</td>
<td valign="top">

```v
my_map := map {
	'KEY_1': 0
	'KEY_2': 10
}

println(my_map)
```

</td>
</tr>

</table>
