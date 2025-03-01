# Migrating Mbed Projects to Visual Studio Code (VS Code)

## Overview

With Mbed OS reaching its end-of-life (EOL), there is a need to migrate existing Mbed projects to a new development environment. Visual Studio Code (VS Code) is a versatile, lightweight, and powerful code editor that can be configured for embedded development. This guide provides a detailed overview of how to migrate your Mbed projects to VS Code, including the installation of the ARM GCC toolchain.

## Benefits of Migrating to VS Code

1. **Versatility**: VS Code supports a wide range of programming languages and development environments.
2. **Extensibility**: A vast library of extensions is available to enhance functionality, including support for embedded development.
3. **Lightweight**: VS Code is lightweight and fast, making it suitable for various development environments.
4. **Strong Community**: VS Code has a robust community, offering extensive resources and support.

## Prerequisites

Before starting the migration, ensure you have the following:

- **Visual Studio Code Installed**: Download and install VS Code from [Visual Studio Code](https://code.visualstudio.com/).
- **ARM GCC Toolchain**: Install the ARM GCC toolchain for compiling ARM Cortex-M microcontrollers.
- **CMake**: Install CMake for managing the build process.

## Installing ARM GCC Toolchain

### Windows

1. **Download the ARM GCC Toolchain**:
   - Visit the [ARM Developer website](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm) and download the latest version of the GCC ARM toolchain for Windows.

2. **Install the Toolchain**:
   - Run the installer and follow the instructions to install the toolchain. By default, it installs to `C:\Program Files (x86)\GNU Tools Arm Embedded\`.

3. **Add to PATH**:
   - Add the bin directory of the installed toolchain to your system's PATH environment variable. For example: `C:\Program Files (x86)\GNU Tools Arm Embedded\8 2019-q3-update\bin`.

### macOS

1. **Download the ARM GCC Toolchain**:
   - Visit the [ARM Developer website](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm) and download the latest version of the GCC ARM toolchain for macOS.

2. **Install the Toolchain**:
   - Extract the downloaded file and move the extracted directory to a desired location, such as `/usr/local/gcc-arm`.

3. **Add to PATH**:
   - Add the bin directory of the toolchain to your PATH environment variable. You can do this by adding the following line to your `.bashrc`, `.zshrc`, or `.profile` file:
     ```sh
     export PATH=/usr/local/gcc-arm/bin:$PATH
     ```

### Linux

1. **Download the ARM GCC Toolchain**:
   - Visit the [ARM Developer website](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm) and download the latest version of the GCC ARM toolchain for Linux.

2. **Install the Toolchain**:
   - Extract the downloaded file and move the extracted directory to a desired location, such as `/opt/gcc-arm`.

3. **Add to PATH**:
   - Add the bin directory of the toolchain to your PATH environment variable. You can do this by adding the following line to your `.bashrc`, `.zshrc`, or `.profile` file:
     ```sh
     export PATH=/opt/gcc-arm/bin:$PATH
     ```

## Migration Steps

### Step 1: Install Required Extensions

Install the following extensions in VS Code to facilitate embedded development:

- **C/C++**: Microsoft C/C++ extension for IntelliSense, debugging, and code browsing.
- **Cortex-Debug**: Extension for debugging ARM Cortex-M microcontrollers.
- **CMake Tools**: Extension for CMake integration.

### Step 2: Set Up the Project Directory

Organize your project directory to align with VS Code's expectations. Move your Mbed source files to a suitable directory and create necessary configuration files.

```
your_project/
├── .vscode
│   └── settings.json
│   └── launch.json
│   └── c_cpp_properties.json
├── include
│   └── some_header.h
├── lib
│   └── some_library
│       └── some_library.cpp
├── src
│   └── main.cpp
├── CMakeLists.txt
└── mbed-os
```

### Step 3: Create `CMakeLists.txt`

Create a `CMakeLists.txt` file to configure the build process. Below is an example configuration:

```cmake name=CMakeLists.txt
cmake_minimum_required(VERSION 3.13)
set(CMAKE_SYSTEM_NAME Generic)
set(CMAKE_SYSTEM_PROCESSOR arm)

# Specify the cross compiler
set(CMAKE_C_COMPILER arm-none-eabi-gcc)
set(CMAKE_CXX_COMPILER arm-none-eabi-g++)

# Set the project name
project(MbedProject)

# Include the Mbed OS directory
include_directories(${CMAKE_SOURCE_DIR}/mbed-os)

# Add source files
file(GLOB_RECURSE SOURCES "src/*.cpp" "lib/*.cpp")

# Create the executable
add_executable(${PROJECT_NAME} ${SOURCES})
```

### Step 4: Configure VS Code Settings

Create the `.vscode` directory and add the following configuration files:

#### `settings.json`

```json name=.vscode/settings.json
{
    "cmake.generator": "Unix Makefiles"
}
```

#### `launch.json`

```json name=.vscode/launch.json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Cortex Debug",
            "type": "cortex-debug",
            "request": "launch",
            "servertype": "jlink",
            "device": "STM32F401RE",
            "interface": "swd",
            "runToMain": true,
            "cwd": "${workspaceRoot}",
            "executable": "${workspaceRoot}/build/MbedProject.elf"
        }
    ]
}
```

#### `c_cpp_properties.json`

```json name=.vscode/c_cpp_properties.json
{
    "configurations": [
        {
            "name": "ARM",
            "includePath": [
                "${workspaceFolder}/**",
                "${workspaceFolder}/mbed-os/**"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/arm-none-eabi-gcc",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "gcc-arm"
        }
    ],
    "version": 4
}
```

### Step 5: Build and Debug

Use the CMake Tools extension to configure and build your project:

1. Open the Command Palette (`Ctrl+Shift+P`) and run `CMake: Configure`.
2. Run `CMake: Build` to compile your project.
3. Use the Cortex-Debug extension to debug your project. Set breakpoints and start a debug session using `F5`.

## Common Migration Issues

### 1. Library Management

Ensure all necessary libraries are included in the `CMakeLists.txt` file and correctly configured.

### 2. Build Configuration

Some build settings in Mbed (`mbed_app.json`, `mbed_lib.json`) may need to be translated to CMake settings. Ensure all relevant configurations are correctly set.

### 3. Debugging Setup

Properly configure the `launch.json` file for your specific microcontroller and debugger interface.

## Testing and Validation

Thoroughly test your migrated project to ensure all functionalities work as expected. Implement automated testing to catch any issues early. Validate performance and stability in the new environment.

## Additional Resources

- **Visual Studio Code Documentation**: [VS Code Docs](https://code.visualstudio.com/docs)
- **ARM GCC Toolchain**: [ARM GCC](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm)
- **CMake Documentation**: [CMake Docs](https://cmake.org/documentation/)

## Conclusion

Migrating from Mbed OS to Visual Studio Code offers several benefits, including versatility, extensibility, and a robust development environment. By following the steps outlined in this guide, you can successfully transition your projects to VS Code and continue development with confidence. If you encounter any issues or need further assistance, the VS Code community and documentation are valuable resources.
