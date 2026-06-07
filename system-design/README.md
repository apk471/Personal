# System Design Study Notes for Backend Developers

These notes cover the fundamental system design topics studied from the point of view of a backend developer. The goal is to understand the building blocks of distributed systems well enough to design, discuss, and critique backend architectures.

---

## What System Design Means for Backend Work

System design is the practice of architecting software systems that are scalable, reliable, maintainable, and cost-effective.

For a backend developer, the practical meaning is:

- Your service should handle expected traffic without collapsing.
- Your data should not be lost when things fail.
- Your architecture should be explainable to teammates.
- Your dependencies (DB, cache, queue) should be chosen deliberately.
- Your capacity decisions should be backed by rough calculations.
- Your messaging patterns should match your consistency and durability needs.

---

## Folder Structure

| Folder | Contents |
| --- | --- |
| `basics/` | Stateless vs stateful, message queues, pub/sub, HLD building blocks, workers |
| `capacity/` | Backend capacity estimation: QPS, bandwidth, storage, cache, DB sizing |
| `interview-framework/` | 4-step framework for system design interviews, time division, common questions |

---

## Mental Model

### Stateless vs Stateful

Stateless services scale horizontally easily. Stateful services hold data in memory or local disk and need careful scaling strategies.

### Message Queues

Queues decouple producers from consumers. They handle spikes, provide durability, and enable async processing.

### Pub/Sub

Pub/Sub is a messaging pattern where publishers send to topics and subscribers receive copies. Useful for broadcasting events.

### HLD Building Blocks

Every high-level design includes: DNS resolution, CDN for static assets, load balancer to distribute traffic, application servers, and databases.

### Workers

Workers are consumer processes that pull from queues and process tasks. They handle retries, dead-letter queues, and backpressure.

### Capacity Planning

Estimating QPS, storage, bandwidth, and number of servers helps you size the system before building it.

---

## Study Order

Recommended order for backend devs:

1. Understand stateless vs stateful.
2. Learn message queue concepts and compare popular queue systems.
3. Learn pub/sub pattern and its relationship to queues.
4. Sketch a high-level architecture with standard building blocks.
5. Learn the worker pattern for async processing.
6. Practice capacity estimation calculations.
7. Learn the interview framework and practice with common questions.

