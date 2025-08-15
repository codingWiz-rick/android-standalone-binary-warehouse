# Android Static Binaries

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Android](https://img.shields.io/badge/Platform-Android-green.svg)](https://www.android.com/)
[![Architecture](https://img.shields.io/badge/Architecture-ARM64%20%7C%20ARM%20%7C%20x86-blue.svg)](https://developer.android.com/ndk/guides/abis)

A comprehensive collection of **statically-linked binaries** optimized for Android devices. These standalone executables require no external dependencies, making them perfect for development, debugging, penetration testing, and system administration on Android platforms.

---

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/codingWiz-rick/android-standalone-binary-warehouse.git
cd android-standalone-binary-warehouse

# Make binary executable
chmod +x ./binaries/your-binary

# Run the binary
./binaries/your-binary --help
```

---

## 📖 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Supported Architectures](#-supported-architectures)
- [Available Binaries](#-available-binaries)
- [Installation](#-installation)
- [Usage Examples](#-usage-examples)
- [Android Integration](#-android-integration)
- [Building from Source](#-building-from-source)
- [Contributing](#-contributing)
- [Security Considerations](#-security-considerations)
- [FAQ](#-faq)
- [License](#-license)

---

## 🔍 Overview

This repository provides a curated collection of essential Unix/Linux tools compiled as **static binaries** for Android devices. Each binary is self-contained and includes all necessary libraries, eliminating dependency hell and compatibility issues commonly encountered when deploying tools on Android.

### Why Static Binaries?

| Advantage | Description |
|-----------|-------------|
| **Zero Dependencies** | No need for additional libraries or system packages |
| **Universal Compatibility** | Works across different Android versions and devices |
| **Easy Deployment** | Simple file transfer - no installation required |
| **Consistent Behavior** | Same functionality regardless of target environment |
| **Offline Ready** | No internet connection required for execution |

---

## ✨ Features

- 🎯 **Ready-to-Use**: Pre-compiled binaries ready for immediate deployment
- 📱 **Android Optimized**: Specifically built for Android ARM and x86 architectures
- 🔒 **Security Focused**: Compiled with security hardening flags
- 📦 **Lightweight**: Optimized for minimal storage footprint
- 🔄 **Version Controlled**: Tagged releases for stability and rollback capability
- 📋 **Well Documented**: Comprehensive usage examples and documentation

---

## 🏗️ Supported Architectures

| Architecture | Status | Description |
|--------------|--------|-------------|
| **ARM64 (aarch64)** | ✅ Primary | Modern 64-bit ARM devices |
| **ARM (armeabi-v7a)** | ✅ Supported | Legacy 32-bit ARM devices |
| **x86_64** | ✅ Supported | Android emulators and x86 tablets |
| **x86** | 🔄 Limited | Legacy x86 devices |

---

## 📦 Available Binaries

### Core System Utilities
| Binary | Version | Description | Size |
|--------|---------|-------------|------|
| `busybox` | 1.36.1 | Swiss Army knife of embedded Linux | ~2.1MB |
| `ls` | GNU 9.4 | Enhanced directory listing | ~1.2MB |
| `grep` | GNU 3.11 | Pattern searching utility | ~890KB |
| `find` | GNU 4.9.0 | File and directory search tool | ~780KB |
| `tar` | GNU 1.35 | Archive manipulation utility | ~1.1MB |

### Network Tools
| Binary | Version | Description | Size |
|--------|---------|-------------|------|
| `curl` | 8.4.0 | HTTP client with SSL support | ~3.2MB |
| `wget` | 1.21.4 | Non-interactive network downloader | ~2.8MB |
| `netcat` | 1.10 | Network connection utility | ~145KB |
| `nmap` | 7.94 | Network discovery and security auditing | ~15.2MB |

### Development Tools
| Binary | Version | Description | Size |
|--------|---------|-------------|------|
| `gcc` | 13.2.0 | GNU Compiler Collection | ~45MB |
| `python3` | 3.11.6 | Python interpreter | ~18MB |
| `node` | 20.9.0 | Node.js runtime | ~32MB |
| `git` | 2.42.0 | Distributed version control | ~8.5MB |

### Text Editors
| Binary | Version | Description | Size |
|--------|---------|-------------|------|
| `vim` | 9.0 | Advanced text editor | ~2.8MB |
| `nano` | 7.2 | Simple text editor | ~580KB |

> 📍 **Note**: Binary availability may vary by architecture. Check the `releases` section for architecture-specific packages.

---

## 🛠️ Installation

### Method 1: Direct Download

1. **Download from Releases**
   ```bash
   wget https://github.com/codingWiz-rick/android-standalone-binary-warehouse/releases/latest/download/android-binaries-arm64.tar.gz
   ```

2. **Extract and Install**
   ```bash
   tar -xzf android-binaries-arm64.tar.gz
   chmod +x binaries/*
   ```

3. **Add to PATH (Optional)**
   ```bash
   export PATH="$PWD/binaries:$PATH"
   echo 'export PATH="$HOME/android-binaries/binaries:$PATH"' >> ~/.bashrc
   ```

### Method 2: Git Clone

```bash
# Clone repository
git clone https://github.com/codingWiz-rick/android-standalone-binary-warehouse.git
cd android-standalone-binary-warehouse

# Make binaries executable
find binaries/ -type f -exec chmod +x {} \;

# Test installation
./binaries/busybox --help
```

### Method 3: ADB Installation (For Android Devices)

```bash
# Push binaries to device
adb push binaries/ /data/local/tmp/
adb shell chmod +x /data/local/tmp/binaries/*

# Test on device
adb shell /data/local/tmp/binaries/busybox ls -la
```

---

## 💡 Usage Examples

### Basic File Operations
```bash
# List directory contents with detailed information
./ls -la /data/

# Search for files by pattern
./find /sdcard/ -name "*.jpg" -type f

# Archive and compress files
./tar -czf backup.tar.gz /sdcard/Documents/
```

### Network Operations
```bash
# Download a file with progress bar
./curl -L -o file.zip https://example.com/file.zip

# Test network connectivity
./netcat -zv google.com 80

# Scan network ports
./nmap -sT 192.168.1.1
```

### Development Tasks
```bash
# Compile C code
./gcc -o hello hello.c

# Run Python scripts
./python3 script.py

# Clone repository
./git clone https://github.com/user/repo.git
```

---

## 📱 Android Integration

### Termux Integration
```bash
# Copy binaries to Termux environment
cp binaries/* $PREFIX/bin/

# Verify installation
which curl
curl --version
```

### Custom ROM Integration
```bash
# Copy to system partition (requires root)
adb root
adb remount
adb push binaries/busybox /system/xbin/
adb shell chmod 755 /system/xbin/busybox
```

### Magisk Module Creation
```bash
# Create Magisk module structure
mkdir -p magisk-module/system/xbin
cp binaries/* magisk-module/system/xbin/
# Add module.prop and service.sh as needed
```

---

## 🔨 Building from Source

### Prerequisites
- Android NDK r25c or later
- CMake 3.22+
- Python 3.8+

### Build Process
```bash
# Clone with submodules
git clone --recursive https://github.com/codingWiz-rick/android-standalone-binary-warehouse.git
cd android-standalone-binary-warehouse

# Set up build environment
export ANDROID_NDK_HOME=/path/to/android-ndk
export TARGET_ARCH=arm64

# Build all binaries
./scripts/build-all.sh

# Build specific binary
./scripts/build-binary.sh curl
```

### Custom Configuration
```bash
# Edit build configuration
vim configs/build-config.json

# Available options:
# - target_arch: arm64, arm, x86_64, x86
# - optimization: -O2, -O3, -Os
# - hardening: true/false
# - static_linking: true/false
```

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Adding New Binaries
1. **Fork and Clone**
   ```bash
   git fork https://github.com/codingWiz-rick/android-standalone-binary-warehouse.git
   git clone https://github.com/YOUR-USERNAME/android-standalone-binary-warehouse.git
   ```

2. **Create Feature Branch**
   ```bash
   git checkout -b add-new-binary-name
   ```

3. **Add Build Script**
   - Create `scripts/build-your-binary.sh`
   - Add entry to `configs/build-config.json`
   - Update documentation

4. **Test and Submit**
   ```bash
   ./scripts/build-binary.sh your-binary
   ./scripts/test-binary.sh your-binary
   git commit -m "Add your-binary v1.0.0"
   git push origin add-new-binary-name
   ```

### Reporting Issues
- 🐛 **Bug Reports**: Use the bug report template
- 💡 **Feature Requests**: Use the feature request template
- 📚 **Documentation**: Help improve our docs

### Development Guidelines
- Follow existing code style and conventions
- Add comprehensive tests for new binaries
- Update documentation and README
- Ensure cross-architecture compatibility

---

## 🔒 Security Considerations

### Binary Verification
```bash
# Verify checksums (provided in releases)
sha256sum -c checksums.txt

# Check binary signatures
gpg --verify android-binaries-arm64.tar.gz.sig
```

### Security Features
- **ASLR**: Address Space Layout Randomization enabled
- **Stack Protection**: Stack canaries and NX bit
- **FORTIFY_SOURCE**: Buffer overflow protection
- **RELRO**: Read-only relocations

### Best Practices
- ✅ Always verify checksums before deployment
- ✅ Use latest releases for security patches
- ✅ Regularly update binaries in production
- ❌ Never run untrusted binaries with elevated privileges
- ❌ Avoid using in sensitive environments without proper audit

---

## ❓ FAQ

### General Questions

**Q: Are these binaries safe to use?**
A: Yes, all binaries are compiled from official sources with security hardening. However, always verify checksums and use the latest versions.

**Q: Will these work on my Android version?**
A: These binaries are tested on Android 7.0+ and should work on most devices. Older versions may have compatibility issues.

**Q: How often are binaries updated?**
A: We follow upstream releases and provide updates monthly or when critical security patches are available.

### Technical Questions

**Q: Why are the binaries so large?**
A: Static linking includes all dependencies, resulting in larger file sizes but eliminating compatibility issues.

**Q: Can I use these in production?**
A: Yes, but ensure you follow security best practices and regularly update to the latest versions.

**Q: How do I request a new binary?**
A: Open an issue with the "binary request" template, including use case and priority information.

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### Third-Party Licenses
Individual binaries may be subject to their respective licenses:
- GNU GPL v3: gcc, grep, tar, etc.
- MIT License: curl, node, etc.
- BSD License: netcat, etc.

See `THIRD_PARTY_LICENSES.md` for complete license information.

---

## 🙏 Acknowledgments

- **Android NDK Team** for providing excellent cross-compilation tools
- **Open Source Communities** for the amazing software we compile
- **Contributors** who help maintain and improve this project

---

## 📧 Contact & Support

- **Issues**: [GitHub Issues](https://github.com/codingWiz-rick/android-standalone-binary-warehouse/issues)
- **Discussions**: [GitHub Discussions](https://github.com/codingWiz-rick/android-standalone-binary-warehouse/discussions)
- **Email**: [codingWiz.rick@gmail.com](mailto:codingWiz.rick@gmail.com)

---

<div align="center">

**⭐ Star this repository if you find it useful!**

[Report Bug](https://github.com/codingWiz-rick/android-standalone-binary-warehouse/issues) • [Request Feature](https://github.com/codingWiz-rick/android-standalone-binary-warehouse/issues) • [Contribute](https://github.com/codingWiz-rick/android-standalone-binary-warehouse/blob/main/CONTRIBUTING.md)

</div>
