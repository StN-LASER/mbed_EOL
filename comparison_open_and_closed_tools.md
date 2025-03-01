# Comparison of Mbed Migration Platforms

## Abstract

As Mbed OS reaches its end-of-life (EOL), developers need to migrate their existing projects to alternative development environments. This paper provides a comprehensive comparison of various open-source and best-of-class platforms suitable for migrating Mbed projects. The platforms discussed include Visual Studio Code (VS Code), PlatformIO, Eclipse with GNU MCU Eclipse Plugins, STM32CubeIDE, Keil MDK, IAR Embedded Workbench, and SEGGER Embedded Studio. Each platform's features, benefits, and common migration issues are examined, and a comparison table is provided to aid in platform selection.

## Introduction

Mbed OS has been a popular choice for embedded development on ARM Cortex-M microcontrollers. With its EOL, developers must transition to new environments to continue their projects. This paper explores various open-source and best-of-class platforms to facilitate this migration. Each platform offers unique features and benefits, and this paper provides a structured approach to evaluating and selecting the most suitable platform.

## Benefits of Migrating to Open Source and Best-of-Class Platforms

### Versatility

Open-source and best-of-class platforms support a broad spectrum of programming languages and development environments, making them flexible choices for various projects.

### Extensibility

A vast library of extensions and plugins is available to enhance functionality, including support for embedded development, debugging, and code analysis.

### Community and Professional Support

The robust communities and professional support surrounding these platforms ensure extensive resources, tutorials, and assistance, aiding developers in troubleshooting and enhancing their projects.

## Prerequisites

Before initiating the migration, ensure the following tools are installed:

- **Visual Studio Code**: Download and install from [Visual Studio Code](https://code.visualstudio.com/).
- **PlatformIO**: Install from [PlatformIO](https://platformio.org/).
- **Eclipse with GNU MCU Eclipse Plugins**: Download and install from [GNU MCU Eclipse](https://gnu-mcu-eclipse.github.io/).
- **STM32CubeIDE**: Download and install from [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html).
- **Keil MDK**: Download and install from [Keil MDK](https://www.keil.com/).
- **IAR Embedded Workbench**: Download and install from [IAR Embedded Workbench](https://www.iar.com/).
- **SEGGER Embedded Studio**: Download and install from [SEGGER Embedded Studio](https://www.segger.com/products/development-tools/embedded-studio/).
- **ARM GCC Toolchain**: Necessary for compiling ARM Cortex-M microcontrollers.
- **CMake**: Required for managing the build process.

## Comparison of Platforms

The following table provides a comparison of the various platforms based on key features and capabilities:

| Feature                       | Visual Studio Code (VS Code) | PlatformIO                   | Eclipse with GNU MCU Eclipse Plugins | STM32CubeIDE                 | Keil MDK                     | IAR Embedded Workbench       | SEGGER Embedded Studio       |
|-------------------------------|------------------------------|-----------------------------|--------------------------------------|-----------------------------|-----------------------------|-----------------------------|-----------------------------|
| **Extensibility**             | High                         | High                        | Medium                               | Medium                      | Low                         | Low                         | Medium                      |
| **Community Support**         | Strong                       | Strong                      | Medium                               | Medium                      | Strong                      | Strong                      | Medium                      |
| **Professional Support**      | Available                    | Available                   | Limited                              | Available                   | Strong                      | Strong                      | Strong                      |
| **Ease of Use**               | High                         | High                        | Medium                               | Medium                      | High                        | High                        | Medium                      |
| **Supported Frameworks**      | Multiple                     | Multiple                    | Limited                              | STM32 specific              | ARM specific                | ARM specific                | ARM specific                |
| **Debugging Capabilities**    | Strong                       | Strong                      | Medium                               | Strong                      | Strong                      | Strong                      | Strong                      |
| **Integration**               | Strong with extensions       | Strong with extensions      | Requires plugins                     | Integrated                  | Integrated                  | Integrated                  | Integrated                  |
| **Cross-Platform**            | Yes                          | Yes                         | Yes                                  | Yes                         | No                          | No                          | Yes                         |
| **License Cost**              | Free                         | Free                        | Free                                 | Free                        | Paid                        | Paid                        | Free to Paid                |
| **Target Audience**           | General                      | General                     | General                              | STM32 developers            | Professional ARM developers | Professional ARM developers | Professional ARM developers |

## Additional Resources

- **Visual Studio Code Documentation**: [VS Code Docs](https://code.visualstudio.com/docs)
- **PlatformIO Documentation**: [PlatformIO Docs](https://docs.platformio.org/)
- **GNU MCU Eclipse Documentation**: [GNU MCU Eclipse Docs](https://gnu-mcu-eclipse.github.io/)
- **STM32CubeIDE Documentation**: [STM32CubeIDE Docs](https://www.st.com/en/development-tools/stm32cubeide.html)
- **Keil MDK Documentation**: [Keil MDK Docs](https://www.keil.com/)
- **IAR Embedded Workbench Documentation**: [IAR Embedded Workbench Docs](https://www.iar.com/iar-embedded-workbench/)
- **SEGGER Embedded Studio Documentation**: [SEGGER Embedded Studio Docs](https://www.segger.com/products/development-tools/embedded-studio/)
- **ARM GCC Toolchain**: [ARM GCC](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm)
- **CMake Documentation**: [CMake Docs](https://cmake.org/documentation/)

## Conclusion

Migrating from Mbed OS to open-source and best-of-class platforms such as Visual Studio Code, PlatformIO, Eclipse with GNU MCU Eclipse Plugins, STM32CubeIDE, Keil MDK, IAR Embedded Workbench, and SEGGER Embedded Studio offers several benefits, including versatility, extensibility, and robust development environments. By evaluating the features and capabilities of each platform, developers can select the most suitable environment for their projects. The communities and extensive documentation for each platform provide valuable resources for troubleshooting and enhancing projects during and after the migration process.

## References

1. Visual Studio Code Documentation. Retrieved from [Visual Studio Code Docs](https://code.visualstudio.com/docs).
2. PlatformIO Documentation. Retrieved from [PlatformIO Docs](https://docs.platformio.org/).
3. GNU MCU Eclipse Documentation. Retrieved from [GNU MCU Eclipse Docs](https://gnu-mcu-eclipse.github.io/).
4. STM32CubeIDE Documentation. Retrieved from [STM32CubeIDE Docs](https://www.st.com/en/development-tools/stm32cubeide.html).
5. Keil MDK Documentation. Retrieved from [Keil MDK Docs](https://www.keil.com/).
6. IAR Embedded Workbench Documentation. Retrieved from [IAR Embedded Workbench Docs](https://www.iar.com/iar-embedded-workbench/).
7. SEGGER Embedded Studio Documentation. Retrieved from [SEGGER Embedded Studio Docs](https://www.segger.com/products/development-tools/embedded-studio/).
8. ARM GCC Toolchain. Retrieved from [ARM Developer](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm).
9. CMake Documentation. Retrieved from [CMake Docs](https://cmake.org/documentation/).