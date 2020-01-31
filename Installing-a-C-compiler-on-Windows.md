You can use either MinGW-w64 or Visual Studio or llvm-mingw. Visual Studio takes a lot more space, but its header files are more up-to-date, so Visual Studio is preferred if you plan to use the UI library.

V uses recent Windows features like UTF-8 and color output support in console, IPv6 and native TLS support on sockets, etc. Windows 10 Fall Creators Update (**1709**) or later is the recommended Windows version for most complete compatibility. Windows 7, Windows 8(.1), and Windows 10 before Fall Creators Update are supported too but programs may lack some features and/or it may be hard to correctly link/redistribute recent C runtime library especially when using GNU C compiler.

#### MinGW-w64

[Download](https://github.com/vlang/v/releases/download/v0.1.10/mingw-w64-install.exe) and install MinGW-w64. I recommend installing it in `C:\mingw-w64`. You can use the default installation options.

Make sure the `C:\mingw-w64\bin` directory is in system's PATH, verify that by running `gcc` in your terminal.

_Please note that Cygwin is not supported. It's used to run *nix software that doesn't run on Windows. V has full Windows support, so there's no point in Cygwin._

#### Visual Studio

[Download](https://visualstudio.microsoft.com/vs/) and install Visual Studio 2019. The community edition will suffice. In the installer select `Visual Studio core editor`, `Desktop development with C++`, and `Windows 10 SDK`.



***

Now you can build V by launching cmd.exe and running

```
cd v
make
```

NB: on windows, the make.bat file first tries to locate gcc from MinGW-w64, and will use it, if it finds it. If not, it will try MSVC. If you want use MSVC, when you have both MinGW-w64 AND MSVC, you can pass:
`make -msvc` 


#### llvm-mingw
You can get a recent build of llvm-mingw from https://github.com/mstorsjo/llvm-mingw/releases .

The main benefit with this compiler toolchain, is that the released archives are self contained - there is NO installation necessary. Just ~516MB of disk space.

1) download a .zip file from the link above.

2) unpack the downloaded .ZIP archive into a folder, say c:\llvm

3) put c:\llvm in your PATH.
*or*
3) use `v -cc c:\llvm\bin\gcc.exe` when compiling your v source.


If you do not want to use this compiler toolchain anymore, you can simply delete the folder where you unpacked the zip (eg. C:\llvm).