# Embedded Linux Systems

---

Linux is ideal for embedded operating systems due to its open-source nature, extensive hardware support, real-time capabilities with patches, strong community and ecosystem, stability, security features, CUSTOMIZATION, and cost-efficiency. Its scalability, familiarity, and long-term support further enhance its suitability for a wide range of embedded applications.

## Terminology

---

- **OpenEmbedded (OE)**: An open-source project and build framework for creating custom Linux distributions tailored to embedded and IoT devices.
- **The Yocto Project**: An open-source collaboration project that builds on OpenEmbedded. It offers a more streamlined and consistent approach to creating custom Linux distributions for embedded systems.
- **Metadata**: Data and configuration information used by OpenEmbedded and the Yocto Project to describe how to build and package software components and configure the Linux system.
- **Recipe**: A set of metadata that describes how to build and package a specific software component, including dependencies, source code location, build instructions, and installation paths.
- **Layer**: A collection of metadata, including recipes and configuration files, organized into a directory structure.
- **Board Support Package (BSP)**: A layer that defines how to build for the specified board. (i.e. a collection of software components, including device drivers, kernel configurations, and bootloader settings, tailored to support a specific hardware platform or development board.)
- **Machine**: Defines the architecture, pins, buses, BSP, etc..
- **Image**: Output of the build process (bootable and executable Linux OS) (i.e. a collection of software components, including device drivers, kernel configurations, and bootloader settings, tailored to support a specific hardware platform or development board.)

## Development Tools

---

In short, BuildRoot and Yocto are used to build custom Linux images.

**BuildRoot**

---

- **Purpose:** Buildroot is a build automation tool that simplifies and streamlines the process of creating a root filesystem and cross-compiling software packages for embedded Linux systems.
- **Key Features:**
    - It focuses on simplicity and ease of use.
    - Provides a simple configuration system to specify the target architecture, desired packages, and system configuration.
    - Automatically downloads, configures, builds, and installs the necessary components, including the Linux kernel, libraries, and applications.
    - Suitable for projects where the goal is to create a minimal, custom Linux system tailored to specific hardware and application requirements.
- **Use Cases:** Buildroot is commonly used in scenarios like IoT devices, single-board computers (SBCs), and custom embedded systems where a lightweight, customized Linux distribution is needed.

**OpenWrt**

---

- **Purpose:** OpenWrt is a Linux-based open-source operating system primarily designed for embedded devices, especially routers and networking equipment.
- **Key Features:**
    - It includes a pre-configured Linux distribution optimized for networking hardware.
    - Supports package management, allowing users to install and manage additional software packages for various network services.
    - Offers a web-based user interface for device configuration and management.
    - Highly extensible and customizable for adding or modifying functionality.
- **Use Cases:** OpenWrt is commonly used in networking devices like wireless routers, access points, and network switches. It enables users to customize and extend the functionality of their network equipment.

**Yocto Project**

---

- **Purpose:** The Yocto Project is a collaborative project that provides tools and metadata for building custom Linux-based distributions for embedded systems.
- **Key Features:**
    - Offers a highly flexible and customizable approach to embedded Linux development.
    - Uses a layer-based system for managing components, allowing users to create and customize distributions to meet specific requirements.
    - Supports cross-compilation, enabling developers to target a wide range of hardware architectures.
    - Provides extensive documentation and a large community for support.
    - USES CACHING (stores compiled binary packages, metadata, and intermediate build artifacts)
- **Use Cases:** The Yocto Project is suitable for a wide range of embedded applications, including industrial systems, automotive infotainment, consumer electronics, and more. It is particularly useful for complex projects that require full control over the Linux distribution and package selection.

## Configuration Steps

---

1. **Cross-Compile Linux Kernel:**
    - Set up a cross-compilation toolchain to compile the Linux kernel for your target architecture.
    - Configure and compile the Linux kernel with the necessary drivers and features for your hardware.
2. **Build Root Filesystem:**
    - Use a tool like Buildroot or the Yocto Project to create a root filesystem for your embedded Linux.
    - Customize the filesystem to include essential libraries, utilities, and packages required for your application.
3. **Bootloader Configuration:**
    - Configure and install a bootloader (e.g., U-Boot) on your embedded system.
    - Specify the kernel image and device tree file in the bootloader's configuration.
4. **Kernel and Root Filesystem Copy:**
    - Copy the compiled Linux kernel image (usually **`zImage`** or **`uImage`**) to the appropriate location on the target device (e.g., an SD card or eMMC).
    - Copy the root filesystem to the target storage media.
5. **Boot Kernel and Init Process:**
    - Boot the embedded system and specify the kernel image and root filesystem in the bootloader's boot command.
    - The kernel will start the init process (usually **`init`** or **`systemd`**), initializing the system with the root filesystem.

## Serial Console

---

The serial console on an embedded Linux system refers to the **complete setup and software configuration** that allows for text-based input and output through a serial connection, which often utilizes UART hardware for the actual data transmission.

**Serial Terminals**

1. **Minicom (Linux):**
    - **Description:** Minicom is a text-based modem control and terminal emulation program. It is lightweight and suitable for a wide range of serial communication tasks.
    - **Features:** Minicom supports various terminal emulation types, file transfer protocols (X/Y/Z-modem), and allows for easy configuration of serial port settings.
    - **Installation:** You can install Minicom using your distribution's package manager. For example, on Debian/Ubuntu-based systems, you can use **`apt`**:
        
        ```arduino
        sudo apt-get install minicom
        ```
        
2. **PuTTY (Windows):**
    - **Description:** PuTTY is a popular and versatile terminal emulator that supports serial communication in addition to SSH, Telnet, and more.
    - **Features:** PuTTY provides a user-friendly interface, supports various terminal emulation types, and allows for easy configuration of serial port settings.
    - **Installation:** You can download PuTTY for Linux from the official website or install it using your distribution's package manager if available

## Citations and Thank Yous

---

These notes were made possible by this wonderful playlist on youtube (and some help formatting/paraphrasing by ChatGPT):

**Embedded Linux Playlist:**

[https://www.youtube.com/watch?v=9vsu67uMcko&list=PLEBQazB0HUyTpoJoZecRK6PpDG31Y7RPB](https://www.youtube.com/watch?v=9vsu67uMcko&list=PLEBQazB0HUyTpoJoZecRK6PpDG31Y7RPB)
