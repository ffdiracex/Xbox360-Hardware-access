Xbox 360 Low-Level Library
https://img.shields.io/badge/license-MIT-blue.svg
https://img.shields.io/badge/platform-Xbox%2520360-lightgrey.svg
https://img.shields.io/badge/language-C%252FC%252B%252B-orange.svg

A comprehensive low-level library for Xbox 360 development, providing direct hardware access and system-level functionality for homebrew, research, and custom applications.

✨ Features
Hardware Abstraction: Direct access to Xbox 360 hardware components

System Utilities: Low-level system calls and kernel interactions

Peripheral Control: Support for controllers, storage, and other peripherals

Graphics & Audio: Direct access to Xenos GPU and XMA audio capabilities

Network Stack: Low-level networking functionality

Security Tools: Utilities for working with Xbox 360 security systems

📋 Prerequisites
Development Environment:

Windows 7/10/11 or Linux

Xbox 360 Development Kit (XDK) or compatible toolchain

Visual Studio 2010+ (Windows) or GCC (Linux)

Hardware:

Xbox 360 Console (Retail or DevKit)

JTAG/RGH modded console for unsigned code execution

USB/Network connectivity for deployment

🚀 Installation
Method 1: Manual Setup
bash
# Clone the repository
git clone https://github.com/yourusername/xbox360-lowlevel-lib.git
cd xbox360-lowlevel-lib

# Build the library
make clean
make all

# Deploy to Xbox 360
make deploy IP=192.168.1.100
Method 2: Integration with Existing Projects
bash
# Add as submodule
git submodule add https://github.com/yourusername/xbox360-lowlevel-lib.git libs/xbox360

# Include in your project
# Add to your Makefile/Visual Studio project
📖 Quick Start
Basic Initialization

#include <xbox360/lowlevel.h>

int main() {
    // Initialize the library
    if (xbox360_init() != XBOX360_OK) {
        debug_printf("Failed to initialize library\n");
        return 1;
    }
    
    // Your code here...
    
    // Cleanup
    xbox360_cleanup();
    return 0;
}
Hardware Access Example

#include <xbox360/hardware.h>

void read_temperature() {
    // Read CPU/GPU temperatures
    float cpu_temp = hardware_read_cpu_temperature();
    float gpu_temp = hardware_read_gpu_temperature();
    
    printf("CPU Temperature: %.2f°C\n", cpu_temp);
    printf("GPU Temperature: %.2f°C\n", gpu_temp);
}
📁 Project Structure
text
xbox360-lowlevel-lib/
├── include/                 # Public headers
│   ├── xbox360/
│   │   ├── hardware.h      # Hardware abstraction
│   │   ├── graphics.h      # GPU access
│   │   ├── audio.h         # Audio subsystem
│   │   ├── network.h       # Networking
│   │   └── security.h      # Security utilities
│   └── examples/           # Example headers
├── src/                    # Source code
│   ├── hardware/          # Hardware drivers
│   ├── kernel/            # Kernel interfaces
│   ├── utils/             # Utilities
│   └── lib/               # Library core
├── examples/              # Example programs
│   ├── basic/            # Basic examples
│   ├── hardware/         # Hardware examples
│   └── advanced/         # Advanced usage
├── tests/                # Test suite
├── docs/                 # Documentation
└── tools/               # Build tools and utilities
🔧 Building
Windows (Visual Studio)
bash
# Using provided solution file
open xbox360-lowlevel.sln
# Build for Xbox 360 target
Linux/Cross-compilation
bash
# Set up Xbox 360 toolchain
export XBOX360_TOOLCHAIN=/path/to/xdk

# Build
make ARCH=xbox360 CONFIG=release
Build Options
bash
# Debug build with symbols
make CONFIG=debug

# Release build with optimizations
make CONFIG=release

# Custom configuration
make CUSTOM_CFLAGS="-DSPECIAL_FEATURE"
📚 API Documentation
Core Modules
Hardware Access

// Memory operations
void* xbox360_mmap(uint32_t physical_addr, size_t size);
int xbox360_munmap(void* addr, size_t size);

// PCI/PCIe access
int pci_read_config(uint8_t bus, uint8_t device, uint8_t func, uint16_t offset);
int pci_write_config(uint8_t bus, uint8_t device, uint8_t func, uint16_t offset, uint32_t value);

// GPIO and I/O
void gpio_set(uint32_t pin, bool value);
bool gpio_get(uint32_t pin);
Graphics

// GPU initialization
int gpu_init();
void* gpu_alloc_vram(size_t size);
void gpu_submit_command(uint32_t* cmd_buffer, size_t size);

// Framebuffer
framebuffer_t* fb_create(uint32_t width, uint32_t height, pixel_format_t format);
void fb_flip(framebuffer_t* fb);
Example: Reading Console Information

#include <xbox360/system.h>

void print_system_info() {
    system_info_t info;
    if (get_system_info(&info) == XBOX360_OK) {
        printf("CPU: %s\n", info.cpu_name);
        printf("RAM: %d MB\n", info.total_ram_mb);
        printf("Kernel: %s\n", info.kernel_version);
        printf("Dashboard: %s\n", info.dashboard_version);
    }
}
🧪 Testing
Run the test suite to verify functionality:

bash
# Build and run tests on development PC
make test

# Run specific test suites
./tests/hardware_test
./tests/graphics_test
./tests/network_test
🤝 Contributing
We welcome contributions! Please see our Contributing Guidelines for details.

Fork the repository

Create a feature branch (git checkout -b feature/amazing-feature)

Commit your changes (git commit -m 'Add amazing feature')

Push to the branch (git push origin feature/amazing-feature)

Open a Pull Request

Code Style
Follow the existing code style

Use descriptive variable and function names

Comment complex algorithms

Write tests for new functionality

⚠️ Disclaimer
IMPORTANT: This library is for educational and research purposes only.

Use only on modded consoles you own

Violating terms of service may result in console bans

No warranty provided - use at your own risk

Not affiliated with Microsoft Corporation

📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgments
Xbox 360 homebrew community

Free60 Project

libXenon developers

All contributors and testers

📞 Support
GitHub Issues

Discussion Forum

Wiki: Documentation and Guides

Happy coding! If you find this library useful, please consider giving it a star ⭐

Made with ❤️ for the Xbox 360 homebrew community
