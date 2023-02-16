# Why create V when there are already so many languages? Why not use Go, Rust, C++, Python, etc?

<a href="https://vlang.io/compare" target="_blank">Detailed comparison of V and other languages.</a>

# What language is V written in?

V. The compiler can compile itself. The original version was written in Go.

# Does V use LLVM?

No. V uses C as its backend and will compile directly to machine code by the time of the 1.0 release.

<a href="https://github.com/vlang/v/wiki/On-the-benefits-of-using-C-as-a-language-backend">On the benefits of using C as a language backend.</a>

A separate LLVM backend is developed by the community.

# What about optimization?

For now, V emits C and uses GCC/Clang for optimized production builds. This way you get access to sophisticated optimization.

Such builds are compiled ≈150 times slower than V development builds (but are still an order of magnitude faster than C++ production builds).

This can be a problem for industries where optimization is required during development (for example, AAA games). In this case, hot code reloading can be used.

In the future, V will have its own optimizer.

# Is there garbage collection?

Yes, by default V uses a GC. You can disable it and manage memory manually with `-nogc` or use an experimental autofree via `-autofree`. vlang.io/docs#memory-management

# Is there a package manager?

Yes! V is a very modular language and encourages creation of modules that are easy to reuse.

The page for modules right now is [vpm.vlang.io](https://vpm.vlang.io/).

Submitting your V module takes a couple of seconds.

Installing modules is as easy as `v install sqlite`

# What about concurrency?

It's going to be the same as in Go. To run `foo()` concurrently, just call it with `go`, like `go foo()`. Right now it launches the function in a new system thread. Soon coroutines and the scheduler will be implemented.

# Does V run on bare metal?

There is a `-freestanding` option that excludes libc and vlib, but it is a work in progress and is not the focus of development right now.

# Will I be able to use a custom allocator?

Yes. This hasn't been implemented yet.

# Is V going to change a lot?

No, V will always stay a small and simple language.

https://github.com/vlang/v/blob/master/README.md#stability-guarantee-and-future-changes

# What operating systems are supported?

Windows, macOS, Linux, FreeBSD, OpenBSD, NetBSD, DragonflyBSD, Solaris, Android (Termux).

Android and iOS later this year.

# Who's behind V?

Me and 250+ open source contributors.

# How can it translate C/C++?

It's very hard for one person to write a C/C++ parser. There is a [C2V](https://github.com/vlang/c2v) tool [WIP], that can help you with translation or wrapper generation from C/C++ to V. Clang parser is used for translating C/C++ to V.

# What about editor support?

There are plugins available for a wide range of IDEs and text editors.

| IDE/Editor     | Link to the plugin                                                         |
|----------------|----------------------------------------------------------------------------|
| VS Code        | https://marketplace.visualstudio.com/items?itemName=vlanguage.vscode-vlang |
| JetBrains IDEs | https://intellij-v.github.io/                                              |
| Vim            | https://github.com/ollykel/v-vim                                           |
| Emacs          | https://github.com/damon-kwok/v-mode                                       |
| Sublime Text   | https://github.com/elliotchance/vlang-sublime                              |

Also check out the <a href="https://github.com/vlang/ved">Ved</a> editor, which is written in V. It has V support built in.

V is a small and simple language, it doesn't need a powerful IDE, but a good plugin can automate routine work and make your development process more fun :)

# Why "V"?

Initially, the language had the same name as the product it was created for Volt. The extension was ".v", I didn't want to mess up git history, so I decided to name it V :)

> **Note**
>
> The ".v" extension clashes with (at least) two other known file formats: "Verilog" and "Coq" languages.
> This is actually unfortunate, but so is life sometimes... V language will not change its extension.

It's a simple name that reflects the simplicity of the language, and it's easy to pronounce for everyone in the world.

Please note that the name of the language is "V", not "Vlang" or "V-Lang" etc.
The name is not very searchable (like Go), so use #vlang on Twitter, vlang on Google, etc.

# Any plans to implement macros?

No, sorry. Macros can be really useful, but they complicate the code significantly. Every company, team, and developer can extend the language, and it's no longer possible to jump into a new codebase and immediately understand what's going on.

V will have sophisticated code generation.

# Under which license is V published?

MIT.