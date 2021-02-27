***

**What Windows Versions Are Supported?**

V uses recent Windows features like UTF-8 and color output support in console, IPv6 and native TLS support on sockets, etc. Windows 10 Fall Creators Update (**1709**) or later is the recommended Windows version for most complete compatibility. Windows 7, Windows 8(.1), and Windows 10 before Fall Creators Update are supported too but programs may lack some features and/or it may be hard to correctly link/redistribute recent C runtime library especially when using GNU C compiler.

***

**What C Compilers Are Supported?**

**_64-bit_** Windows users can use **_MinGW-w64_**, **_Visual Studio_**, **_LLVM-MinGW_**, or **_TCC_** (both TCC64 and TCC32). 

**_32-bit_** Windows users can use **_TCC32_**. Other C compilers might also work to some extent but they're not officially supported yet.

***

**How Can I build V?**

After installation of a C compiler you can build V by launching cmd.exe and running below.

```
cd v
make
```

On windows, the `make.bat` file tries to find a compiler on your computer according to below order. 
```
LLVM-MinGW (make -clang)
MinGW-w64 (make -gcc)
MSVC (make -msvc)
TCC (make -tcc/tcc32)
```
If all attempts fail, it will download TCC to `thirdparty/tcc` folder and use it as C backend. So if you have multiple usable compilers on your computer, passing a compiler flag as above is recommended. For example, if you have both MinGW-w64 AND MSVC, use `make -msvc` to specify MSVC as backend. 

***

**Can you give brief instructions on choosing and installing C compilers?**

In short, there's no panacea. Please choose the most suitable one depending on your needs. 

* **MinGW-w64** - GNU GCC - slow compilation | medium disk space | good binary optimization
* **Visual Studio** - Microsoft product - medium compilation speed | huge disk space | medium binary optimization
* **LLVM-MinGW** - Clang with GCC compatibility - slow compilation | medium disk space | good binary optimization
* **TCC** - Tiny C compiler - very fast compilation | very little disk space | only very basic binary optimization

#### (1) MinGW-w64

[Download](https://github.com/vlang/v/releases/download/v0.1.10/mingw-w64-install.exe) and install MinGW-w64. I recommend installing it in `C:\mingw-w64`. You can use the default installation options. Make sure the `C:\mingw-w64\bin` directory is in system's PATH, verify that by running `gcc` in your terminal.

_Please note that Cygwin is not supported. It's used to run *nix software that doesn't run on Windows. V has full Windows support, so there's no point in Cygwin._

#### (2) Visual Studio

Visual Studio takes a lot more space (~10GB), but its header files are more up-to-date, so Visual Studio is preferred if you plan to use the UI library.

[Download](https://visualstudio.microsoft.com/vs/) and install Visual Studio 2019. The community edition will suffice. In the installer select `Visual Studio core editor`, `Desktop development with C++`, and `Windows 10 SDK`.

#### (3) LLVM-MinGW

You can get a recent build of LLVM-MinGW from https://github.com/mstorsjo/llvm-mingw/releases. The main benefit with this compiler toolchain is that the released archives are self contained. There is NO installation necessary. Just ~516MB of disk space.

1) download a .zip file from the link above.

2) unpack the downloaded .ZIP archive into a folder, say c:\llvm

3) put c:\llvm in your PATH.
*or*
3) use `v -cc c:\llvm\bin\gcc.exe` when compiling your v source.

If you do not want to use this compiler toolchain anymore, you can simply delete the folder where you unpacked the zip (eg. `C:\llvm`).

#### (4) TCC

TCC is a very lightweight C compiler. Its main advantages are that it takes up very little storage space (~5MB), and compiles much more quickly than the other compilers listed here. However, it has several limitations. For these reasons, a different and more advanced compiler is recommended.
 - It barely optimizes the resulting binaries, so resulting executables will be slower. That's partly why it compiles faster.
 - It is not as stable as GCC or Visual Studio. While it compiles V and its standard library perfectly, you may encounter issues if working with C interop, or with external modules that depend on C libraries.

Due to its small size, TCC is downloaded automatically if no existing C compiler is found. By default, TCC64 would be downloaded for 64-bit Windows users and TCC32 for 32-bit Windows users.

For 64-bit Windows users, you can also install it manually by using `.\make.bat -tcc`(TCC64) / `.\make.bat -tcc32`(TCC32), or by running `git clone https://github.com/vlang/tccbin/tree/thirdparty-windows-amd64 thirdparty/tcc`(TCC64) / `git clone https://github.com/vlang/tccbin/tree/thirdparty-windows-i386 thirdparty/tcc`(TCC32) from V's root folder.

For 32-bit Windows users, you can also install it manually by using `.\make.bat -tcc`, `.\make.bat -tcc32`, or `git clone https://github.com/vlang/tccbin/tree/thirdparty-windows-i386 thirdparty/tcc` - Any of them would install TCC32 for you.
