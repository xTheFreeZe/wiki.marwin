Strings can be used to do many things.

# Functions
There are many functions that can be cast on strings.

## Determine the length
If you want to know the length, you don't have to call a function. The length is stored in a field and can be read with `.len`. This is an integer.

## Replace
Replacing characters can be easily done with `.replace(rep, with)`. For example:
```
name := 'John Doe'
name2 := name.replace('o', 'e')
println('Hello, my name is $name2!')
```

This returns `Hello, my name is Jehn Dee!`.

## Get numerical value
You can get the integer value of a string easily with `.int()`. Floats are also an option: `.f32()` Numbers can also be cast to a string the same way: `.str()`.

## Compare strings
Strings can be compared in multiple ways.

### Using comparison operators
You can use the normal comparison operators to compare two strings:

```
fn main() {
    name := 'Apple'
    name2 := 'Banana'

    println(name < name2)   // true
    println(name > name2)   // false
    println(name == name2)  // false
}
```

### Using `compare_strings`
There is also a function that can help you with this: `compare_strings(a, b string)`

This will return `-1`, `0` or `1`:

+ `-1`: `a` is smaller than `b`
+ `0`: `a` and `b` are equal
+ `1`: `a` is bigger than `b`

## Compare strings based on length
Comparing the length of strings can, of course, be done by comparing the `.len` values. You can also use the `compare_strings_by_len(a, b string)`

This will return `-1`, `0` or `1`:

+ `-1`: the length of `a` is smaller than `b`
+ `0`: the length of `a` and `b` are equal
+ `1`: the length of `a` is bigger than `b`