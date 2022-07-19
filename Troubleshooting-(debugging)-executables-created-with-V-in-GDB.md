[A minimal V project using VS Code, mingw gcc and gdb, containing .vscode/ with settings](https://github.com/lazalong/V-Hello) -  https://github.com/lazalong/V-Hello

First, it is best to compile your V programs with `-keepc`, and use either `-cg` or `-g` so that the executables will have more debugging information/symbols in them.

`-cg` is better, if you are trying to debug C interoperation, because you will avoid the mental context switches while debugging, seeing everything in one large generated C file.
`-g` is better, for higher level V programs. 
In debugging them, you often do not care much about the generated C, but instead want to see and use .v file line numbers in backtraces and when stepping in the debugger.

After you have compiled your program, it is time to execute it under gdb:
`gdb --args program arg1 arg2`

V generates its own wmain/main/wWinMain C function, that has some setup and cleanup code in it.
Your own `fn main(){}` will instead always be named `main__main`.

So if you want to debug your program from the start, in GDB, you can do:
`b main__main`

This will put a breakpoint on the C function `main_main`.
You can put breakpoints on other functions too, just remember that V uses the `module__submodule__functionname` and `module__submodule__structname__methodname` mapping of V fn/method names to C functions.

Now, it is time to execute your program, which you can do in GDB with the `run` or `r` command.

GDB will stop at your breakpoint(s).

To execute the next statement, without stepping inside if it is a function call, type `next` or `n`.
You can follow the execution inside function calls, with `step` or `s`.

You can inspect local variables with `info locals`.

You can use `bt full` to get a backtrace, showing you all the functions on the call stack, and the local variables in each stack frame.

To show the current value of a specific variable, use either `print var` or `display var`.
The difference, is that with `print var` you will see its value just once.
With `display var`, the value will be displayed every time your program stops, which is handy if you want to trace it.

If you want to inspect the contents of a variable `arr`, that is a V array, you can use `print arr`, but that may not be very helpful, because GDB will only show you the metadata for the array like .len length and capacity .cap, as well as its .data pointer, but *not its content*. If you want to see the contents too, you have to know the type of the elements, and cast the .data pointer.
For example in GDB, `print ((struct string *)_const_os__args.data)[0]`, will show you the first element of os.args, similar to V's `println(os.args[0])` .

