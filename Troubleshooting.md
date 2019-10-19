You can see how V invokes the C backend compiler with `v -show_c_cmd file.v` .

You can produce a .c file, *without* compiling it further with `v -o file.c file.v` . 
That is useful, if you want to integrate v as a transpiler into the build system (probably using a Makefile) of an existing large C code base, or if you just want to read the produced C code.

You can prevent V from deleting the intermediate .c file (which is useful if you want to use a debugger like gdb or msvc) by: `v -debug file.v` .

You can pass `-g`, which has the effect of -debug, and in addition will make the debugger information to have V line numbers, instead of C ones (NB: this will make the intermediate .c file harder to read).


You can also set the VFLAGS environment variable to pass one or more flags to v, so that you do not have to type them manually everytime.
Windows (cmd): `set VFLAGS=-debug -show_c_cmd`
Windows (PowerShell): `$env:VFLAGS="-debug -show_c_cmd"`
Unix (bash): export VFLAGS="-debug -show_c_cmd"

Windows:
If you get this error while running the V REPL, and you are using msvc:
`'gcc' is not recognized as an internal or external command, operable program or batch file.`

... please try:
```shell
set VFLAGS=-os msvc
v.exe runrepl

```