# TtlSemLock v0.7.6 Release Notes

**Release Date:** June 28, 2025  
**Release Type:** Infrastructure & CI/CD Enhancement  
**Branch:** main  
**Commit:** f30c540

**[⬇️ Download from Releases](https://github.com/kabiroman/TtlSemLock/releases/latest)**

## 🎯 Overview

TtlSemLock v0.7.6 represents a **major infrastructure milestone**, building upon the enterprise-grade features delivered in v0.7.5. While v0.7.5 introduced the **Graceful Release Framework** with advanced retry logic, v0.7.6 focuses on making these powerful features accessible to the broader community through **Docker Hub integration** and **streamlined deployment**.

## 🚀 What's New in v0.7.6

### 🐳 Docker Hub Integration (Community Access)
- **NEW:** Official Docker Hub repository: [`kabiromandocker/ttlsemlock`](https://hub.docker.com/r/kabiromandocker/ttlsemlock)
- **NEW:** One-command deployment: `docker run kabiromandocker/ttlsemlock:latest`
- **NEW:** Multi-registry support (Docker Hub + GitHub Container Registry)
- **NEW:** Separate debug images: `kabiromandocker/ttlsemlock-debug`

### 🔧 DevOps & Infrastructure Enhancements
- **IMPROVED:** GitLab CI/CD pipeline with Docker Hub integration
- **IMPROVED:** Robust GitHub release handling (handles existing releases)
- **IMPROVED:** Enhanced artifact publishing workflow
- **IMPROVED:** Better error handling and retry logic in CI/CD

### 📦 Distribution & Accessibility
- **UPDATED:** `docker-compose.yml` to use Docker Hub images by default
- **UPDATED:** Multi-registry authentication in CI/CD
- **UPDATED:** Improved Docker image naming conventions
- **UPDATED:** Enhanced caching strategies for faster builds

## 🎉 Major Features Since v0.7.5

### ✨ Advanced Retry Logic Framework (v0.7.4-v0.7.5)
**Enterprise-grade reliability for production environments**

- **🔄 Exponential Backoff + Jitter:** Intelligent retry timing to prevent thundering herd
- **⚙️ Configurable Parameters:** Global and per-lock retry settings
- **🛡️ Split-Brain Prevention:** Advanced conflict resolution mechanisms
- **📊 Retry Metrics:** Comprehensive monitoring of retry attempts and outcomes

```json
{
  "retry": {
    "enabled": true,
    "max_attempts": 5,
    "initial_delay_ms": 100,
    "max_delay_ms": 5000,
    "backoff_multiplier": 2.0,
    "jitter_enabled": true
  }
}
```

### 🛡️ Graceful Release Framework (v0.7.5)
**Resource leak prevention with RAII pattern**

- **🔒 Multiple Lock Acquisition:** Safe handling of multiple semaphores
- **🧹 Automatic Cleanup:** RAII pattern ensures no resource leaks
- **⚡ Exception Safety:** Guaranteed cleanup even during failures
- **🔍 Resource Tracking:** Complete visibility into lock ownership

```php
// PHP Client Example
$lockCollection = new LockCollection($client);
try {
    $lockCollection->acquire(['resource1', 'resource2'], 30);
    // Your critical section here
} finally {
    $lockCollection->releaseAll(); // Automatic cleanup guaranteed
}
```

### 📊 Advanced Observability (v0.7.1-v0.7.2)
**Complete monitoring and memory protection**

- **📈 15+ Prometheus Metrics:** Full observability stack
- **🏥 Multi-port Architecture:** TCP:8765 + HTTP:9765 + Debug:9766
- **🧠 Memory Protection:** Configurable limits (100K locks, 512MB memory)
- **⚠️ Warning System:** Proactive alerts at 80% resource usage

## 📦 Distribution Channels

### Docker Images
```bash
# Production image (Docker Hub)
docker pull kabiromandocker/ttlsemlock:v0.7.6
docker pull kabiromandocker/ttlsemlock:latest

# Debug image (with debugging tools)
docker pull kabiromandocker/ttlsemlock-debug:v0.7.6
docker pull kabiromandocker/ttlsemlock-debug:latest

# GitHub Container Registry (alternative)
docker pull ghcr.io/kabiroman/ttlsemlock:v0.7.6
docker pull ghcr.io/kabiroman/ttlsemlock:latest
```

### 🚀 Quick Start (Now Easier Than Ever!)
```bash
# 1. One-command deployment with Docker Hub
docker run -p 8765:8765 -p 9765:9765 kabiromandocker/ttlsemlock:latest

# 2. Production setup with monitoring
curl -O https://raw.githubusercontent.com/kabiroman/TtlSemLock/main/docker-compose.yml
docker-compose up -d

# 3. Test the advanced retry logic
curl -X POST http://localhost:9765/lock \
  -H "Content-Type: application/json" \
  -d '{"resource":"test","ttl":30,"retry":{"max_attempts":5}}'

# 4. Monitor with Prometheus metrics
curl http://localhost:9765/metrics | grep ttl_semlock
```

### 💡 What You Get Out of the Box
- **🔄 Advanced Retry Logic:** Exponential backoff with jitter for enterprise reliability
- **🛡️ Resource Protection:** Memory limits and graceful cleanup prevent system overload  
- **📊 Full Observability:** 15+ Prometheus metrics for production monitoring
- **🐳 Easy Deployment:** One Docker command gets you production-ready semaphores

## 🔧 Technical Changes

### Docker & Container Improvements
- **Enhanced:** Multi-platform Docker builds (linux/amd64, linux/arm64)
- **Enhanced:** Docker layer caching for faster CI/CD builds
- **Enhanced:** Improved container security and optimization
- **Enhanced:** Better health checks and monitoring integration

### CI/CD Pipeline Architecture
- **Optimized:** Tag-only release pipeline (no pipeline spam)
- **Optimized:** Parallel job execution for faster builds
- **Optimized:** Advanced caching strategies (Go modules, security tools, APK packages)
- **Optimized:** Artifact management and distribution

### Infrastructure as Code
- **Updated:** Docker Compose configuration for production readiness
- **Updated:** Prometheus and Grafana integration examples
- **Updated:** Network and volume management improvements
- **Updated:** Environment variable handling

## 🛠️ Development Experience

### For Developers
- **Simplified:** Local development with Docker Compose
- **Simplified:** Debug image with pre-installed tools (curl, htop, strace, etc.)
- **Simplified:** Automated testing and validation pipelines
- **Simplified:** Multi-platform binary distribution

### For DevOps Teams
- **Enhanced:** GitLab CI/CD integration examples
- **Enhanced:** Multi-registry Docker publishing
- **Enhanced:** Automated release management
- **Enhanced:** Infrastructure monitoring setup

## 📊 Performance & Reliability

### Build Performance
- **Faster:** Docker builds with layer caching
- **Faster:** Go module caching across pipeline runs
- **Faster:** Parallel job execution in CI/CD
- **Faster:** Optimized artifact handling

### Reliability Improvements
- **Robust:** Error handling in CI/CD pipelines
- **Robust:** Retry logic for network operations
- **Robust:** Better DNS and network configuration
- **Robust:** Graceful handling of existing releases

## 🔒 Security & Compliance

### Container Security
- **Enhanced:** Multi-stage Docker builds for minimal attack surface
- **Enhanced:** Non-root user execution in containers
- **Enhanced:** Security scanning integration (Trivy)
- **Enhanced:** Vulnerability monitoring and reporting

### CI/CD Security
- **Secured:** Masked environment variables for sensitive data
- **Secured:** Token-based authentication for registries
- **Secured:** Secure artifact handling and distribution
- **Secured:** Access control for protected operations

## 📚 Documentation & Examples

### Updated Documentation
- **NEW:** Docker Hub integration guide
- **NEW:** Multi-registry deployment examples
- **NEW:** CI/CD pipeline documentation
- **UPDATED:** Docker Compose examples with monitoring

### Configuration Examples
- **NEW:** Production-ready Docker Compose setup
- **NEW:** GitLab CI/CD variable configuration
- **NEW:** Multi-environment deployment patterns
- **UPDATED:** Container orchestration examples

## 🌐 Community & Ecosystem

### Accessibility Improvements
- **Public:** Docker Hub repository for easy access
- **Public:** GitHub releases with comprehensive artifacts
- **Public:** Multi-platform binary distribution
- **Public:** Community-friendly documentation

### Integration Support
- **Enhanced:** Kubernetes deployment examples
- **Enhanced:** Docker Swarm compatibility
- **Enhanced:** Cloud platform integration guides
- **Enhanced:** Monitoring and observability setup

## 🔄 Migration Guide

### From Previous Versions
No breaking changes in this release. All existing configurations remain compatible.

### Docker Image Updates
If you're using custom Docker configurations, update your image references:

```yaml
# Old (still works)
image: ghcr.io/kabiroman/ttlsemlock:latest

# New (recommended)
image: kabiromandocker/ttlsemlock:latest
```

## 🚨 Known Issues

- **Minor:** DNS timeout issues in some network configurations (temporary, resolved by retry)
- **Minor:** Docker Hub rate limiting may affect frequent pulls (use authentication)

## 🎯 Why v0.7.6 Matters

**For End Users:** The enterprise-grade features from v0.7.5 (advanced retry logic, graceful release framework) are now **one Docker command away**. No complex setup, no dependency management - just pull and run.

**For DevOps Teams:** Production-ready deployment with built-in monitoring, memory protection, and automated retry logic. Everything you need for reliable distributed semaphores in production.

**For Developers:** Rich debugging capabilities with separate debug images, comprehensive metrics, and clear error handling make integration seamless.

## 🎉 Acknowledgments

This release represents the culmination of months of enterprise-grade feature development (v0.7.1-v0.7.5) now made accessible to the broader community. Special thanks to the feedback that drove both the advanced features and the infrastructure improvements.

## 📞 Support & Feedback

- **🐛 GitHub Issues:** [Report bugs and feature requests](https://github.com/kabiroman/TtlSemLock/issues)
- **🐳 Docker Hub:** [Official images and documentation](https://hub.docker.com/r/kabiromandocker/ttlsemlock)
- **📚 Documentation:** [Complete guides and examples](https://github.com/kabiroman/TtlSemLock/tree/main/docs)
- **📊 Metrics:** Built-in Prometheus endpoint at `:9765/metrics`

---

## 🔮 What's Next

**v0.7.7 (Next):** Documentation cleanup and structure improvements for better developer experience  
**v0.8.0 (Major):** Persistence layer and Raft consensus for true distributed semaphores

## 📥 Get Started Today

**🚀 Quick Start:** `docker run -p 8765:8765 -p 9765:9765 kabiromandocker/ttlsemlock:latest`  
**📦 Download:** [GitHub Releases](https://github.com/kabiroman/TtlSemLock/releases/tag/v0.7.6)  
**📏 Size:** ~8.5MB (production image) | ~45MB (debug image with tools) 
