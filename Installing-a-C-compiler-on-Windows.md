You can use either MinGW-w64 or Visual Studio. Visual Studio takes a lot more space, but its header files are more up-to-date, so Visual Studio is preferred if you plan to use the UI library.

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

