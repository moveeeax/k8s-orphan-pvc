# k8s-orphan-pvc

> The volumes nobody mounts are still on the invoice.

**Status:** 🚧 In development

## Overview

Find PersistentVolumeClaims that no running pod mounts, with size, storage class and an estimated monthly cost, so abandoned volumes stop billing quietly.

## Features

- Lists PVCs that no running pod mounts, across all namespaces or a chosen subset
- Separates claims that were never mounted from ones released when a workload was deleted
- Shows capacity, storage class, access modes, phase and age for each claim
- Estimated monthly cost from a per-GiB price table, overridable per storage class
- Skips claims still owned by a live StatefulSet volumeClaimTemplate, so scaled-down replicas are not false positives
- Table, CSV and JSON output plus a `--min-age` filter, for a scheduled cost report

## Stack

Go + client-go and cobra, with tablewriter for the terminal output.

## Usage

```bash
k8s-orphan-pvc --all-namespaces --min-age 30d --price-per-gib 0.05 --output table
```

## License

MIT
