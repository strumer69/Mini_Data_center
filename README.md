# Mini_Data_center
create a mini dataCenter on our labtop

## instal  Vagrant
- brew install vagrant
- Vagrant is a source-available software product for building and maintaining portable virtual software development environments; e.g., for VirtualBox, KVM, Hyper-V, Docker containers, VMware, Parallels, and AWS

# Create a project directory
mkdir -p ~/mini-datacenter && cd ~/mini-datacenter

# Step 1: Spin Up 3 Virtual Machines
- We will create a Vagrantfile defining three nodes:

- node1 — NFS Storage Server

- node2 — Docker App Node

- node3 — Slurm Worker / Monitoring Node (with node1 as Slurm Master)

# Mini Data Center on macOS (Apple Silicon)

A local, multi-node Linux infrastructure environment running on macOS using Vagrant and QEMU. This project simulates enterprise hybrid-cloud and High-Performance Computing (HPC) workflows by orchestrating separate storage, container compute, and workload management nodes on a private virtual network.

---

## Architecture Overview

| Node Name | IP Address | Role | Specs | Key Technologies |
| :--- | :--- | :--- | :--- | :--- |
| **node1** | `192.168.56.11` | Storage & Slurm Controller | 1 vCPU, 1 GB RAM | NFS Server, `slurmctld` |
| **node2** | `192.168.56.12` | Container Compute Host | 2 vCPU, 2 GB RAM | Docker Engine, NFS Client |
| **node3** | `192.168.56.13` | Slurm Execution Worker | 1 vCPU, 1 GB RAM | `slurmd`, Munge Auth |

---

## Value & Learning Outcomes

By building and operating this mini data center, you gain hands-on experience in:
* **Infrastructure as Code (IaC):** Virtual machine orchestration on Apple Silicon using Vagrant and QEMU.
* **Network Infrastructure:** Private subnet routing, static IP assignment, custom SSH port forwarding, and host name resolution.
* **Network Storage (NAS):** Provisioning, exporting, and mounting Network File System (NFS) shares.
* **Containerization:** Running isolated microservices and applications via Docker.
* **HPC Workload Management:** Configuring Slurm clusters, job schedulers, and node communications.
* **Resource Monitoring:** Tracking system resource utilization across distributed nodes.

---

## Prerequisites

* **OS:** macOS running on Apple Silicon (M1/M2/M3/M4)
* **Homebrew Packages:** `brew install vagrant qemu`
* **Vagrant Plugin:** `vagrant plugin install vagrant-qemu`

---

## Quick Start Guide

### 1. Provision the Infrastructure

Clone or open the project folder in your terminal and run:

```bash
# Spin up all three virtual machines sequentially
vagrant up --provider=qemu --no-parallel
