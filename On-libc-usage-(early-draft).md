On all systems except Linux libc is the only official system API. (WinAPI in case of Windows.)

The syscall API is private or unstable.

The Go team used to use syscalls instead of libc on non-Linux systems, but they moved to libc instead:

https://github.com/golang/go/issues/16272

https://github.com/golang/go/issues/30401

V can support libc free builds on Linux by passing `-freestanding`.

libc/syscalls discussion:
https://news.ycombinator.com/item?id=18439100