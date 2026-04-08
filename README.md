# DLL Injector

This project is a simple DLL injector with a native Windows Win32 Graphical User Interface. It allows users to browse for an external dynamically linked library (DLL) and inject it into a running process. The tool also supports ejecting (unloading) previously injected DLLs from target processes.

## Features

- Native Win32 GUI without heavy dependencies.
- Browse and select a target DLL.
- Select a target process where the DLL will be injected.
- Inject a DLL into a remote process space using standard Windows API methods (CreateRemoteThread).
- Eject (unload) a DLL from a foreign process.

## Architecture Compatibility

The source code itself is architecture-agnostic. However, because this injector relies on the standard CreateRemoteThread mechanism, the architecture of the compiled injector must strictly match the architecture of both the target DLL and the target process.
- If you compile this injector as a 64-bit (x64) application, it can only inject 64-bit DLLs into 64-bit processes.
- If you compile it as a 32-bit (x86) application, it can only inject 32-bit DLLs into 32-bit processes.

By default, modern CMake and MSVC setups will compile this tool for the x64 architecture.

## Prerequisites

- Windows Operating System.
- CMake (version 3.10.0 or higher).
- A C++ compiler supporting C++17 (MSVC is recommended for Windows native projects).

## Compilation

You can compile this project simply using CMake.

1. Open a terminal or a developer command prompt.
2. Navigate to the project root directory.
3. Configure the build directory:
   ```cmd
   mkdir build
   cd build
   cmake ..
   ```
4. Build the executable:
   ```cmd
   cmake --build . --config Release
   ```

Upon a successful build, the `injector.exe` will be located in the `Release` folder within your `build` directory.

## Usage

1. Run the `injector.exe` application.
2. Click the 'Browse' button to locate and select the DLL you wish to inject.
3. Input the target process name or Process ID.
4. Click 'Inject' to load the DLL into the targeted process.
5. If you need to remove the DLL from the process, click 'Unload'.
   
*Note: Depending on the target process permissions, you may need to run this tool as Administrator to successfully inject or eject libraries.*

## Disclaimer

This tool is created for educational and debugging purposes. Ensure you have the right to modify the target applications and always use this software in a legal and compliant manner.
