**Deror** — The Cluster-Orchestrating Sidecar for Exo  

![License](https://img.shields.io/badge/license-MIT-blue.svg)  
![Rust](https://img.shields.io/badge/language-Rust-orange.svg)  
![Python](https://img.shields.io/badge/bindings-Python-green.svg)

---

## Overview

**Deror** is a **lightweight, high-performance sidecar** library designed to work alongside [Exo](https://github.com/exo-explore/exo). Its primary goal is to **maintain, monitor, and orchestrate clusters** managed by Exo, providing reliability, automation, and observability in distributed environments.

Written in **Rust** for performance and safety, Deror exposes **Python bindings** for seamless integration in modern Python-based workflows, enabling engineers to manage clusters programmatically with minimal overhead.


---

## Key Features

- **Cluster Maintenance** – Automatically monitors cluster health, performs routine updates, and recovers failed nodes.  
- **Sidecar Architecture** – Runs alongside Exo without interfering with its core operations.  
- **Rust-Powered Performance** – Efficient memory usage and low-latency operations for large-scale deployments.  
- **Python Bindings** – Expose the full functionality through a Pythonic API for ease of use.  
- **Extensible** – Easily integrates with other tools and monitoring systems.  

---

## Installation

### Python installation

```bash
pip install deror
```


### Rust installation
```bash
cargo add deror
```

## Usage

### Python

```python
from deror import ClusterManager

# Initialize the sidecar for an existing Exo cluster
manager = ClusterManager(cluster_id="exo-cluster-01")

# Monitor cluster health
status = manager.health_check()
print(f"Cluster status: {status}")

# Perform automated maintenance
manager.perform_maintenance()
```

### Rust

```rust
use deror::ClusterManager;

fn main() {
    let manager = ClusterManager::new("exo-cluster-01");

    // Check cluster health
    let status = manager.health_check();
    println!("Cluster status: {:?}", status);

    // Perform routine maintenance
    manager.perform_maintenance();
}
```

## Architecture

+----------------+       +----------------+
|                |       |                |
|   Exo Node 1   | <---> |  Deror Sidecar |
|  (Worker + DB) |       |  (Health, Ops) |
+----------------+       +----------------+
        |
        v
+----------------+       +----------------+
|                |       |                |
|   Exo Node 2   | <---> |  Deror Sidecar |
|  (Worker + DB) |       |  (Health, Ops) |
+----------------+       +----------------+
        |
        v
+----------------+       +----------------+
|                |       |                |
|   Exo Node 3   | <---> |  Deror Sidecar |
|  (Worker + DB) |       |  (Health, Ops) |
+----------------+       +----------------+

Exo Nodes: Responsible for computation, scheduling, and cluster operations.

Deror Sidecars: Independently monitor each node, execute automated maintenance, ensure node health, and report metrics.

This design provides redundancy, fault tolerance, and real-time cluster observability.

## Contributing

We welcome contributions! Please follow these steps:

- Fork the repository.

- Create a new feature branch: git checkout -b feature/my-feature.

- Implement your changes and add tests.

- Submit a pull request with a clear description of your changes.

Guidelines:

- Follow the existing code style.

- Ensure tests cover new functionality.

- Provide clear documentation for new features.


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Roadmap

### Roadmap / Future Plans

- Advanced cluster analytics and metrics collection.

- Kubernetes-native integration for auto-scaling and resilience.

- Enhanced Python SDK with asynchronous support.

- CLI for monitoring and maintenance without embedding Python/Rust code.

- Dashboard UI for visualizing cluster health and operations.

- Plugin system for custom cluster policies and automated workflows.