🚀 TtlSemLock

**High-performance distributed semaphores with TTL**

## 📦 Download Ready-to-Use Binaries

TtlSemLock is available as pre-compiled binaries for all major platforms. **No compilation required!**

### 🎯 Latest Release: v0.5.0

**[⬇️ Download from Releases](https://github.com/kabiroman/TtlSemLock/releases/latest)**

- 🐧 **Linux** (AMD64, ARM64)
- 🍎 **macOS** (Intel, Apple Silicon) 
- 🪟 **Windows** (AMD64)
- 🐘 **PHP Client Library**
- 📋 **Protocol Documentation**

## ⚡ Quick Start

### 1. Download & Run Server
```bash
# Linux AMD64
wget https://github.com/kabiroman/TtlSemLock/releases/download/v0.5.0/ttl-semlock-linux-amd64
chmod +x ttl-semlock-linux-amd64
./ttl-semlock-linux-amd64 --port 8765
```

### 2. Use in Your Application
```php
<?php
$semaphore = new TtlSemLock('127.0.0.1', 8765);

if ($semaphore->acquire('critical_section', 60)) {
    try {
        // Your critical section code
        performExpensiveOperation();
    } finally {
        $semaphore->release('critical_section');
    }
}
```

## 🔥 Key Features

- ⚡ **High Performance**: 10,000+ operations/second
- ⏰ **TTL Support**: Automatic lock expiration
- 🔐 **Enterprise Security**: API key authentication
- 🌐 **Universal Protocol**: JSON over TCP
- 🐘 **PHP Ready**: Symfony Lock integration
- 🔄 **Thread-Safe**: Concurrent operations

## 📊 Performance

- **Acquire+Release**: 9,975 ops/sec
- **Extend operations**: 12,814 ops/sec  
- **Stats queries**: 18,100 ops/sec
- **Memory usage**: Minimal
- **Startup time**: <100ms

## 🛠️ What's Included

### Binary Downloads
- Cross-platform executables (no dependencies)
- SHA256 checksums for verification
- Ready-to-run servers

### PHP Client
- Complete PHP library
- Symfony Lock Component integration
- Composer package ready

### Documentation
- Complete protocol specification
- JSON schemas for validation
- API reference and examples

## 🔧 Production Ready

- ✅ **53 Automated Tests** - Complete coverage
- ✅ **Enterprise Security** - API key authentication  
- ✅ **Monitoring** - Built-in statistics
- ✅ **Stability** - Singleton process management
- ✅ **Documentation** - Comprehensive guides

## 🌟 Use Cases

- **Critical Sections** - Prevent race conditions
- **Process Coordination** - Service synchronization
- **Rate Limiting** - Operation frequency control
- **Resource Locking** - TTL-based locks
- **Distributed Systems** - Cross-service coordination

## 📋 System Requirements

- **Linux**: Any modern distribution (glibc 2.17+)
- **macOS**: 10.12+ (Sierra and later)
- **Windows**: Windows 7+ (64-bit)
- **Memory**: 10MB RAM minimum
- **Network**: TCP port (default 8765)

## 🚀 Why TtlSemLock?

- **Zero Dependencies**: Single binary, no installation
- **Language Agnostic**: Works with any programming language
- **Production Proven**: Enterprise-grade reliability
- **Easy Integration**: Drop-in replacement for file locks
- **High Performance**: Designed for high-load environments

## 📚 Documentation

- **[Download Latest Release](https://github.com/kabiroman/TtlSemLock/releases/latest)**
- **Protocol Specification**: Included in release packages
- **PHP Client Guide**: Available in PHP client package
- **Configuration Examples**: Security and performance tuning

## 🔗 Support

- **Issues**: [GitHub Issues](https://github.com/kabiroman/TtlSemLock/issues)
- **Releases**: [GitHub Releases](https://github.com/kabiroman/TtlSemLock/releases)
- **Protocol**: JSON over TCP (documentation in releases)

---

**⚡ Ready to use in production environments!**  
**📦 Download, run, and integrate in minutes!** 
