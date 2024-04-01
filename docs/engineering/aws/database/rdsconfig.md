# RDS Master-Slave Navigator

## 1. Introduction

### Objective
This documentation provides an overview of the configuration and management of our databases in RDS, with a master-slave architecture.

### Scope
Covers the configurations and management procedures of the master and slave databases.

## 2. General Description

### Architecture
Details the master-slave structure of the databases, where the master database handles I/O operations and the slave database is configured for read-only access.

## 3. Configuration Details

### Master Configuration
- `max_connections = 1000`
- `shared_buffers = 2048000`
- `effective_cache_size = 2147483647`
- `maintenance_work_mem = 512000`
- `checkpoint_completion_target = 0.9`
- `wal_buffers = 16000`
- `default_statistics_target = 100`
- `random_page_cost = 1.1`
- `effective_io_concurrency = 50`
- `work_mem = 64000`
- `min_wal_size = 1024`
- `max_wal_size = 4000`

### Replica Configuration
- `max_connections = 1000`
- `shared_buffers = 2048000`
- `effective_cache_size = 2147483647`
- `maintenance_work_mem = 512000`
- `checkpoint_completion_target = 0.9`
- `wal_buffers = 16000`
- `default_statistics_target = 100`
- `random_page_cost = 1.1`
- `effective_io_concurrency = 50`
- `work_mem = 64000`
- `min_wal_size = 1024`
- `max_wal_size = 4000`

---

