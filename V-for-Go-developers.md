<table>
<thead>
<tr><td align="center"><strong>Go</strong></td><td align="center"><strong>V</strong></td></tr>
</thead>
<tr><td colspan="2" align="center">Hello World</td></tr>
<tr>
<td>

```go
package main
import "fmt"
func main() {
	fmt.Println("Hello World!")
}
```

</td>
<td valign="top">

```v
println('Hello World!')
```

</td>
</tr>
<tr><td colspan="2" align="center">Slice initialization</td></tr>
<tr>
<td>

```go
numbers := []int{1, 2, 3, 4}
```

</td>
<td valign="top">

```v
numbers := [1, 2, 3, 4]
```

</td>
</tr>
<tr><td colspan="2" align="center">Add an element to a slice</td></tr>
<tr>
<td>

```go
numbers = append(numbers, 5)
```

</td>
<td valign="top">

```v
numbers << 5
```

</td>
</tr>
<tr><td colspan="2" align="center">Printing a slice</td></tr>
<tr>
<td>

```go
fmt.Println(numbers)
```

</td>
<td valign="top">

```v
println(numbers)
```

</td>
</tr>
<tr><td colspan="2" align="center">Filtering a slice</td></tr>
<tr>
<td>

```go
even := make([]int, 0)
for _, num := range numbers {
	if num % 2 == 0 {
		even = append(even, num)
	}
}
```

</td>
<td valign="top">

```v
even := numbers.filter(it % 2 == 0)
```

</td>
</tr>
<tr><td colspan="2" align="center">Checking if a slice contains an element</td></tr>
<tr>
<td>

```go
contains := false
for _, num := range numbers {
	if num == x {
		contains = true
		break
	}
}
```

</td>
<td valign="top">

```v
contains := x in numbers
```

</td>
</tr>
<tr><td colspan="2" align="center">Reading a file</td></tr>
<tr>
<td>

```go
import (
	"io/ioutil"
	"log"
)
b, err := ioutil.ReadFile(path)
if err != nil {
	log.Println(err)
	return
}
text := string(b)
```

</td>
<td valign="top">

```v
import os
text := os.read_file(path) or {
	eprintln(err)
	return
}
```

</td>
</tr>
<tr><td colspan="2" align="center">Testing a function</td></tr>
<tr>
<td>

```go
package greeter_test
import (
	"testing"
)
func TestHello(t *testing.T) {
	if Hello() != "Hello" {
		t.Fatalf("Hello() failed")
	}
}
```

</td>
<td valign="top">

```v
fn test_hello() {
	assert hello() == 'hello'
}
```

</td>
</tr>
</table>
