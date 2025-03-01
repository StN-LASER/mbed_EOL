# Migrating from Mbed OS to PlatformIO

## Overview

Using PlatformIO instead of the Mbed Online Compiler or Mbed CLI doesn't necessarily mean you are using a completely different compiler, but it does mean you are using a different build system and development environment. Here's a breakdown of what changes and what remains the same:

### What Changes:

1. **Build System and Environment**:
   - **Mbed**: Uses its own build tools and environment, typically accessed via the Mbed Online Compiler or Mbed CLI.
   - **PlatformIO**: Uses its own build system integrated into a variety of development environments (e.g., VS Code, Atom) and can be accessed via the PlatformIO CLI.

2. **Project Configuration**:
   - **Mbed**: Configuration is typically done through `mbed_app.json` and `mbed_lib.json` files.
   - **PlatformIO**: Configuration is done through the `platformio.ini` file.

3. **Library Management**:
   - **Mbed**: Uses the Mbed OS library management system.
   - **PlatformIO**: Uses its own library management system, which may require different steps for including and managing dependencies.

### What Remains the Same:

1. **Compiler**:
   - Both Mbed and PlatformIO often use the GCC ARM toolchain (GNU Arm Embedded Toolchain) as the default compiler for ARM Cortex-M microcontrollers.
   - You can also configure PlatformIO to use different compilers if needed, but by default, it will use the same or similar toolchains that Mbed uses.

2. **Source Code**:
   - The source code of your project (e.g., `main.cpp`, libraries) remains the same. The code written for Mbed should compile and run in PlatformIO with minimal changes, assuming all necessary libraries and dependencies are correctly configured.

## Example `platformio.ini` Configuration

Here is an example `platformio.ini` file to help you get started with PlatformIO:

```ini name=platformio.ini
[env:nucleo_f401re]
platform = ststm32
board = nucleo_f401re
framework = mbed
build_flags = -DMBED_CONF_PLATFORM_STDIO_BAUD_RATE=115200
monitor_speed = 115200
```

## Example Project Structure

Ensure your project structure aligns with PlatformIO's expectations:

```
your_project/
├── include
│   └── some_header.h
├── lib
│   └── some_library
│       └── some_library.cpp
├── src
│   └── main.cpp
└── platformio.ini
```

## Migration Steps

1. **Install PlatformIO**: Install PlatformIO in your preferred environment (VS Code, CLI, etc.).

2. **Initialize a PlatformIO Project**: Navigate to your project directory and run:
    ```sh
    platformio init --board <your_board>
    ```

3. **Move Files**: Move your Mbed source files to the `src` directory and any libraries to the `lib` directory.

4. **Configure `platformio.ini`**: Create and configure the `platformio.ini` file as shown above.

5. **Build and Upload**: Use PlatformIO to build and upload your project:
    ```sh
    platformio run
    platformio run --target upload
    ```

By following these steps, you can transition from Mbed to PlatformIO while maintaining the same underlying compiler and minimizing changes to your source code.