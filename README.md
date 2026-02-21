# AI Cluster Failure Modes
### Diagnostics for high-performance AI infrastructure.

> **Architecture Principle:** GPUs rarely fail. The storage and network feeding them fail constantly.

## 📚 Canonical Architecture Reference  
This repository contains the diagnostic frameworks for maintaining $100k+ cluster uptime.

**The continuously maintained architectural specification lives here:** 👉 [https://www.rack2cloud.com/ai-infrastructure-strategy-guide/](https://www.rack2cloud.com/ai-infrastructure-strategy-guide/)

---

## The 3 Critical Bottlenecks
When training stalls or inference latency spikes, the root cause is almost always outside the compute nodes.

| Failure Mode | Symptom | Architectural Fix |
| :--- | :--- | :--- |
| **Checkpoint Stalls** | GPUs drop to 0% utilization every hour. | Implement parallel file systems (e.g., WEKA, Lustre) instead of standard NFS. |
| **Network Jitter** | Multi-node training efficiency drops below 60%. | Dedicated non-blocking RoCEv2 or InfiniBand fabrics. |
| **API Rate Limiting** | Zombie API keys draining LLM token quotas. | Deploy an AI-specific API Gateway (Control Plane) for token-level throttling. |

---
**Star this repo for AI operational frameworks.** *Maintained by [Rack2Cloud](https://www.rack2cloud.com)*
