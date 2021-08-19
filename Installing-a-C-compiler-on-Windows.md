**Q: What Windows versions are supported?**

V uses recent Windows features like UTF-8 and color output support in console, IPv6 and native TLS support on sockets, etc. Windows 10 Fall Creators Update (**1709**) or later is the recommended Windows version for best compatibility. Previous versions are supported as well, but are not as well tested and may lack some features.

***

**Q: How can I build V?**

You will need to install [git](https://gitforwindows.org).

Then, you can install and build V from source (the recommended way of installing it) by launching `cmd.exe`, `cd`ing to your install directory of preference (preferably a path with no spaces or non-ASCII characters) and running these commands:

```
git clone https://github.com/vlang/v
cd v
.\make.bat
```

The entire process may take anywhere from 5 to 60 seconds, depending on your internet speed.

***

**Q: Do I need to install a C compiler?**

Due to its small size and very fast compile speeds, V downloads TCC automatically when running `make.bat`, and uses it by default in normal (debug) builds. However, V will attempt to use an alternative compiler (if installed) in `-prod` mode for better optimization, and installing one of these optimizing compilers is recommended.

***

| C Compiler           | Compile speed | Disk usage  | Optimizations (with `-prod`) |
|---------------------:|---------------|-------------|---------------|
| TCC (default)        | very fast     | very low    | very few      |
| MinGW (GCC/clang)    | slow          | medium      | very many     |
| Visual Studio (MSVC) | medium        | very high   | many          |

#### (1) TCC

TCC is a very lightweight C compiler. Its main advantages are that it takes up very little storage space (~5MB), and compiles much more quickly than the other compilers listed here. However, it has several limitations, and an additional compiler is recommended.
 - It barely optimizes the resulting binaries, so resulting executables will be slower and larger. That's partly why it compiles faster.
 - It may not be as stable as other compilers. If you're doing C interop yourself, you may possibly find that some libraries may not compile with TCC, but do compile with one of the other compilers; if this happens to you, you can open an issue over in [the tccbin repo](https://github.com/vlang/tccbin).

    *Please note that the [original TCC](https://repo.or.cz/tinycc.git) isn't fully compatible with V, and V distributes [its own patched binary](https://github.com/vlang/tccbin/tree/thirdparty-windows-amd64).*

#### (2) MinGW

You can get an up-to-date build of MinGW [here](https://winlibs.com/) (recommended), or [here](https://github.com/mstorsjo/llvm-mingw/releases). The main benefit with these compiler toolchains is that the release archives are self contained. There is NO installation necessary. Just ~1GB of disk space.

1) download a .zip file from the links above.
2) unpack the downloaded archive into a folder, say `C:\mingw\`
3) add the `bin` subfolder (`C:\mingw\bin\`) to your PATH.

If you want to uninstall this compiler, you can simply delete the folder where you unpacked the zip (eg. `C:\mingw\`).

#### (3) Visual Studio

Visual Studio takes up a lot more space (~10GB), but may be useful if you're planning on doing C interop with the Windows SDK / WinAPI.

[Download](https://visualstudio.microsoft.com/vs/) and install Visual Studio 2019. The community edition will suffice. In the installer select `Visual Studio core editor`, `Desktop development with C++`, and `Windows 10 SDK`.
