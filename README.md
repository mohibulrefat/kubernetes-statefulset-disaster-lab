# Kubernetes StatefulSet Disaster Lab

A hands-on Kubernetes learning project focused on running a stateful PostgreSQL service and recovering it from different failure scenarios.

## Goal

Build a miniature production-style PostgreSQL platform using Kubernetes and learn how different Kubernetes resources contribute to application reliability, persistence, and disaster recovery.

The main objective is to understand the difference between:

* Pod durability
* Workload durability
* Storage durability
* Backup and recovery

## Target Architecture

```text
                ┌─────────────┐
                │   Frontend  │
                └──────┬──────┘
                       │
                       ▼
                ┌─────────────┐
                │   Backend   │
                └──────┬──────┘
                       │
                       ▼
              ┌─────────────────┐
              │   PostgreSQL    │
              │   StatefulSet   │
              └────────┬────────┘
                       │
                       ▼
                     PVC
                       │
                       ▼
               Persistent Storage
```

## Kubernetes Components

The lab will use:

* PostgreSQL
* StatefulSet
* Headless Service
* PersistentVolumeClaim (PVC)
* StorageClass
* Secret
* Health Probes
* Resource Limits
* PodDisruptionBudget
* Backup Job
* Backup CronJob
* Restore Job

## Disaster Scenarios

The system will intentionally be exposed to several failure scenarios:

1. Delete the PostgreSQL Pod
2. Delete the PostgreSQL Service
3. Delete the Backend Pod
4. Restart the Kubernetes Node
5. Simulate database unavailability
6. Fill the database close to storage capacity
7. Deploy an incompatible schema migration
8. Destroy the original PostgreSQL workload and restore from backup

## Final Challenge

Recover the application after destroying the original PostgreSQL workload while preserving the database data through the appropriate recovery mechanism.

## Learning Objectives

By completing this lab, You should understand:

* How StatefulSets manage stateful workloads
* Why Pods are considered disposable
* How StatefulSets provide stable Pod identity
* How PVCs provide persistent storage
* How StorageClasses provision storage
* How Services provide stable networking
* How Headless Services work with StatefulSets
* How Kubernetes Secrets provide configuration to Pods
* The difference between startup, readiness, and liveness probes
* How resource requests and limits affect workloads
* What PodDisruptionBudgets protect against
* How Jobs and CronJobs work
* How PostgreSQL backups and restores work
* The difference between persistence and disaster recovery
* How to recover an application after a database failure

## Project Structure

```text
.
├── README.md
├── docs/
│   ├── architecture.md
│   ├── concepts.md
│   ├── disaster-scenarios.md
│   └── recovery.md
├── manifests/
│   ├── namespace/
│   ├── storage/
│   ├── secrets/
│   ├── postgres/
│   ├── backend/
│   ├── backup/
│   └── restore/
├── disaster-scenarios/
└── scripts/
```

The detailed structure will evolve as the lab is implemented.

## Status

**Phase 0 - Not Started**

This project is being built incrementally as a hands-on Kubernetes learning exercise.

## Disclaimer

This is a learning environment, not a production database platform.

The purpose is to understand Kubernetes stateful workloads, failure behavior, persistence, backup, and disaster recovery.
