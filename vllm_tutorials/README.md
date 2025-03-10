# vLLM Optimization Tutorials

This directory contains a series of tutorials on setting up and optimizing vLLM for LLM inference. The tutorials use the Mistral-7B-Instruct-v0.3 model as an example.

## Tutorial Overview

```
┌─────────────────────────────────────────────────────────────┐
│                 vLLM Tutorial Series                        │
│                                                             │
│  ┌─────────────────────┐      ┌─────────────────────────┐   │
│  │ 00: Environment     │      │ 01: Basic vLLM          │   │
│  │    Setup            │─────►│    Deployment           │   │
│  │                     │      │                         │   │
│  └─────────────────────┘      └───────────┬─────────────┘   │
│                                           │                 │
│                                           ▼                 │
│  ┌─────────────────────┐      ┌─────────────────────────┐   │
│  │ 03: Remote Shared   │◄─────┤ 02: KV Cache            │   │
│  │    KV Cache         │      │    Offloading           │   │
│  │                     │      │                         │   │
│  └─────────────┬───────┘      └─────────────────────────┘   │
│                │                                            │
│                └──────────────────┐                         │
│                                   ▼                         │
│                ┌─────────────────────────────────────┐      │
│                │ 04: Performance Benchmarking        │      │
│                │                                     │      │
│                └─────────────────────────────────────┘      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Notebooks in this Series

1. **00_mistral_setup.ipynb**: Setting up the environment with Mistral-7B-Instruct-v0.3
   - Comprehensive setup guide with diagrams
   - Kubernetes and MicroK8s configuration
   - Brev CLI port forwarding instructions

2. **01_setup_vllm_production_stack.ipynb**: Basic vLLM deployment
   - Setting up a Kubernetes environment
   - Installing vLLM using Helm
   - Testing the deployment

3. **02_kv_cache_offloading.ipynb**: KV cache offloading to CPU
   - Understanding KV cache and its importance
   - Configuring CPU offloading
   - Performance benefits and trade-offs

4. **03_remote_shared_kv_cache.ipynb**: Remote shared KV cache
   - Setting up shared KV cache across multiple instances
   - Fault tolerance and horizontal scaling
   - Advanced configuration options

5. **04_performance_benchmarking.ipynb**: Performance benchmarking
   - Comparing different optimization techniques
   - Measuring throughput, latency, and memory usage
   - Recommendations for different use cases

## Hardware Requirements

For optimal performance with these tutorials, we recommend:

- **GPU**: NVIDIA A10G or better (24GB+ VRAM)
- **CPU**: 8+ cores (16+ for KV cache offloading)
- **RAM**: 32GB+ (64GB+ recommended for KV cache offloading)
- **Storage**: 100GB+ SSD

## Getting Started

Start with the `00_mistral_setup.ipynb` notebook to set up your environment, then proceed through the tutorials in order.

## Port Forwarding with Brev CLI

To access the vLLM API from your local machine when running on Brev.dev, use:

```bash
brev port-forward your-workspace-name --port 53936:53936
```

Or interactively:

```bash
brev port-forward your-workspace-name
# Then enter 53936 for both remote and local ports when prompted
```