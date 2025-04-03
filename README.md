# Camunda Engine Orchestrator

Welcome to the **Camunda Engine Orchestrator**, a lightweight, distributed, and autoscaling platform designed to simplify workflow management and migration between **Camunda 7** and **Camunda 8**. This engine introduces a new paradigm in distributed computing, leveraging **WebAssembly (WASM)** for high-performance, portable, and secure service execution.

---

## Key Features

### 1. **Seamless Workflow Migration**
- **Blue-Green Deployment**: Gradually migrate workflows from Camunda 7 to Camunda 8 with zero downtime.
- **Dynamic Routing**: Automatically route requests to the appropriate engine based on migration progress.
- **State Synchronization**: Synchronize process instances and variables between Camunda 7 and Camunda 8.

### 2. **High-Performance Job Workers**
- **Lightweight Execution**: The engine is only **20MB** and can handle **100k WASM services per host**.
- **Distributed and Autoscaling**: Automatically scale job workers across multiple hosts for fault tolerance and performance.
- **Cross-Environment Compatibility**: Run job workers on **browsers, mobile devices, servers, or microcontrollers**.

### 3. **Unified API Management**
- **Abstract Complexity**: Expose a unified REST API for both Camunda 7 and Camunda 8.
- **Dynamic Overrides**: Customize and override endpoints dynamically to adapt to your business needs.
- **API Gateway Features**: Built-in support for rate limiting, authentication, and CORS.

### 4. **Future-Proof with WebAssembly**
- **Portability**: WASM services can run anywhere, from the cloud to edge devices.
- **Security**: WASM’s sandboxing model ensures strong isolation and security.
- **Performance**: WASM’s lightweight nature ensures fast execution, even on resource-constrained devices.

---

## How It Works

### 1. Service Configuration
Define your services using `service.yaml`:
```yaml
service:
  name: "Camunda8Worker"
  description: "Worker service for interacting with Camunda 8 via gRPC API"
  version: "1.0.0"
  dependencies:
    - name: "grpc"
      version: "^1.0.0"
  grpc:
    host: "localhost"
    port: 26500
    proto-files:
      - "camunda8.proto"