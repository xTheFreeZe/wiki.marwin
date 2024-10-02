If you are trying to build V on a Windows ARM device and encounter erros when running `make.bat`, such as C compilation errors due to missing libraries, follow the steps below to resolve the issue.

## 1. Install Visual Studio C++ Tools

To address the missing libraries, you will need to install the Visual Studio C++ build tools and the `cl` compiler. [You can download the Visual Studio Build Tools from here](https://visualstudio.microsoft.com/en/vs/community/)

> Ensure that you install Visual Studio with the **Desktop development with C++** package. 
> This will include the necessary libraries the Microsoft C++ (MSVC) compiler.

## 2. Build V with MSVC

After installing the required tools, you can attempt to build V using the `MSVC` toolchain:

```bash
make.bat -msvc
```

> While the full build process may still fail due to incomplete support for ARM chips, 
> this step will successfully generate a `v.exe` executable.

## 3. Testing the V Compiler

Once the `v.exe` executable is created, you can test the V compiler by running the following commands:

```bash
v -cc msvc examples/hello_world.v
```

Then, run the compiled executable:

```bash
v -cc msvc run examples/hello_world.v
```

If successfull, you should see the output `Hello, World!` in the console.

## 4. Setting the Environment Variable

To avoid specifying the `-cc msvc` flag each time you compile a V program, you can set the `VFLAGS` environment variable to ensure that the `MSVC` compiler is used by default. Follow [this](https://www.tenforums.com/tutorials/121855-edit-user-system-environment-variables-windows.html#option3) guide and set the `VFLAGS` environment variable to `-cc msvc`.

```bash
v run examples/hello_world.v
```