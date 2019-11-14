On all systems except Linux libc is the only official system API. (WinAPI in case of Windows.)

The syscall API is unstable.

The Go team used to use syscalls instead of libc on non-Linux systems, but they moved to libc instead:

https://github.com/golang/go/issues/30401

V will support libc free builds on Linux soon.