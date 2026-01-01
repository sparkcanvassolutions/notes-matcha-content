# Unit 5: Transactions & Concurrency Control

## Overview
Transactions ensure data consistency. Concurrency control allows multiple transactions to execute safely without conflicts.

## Learning Objectives
- Master ACID properties
- Learn transaction states
- Understand concurrency problems
- Master locking mechanisms
- Learn isolation levels

## Core Concepts

### ACID Properties

**Atomicity**: All-or-nothing. Either all operations succeed or none.

**Consistency**: Database moves from valid state to valid state.

**Isolation**: Concurrent transactions don't interfere.

**Durability**: After COMMIT, data persists permanently.

### Transaction States
- Active: Currently executing
- Partially Committed: Last statement executed
- Committed: Successfully completed
- Failed: Errors occurred
- Aborted: Rolled back

### Concurrency Problems

**Dirty Read**: Reading uncommitted data
**Lost Update**: Changes overwritten
**Unrepeatable Read**: Same data read twice gets different values
**Phantom Read**: Rows inserted/deleted affecting other transactions

### Locking Mechanisms

**Shared Lock**: Multiple readers, no writers
**Exclusive Lock**: Single writer, no other locks

### Isolation Levels (Lowest to Highest)
1. Read Uncommitted: Allows dirty reads
2. Read Committed: Prevents dirty reads
3. Repeatable Read: Prevents unrepeatable reads
4. Serializable: Prevents all anomalies

### Deadlock
Transactions wait for each other indefinitely.

**Prevention:**
- Lock ordering
- Timeout
- Deadlock detection

## Exam Notes
- ACID ensures reliability
- Dirty read most serious
- Serializable safest but slowest
- Deadlock detection critical

## Short Questions
1. Explain ACID with examples
2. Define dirty read
3. Difference between shared and exclusive locks
4. Isolation level hierarchy
5. What is deadlock?
6. When use ROLLBACK?
7. Explain phantom read
8. Consistency meaning
9. Bank transfer transaction design
10. Most common isolation level

## Key Takeaways
- Transactions guarantee data reliability
- ACID properties essential
- Concurrency control prevents conflicts
- Locking manages access
- Balance performance vs safety
