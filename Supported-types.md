There are many types that V natively supports. Some are interchangeable and many can be cast to others.

## String
A string is an array of characters. Luckily, you don't have to deal with that any longer. You can simply start a string, and keep writing.

```
mut name := 'John'
name += ' '
name += 'Doe'

println('Hello, my name is $name!')
```

Output: `Hello, my name is John Doe!`

As you see, strings can be easily appended and you can even use string interpolation anywhere you want. Strings also have a lot of useful features.

## Integer
Integers can be found in many forms.

### `int`
The easiest is `int`. This is the same as a `i32`, an int of 32 bits. This allows you to store numbers with a maximum value of `2,147,483,647` in them.

### Custom value
You can also define your own integer size. V offers a few flavors to do so: `i8`, `i16`, `i32` and `i64`. You can define a value yourself like this:

```
number := i64(2147483648)
```
#### Rune
A rune is a Unicode code point. It is actually an `i32`. They can be used to cover all of the Unicode characters.

### Unsigned integer
Unsigned integers are really something else than integers in V. They can be casted with `u8`, `u16`, `u32` and `u64`. The maximum value is doubled because an unsigned integer can only be a positive number (or 0).

#### Byte
A byte is just another word for `u8`. It can contain a letter, for example.

```
name := 'John Doe'
char := name.at(0)
```

`char` will now be a byte.

## Boolean
A boolean can only be `true` or `false`. V uses non-capitalized words for this: `statement := true`. They can be extremely helpful because they can be evaluated with if-statements.

```
if (statement) {
  println('statement is true')
}
```

This will indeed print `statement is true`.