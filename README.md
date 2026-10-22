# PocketHost Mobile PaaS (pockethost-mobile-paas)

1-Click Mobile PaaS & Instant Domain Hosting Engine for Android

PocketHost Mobile PaaS turns any Android device into a fully operational, zero-config web hosting platform and auto-detecting application orchestrator.

## System Architecture & Components

### 1. Native Android Wrapper (`android-app/`)
* Environment & Runtime: Android wrapper managing background service lifecycle, Termux environment, battery optimizations, and network listener bindings.
* Service Lifecycle: Keeps node background processes persistent across reboots and network switches.

### 2. Zero-Config Orchestrator & Auto-Detector (`engine/src/`)
* `server.js`: Central API gateway, HTTP/HTTPS request routing, dynamic host matching, and health check dashboard endpoints.
* `supervisor.js`: Process monitor that watches spawned app instances, automatically restarting failed processes and managing CPU/memory allocations on mobile hardware.
* `detector.js`: Auto-detects local project runtime requirements (Node.js, Python, Static HTML, Go, etc.) upon upload or deployment.
* `tunnel_manager.js`: Manages secure tunnels to assign instant public domain names to locally hosted applications without requiring static public IPs or manual port forwarding.

### 3. 1-Command Phone Bootstrap (`scripts/install-on-phone.sh`)
* Single-line bash setup script for Android/Termux environments.
* Automatically installs Node.js, Git, dependencies, configures permissions, and registers the system service daemon.

### 4. 13-Step Automated Smoke Test Suite (`smoke_test.js`)
Comprehensive validation suite covering:
1. Environment & runtime check
2. Dependency verification
3. Config initialization
4. Daemon startup
5. Auto-detector file discovery
6. App provisioning & port binding
7. Process supervision & lifecycle restart
8. Dynamic route creation
9. Domain tunnel creation & public ping
10. Health check endpoint status
11. High-load stress & memory threshold response
12. Graceful app shutdown
13. Clean teardown & log audit

## Quick Start

`bash scripts/install-on-phone.sh`
