# Centralized vs Distributed vs Decentralized system

## Centralized system

### Definition of centralized system

System that use client/server architecture, where one or more clients node are
connected to a central server.

### Advantages of centralized system

- Easy to physically secure;
- Quick updates (only one server to update);
- Easy to manage: owner has just to manage one server, no need to manage
clients;
- Full control of the system by the owner.

### Disadvantages of centralized system

- Single point of failure: if the server is down, the system is down;
- Centralized control (disadvantage for users);
- Difficult server maintenance (only hot updates are possible, may break the
system);
- Less possibility of data backup (redundancy must be applied);
- Difficult to scale (server must be upgraded to handle more clients);
- DDOS attack (server can be overloaded by malicious users).

### Applications of centralized system

- Application development (especially for web applications);
- Data analysis: easier analysis when data is centralized;
- Data storage;
- Personal computing.

## Distributed system

### Definition of distributed system

System that uses peer-to-peer architecture, where nodes interact with each
other to achieve a common goal.

### Advantages of distributed system

- Low latency: because of high geographical nodes distribution, time to get a
response is low;
- High scalability: nodes can be added to the system to handle more clients or
more computing power.

### Disadvantages of distributed system

- Still under the control of the owner.

### Applications of distributed system

- Cluster computing: computers are coupled together to work as a single system,
to achieve a common goal;
- Grid computing: All the resources are pooled together in order to turn the
system into a single supercomputer;
- Cloud computing.

## Decentralized system

### Definition of decentralized system

System that uses peer-to-peer architecture, where each node operates on its own
on local data to accomplish global goals.

### Advantages of decentralized system

- Minimal bottleneck: the entire load is balanced across all nodes;
- No single point of failure (high availability): if one node is down, the
system is still up;
- No central authority / Trustless: no one can control the system;
- Easy to scale: nodes can be added so it increases the performance of the
entire system and lead to a more decentralized system;
- Redundancy: data is always replicated on all nodes.

### Disadvantages of decentralized system

- Hard to sync: a consensus algorithm must be used to sync all nodes;
- No central authority: since nodes themselves are in charge of the security,
if 51% of the nodes are malicious, the system is compromised;
- Complexity: difficult to understand, deploy, maintain & debug.

### Applications of decentralized system

- Blockchain;
- Data storage;
- Data base.

## Comparison

|| Centralized | Distributed | Decentralized |
|---|---|---|---|
| *Network/hardware resources* | Maintained & controlled by single entity in a centralized location | Spread across multiple data centers & geographies; owned by network provider | Resources are owned & shared by network members; difficult to maintain since no one owns it |
| *Solution components* | Maintained & controlled by central entity | Maintained & controlled by solution provider | Each member has exact copy of distributed ledger |
| *Data* | Maintained & controlled by central entity | Typically owned & managed by customer | Only added through group consensus |
| *Control* | Controlled by central entity | Typically, a shared responsibility between network provider, solution provider & customer | No one owns the data & everyone owns the data |
| *Single point of failure* | Yes | No | No |
| *Fault tolerance* | Low | High | Extremely high |
| *Security* | Maintained & controlled by central entity | Typically, a shared responsibility between network provider, solution provider & customer | Increases as number of nodes increases |
| *Performance* | Maintained & controlled by central entity | Increases as network/hardware resources scale up and out | Decreases as number of nodes increases |
| *Example* | ERP system | Cloud computing | Blockchain |
