# Replication
MongoDB replication project implementing a five-node PSA replica set, automated failover, oplog configuration, read/write concerns, and geographically local read operations.

# MongoDB Replication

This project explores MongoDB replication and replica set configuration using a five-node PSA architecture. The project demonstrates how MongoDB can provide data redundancy, automatic failover, and different read/write consistency configurations.

## Project Overview

### 1. Replica Set Configuration

A five-node MongoDB replica set was manually created using a PSA architecture consisting of:

- 1 Primary node
- 3 Secondary nodes
- 1 Arbiter

Each node was configured on a separate port and the replica set was initialized using `rs.initiate()`. The configuration was verified using `rs.status()`, and the employee burnout dataset was imported into the primary node and replicated across the secondary nodes. 

### 2. Failover & Oplog

The project examined MongoDB's automatic failover process, including how secondary nodes detect primary failure and participate in an election to select a new primary.

The role of the arbiter was also explored, along with MongoDB's Oplog, which records write operations from the primary and allows secondary nodes to replicate those changes. The Oplog configuration was increased to 25GB. 

### 3. Read & Write Concerns

The replica set was configured to control the consistency of database operations.

A write concern of `w:2` was configured so that writes are acknowledged after being written to the primary and at least one secondary node. The read concern was configured to `majority` to ensure reads return data that has been replicated to the majority of nodes. 

### 4. Geographically Local Reads

MongoDB's `readPreference: "nearest"` was explored to support geographically local reads. This allows MongoDB to select a suitable node based on network latency, potentially reducing response times for users located closer to a secondary node. 

### 5. Replica Set Removal

The final task covered how to safely shut down the MongoDB instances making up the replica set and remove the associated configuration and data directories if required. :

## Key Technologies & Concepts

- MongoDB
- MongoDB Replica Sets
- PSA Architecture
- Primary & Secondary Nodes
- Arbiter Nodes
- Automatic Failover
- Elections
- Oplog
- Write Concern
- Read Concern
- Read Preference
- Data Replication
- Distributed Databases
- Fault Tolerance
