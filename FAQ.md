**Why create V when there are already so many languages? Why not use Go, Rust, C++, Python etc?**
Detailed comparison of V and other languages.

**What language is V written in?**
V. The compiler can compile itself. The original version was written in Go.

**Does V use LLVM?**
No. V uses C as its backend and will compile directly to machine code by the time of the 1.0 release.

On the benefits of using C as a language backend.

A separate LLVM backend is developed by the community.

**What about optimization?**
For now V emits C and uses GCC/Clang for optimized production builds. This way you get access to sophisticated optimization.

Such builds are compiled ≈150 times slower than V development builds (but are still an order of magnitude faster than C++ production builds).

This can be a problem for industries where optimization is required during development (for example AAA games). In this case, hot code reloading can be used.

In the future V will have its own optimizer.

**Is there garbage collection?**
No. V manages memory at compilation, like Rust: vlang.io/docs#memory-management

**Is there a package manager?**
Yes! V is a very modular language and encourages creation of modules that are easy to reuse.

vpm.vlang.io.

Submitting your V module takes a couple of seconds.

Installing modules is as easy as

v install sqlite

**What about concurrency?**
It's going to be the same as in Go. To run foo() concurrently, just call it with go foo(). Right now it launches the function in a new system thread. Soon coroutines and the scheduler will be implemented.

**Does V run on bare metal?**
Yes! Simply run with -freestanding to exclude libc and vlib. See an example here.

**Will I be able to use a custom allocator?**
Yes. This hasn't been implemented yet.

**Is V going to change a lot? When is v1.0 happening?**
Right now V is under heavy development, lots of things change.

A stable 0.2 version will be released in early June 2019.

1.0 is going to have forward compatibility, meaning that V 1.0 programs will continue to compile and run without change.

It's very important to give developers certainty and stability, and not to be in beta for years. This means that we need to be careful with the 1.0 release. It's going to happen in early 2020.

**What operating systems are supported?**
Windows, macOS, Linux, FreeBSD, OpenBSD, NetBSD, DragonflyBSD, Solaris, Android (Termux).

Android and iOS later this year.

**Who's behind V?**
Me and 250+ open source contributors.

How can it translate C++? It's impossible for one person to write a C++ parser.
Clang parser is used for translating C/C++ to V.

**What about editor support?**
There are basic plugins for VS Code and Vim. Also check out the Vid editor, which is written in V. It has V support built in.

Plugins for Emacs, and other popular editors will be available soon.

V is a small and simple language, it doesn't need a powerful IDE.

**Why "V"?**
Initially the language had the same name as the product it was created for: Volt. The extension was ".v", I didn't want to mess up git history, so I decided to name it V :)

It's a simple name that reflects the simplicity of the language, and it's easy to pronounce for everyone in the world.

Please note that the name of the language is "V", not "Vlang" or "V-Lang" etc.

The name is not very searchable (like Go), so use #vlang on Twitter, vlang on Google etc.

**Any plans to implement macros?**
No, sorry. Macros can be really useful, but they complicate the code significantly. Every company, team, developer can extend the language, and it's no longer possible to jump into a new codebase and immediately understand what's going on.

V will have sophisticated code generation.

**Under which license is V published?**
MIT.