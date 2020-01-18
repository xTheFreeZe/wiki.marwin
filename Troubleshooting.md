You can see how V invokes the C backend compiler with `v -show_c_cmd file.v`.

You can produce a .c file, *without* compiling it further with `v -o file.c file.v` . 
That is useful, if you want to integrate v as a transpiler into the build system (probably using a Makefile) of an existing large C codebase, or if you just want to read the produced C code.

You can prevent V from deleting the intermediate .c file (which is useful if you want to use a debugger like gdb or msvc) by: `v -keep_c file.v`.

You can pass `-g`, which will generate debugging symbols in your executable. The debugging symbols have V line numbers, instead of C ones (NB: this will make the intermediate .c file harder to read).

You can pass `-cg`, which will generate debugging symbols in your executable just like -g. The debugging symbols have C line numbers. NB: this will make the intermediate .c file easier to read, but in effect, you will be debugging an ordinary generated C program, without mapping to the underlying V source code.


You can also set the VFLAGS environment variable to pass one or more flags to v, so that you do not have to type them manually every time.
Windows (cmd): `set VFLAGS=-keep_c -g -cc msvc -show_c_cmd`
Windows (PowerShell): `$env:VFLAGS="-keep_c -g -cc msvc -show_c_cmd"`
Unix (bash): export VFLAGS="-keep_c -g -cc gcc -show_c_cmd"

Windows:
If you get this error while running the V REPL, and you are using msvc:
`'gcc' is not recognized as an internal or external command, operable program or batch file.`

... please try:
```shell
set VFLAGS=-cc msvc
v.exe runrepl

```