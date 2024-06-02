stributed Web Infrastructure Design

## Components:
1. **2 Servers**
2. **1 Web Server (Nginx)**
3. **1 Application Server**
4. **1 Load Balancer (HAproxy)**
5. **1 Set of Application Files (your code base)**
6. **1 Database (MySQL)**

## Overview:
This design hosts a website reachable via `www.foobar.com` using a distributed web infrastructure.

![Distributed Web Infrastructure](./distributed_web_infrastructure.png)

## Additional Elements and Their Roles:
1. **Load Balancer (HAproxy)**:
   - Distributes incoming traffic across multiple servers.
   - Helps in handling more traffic and provides high availability.

2. **Distribution Algorithm**:
   - The load balancer is configured with a round-robin algorithm.
   - This algorithm distributes client requests evenly across the servers in the pool.

3. **Active-Active vs. Active-Passive Setup**:
   - Our setup enables an **Active-Active** configuration.
   - **Active-Active**: Both servers handle traffic simultaneously.
   - **Active-Passive**: One server handles traffic while the other is on standby.

4. **Database Primary-Replica (Master-Slave) Cluster**:
   - **Primary Node**: Handles write operations and replicates data to the replica node.
   - **Replica Node**: Handles read operations and provides redundancy.

## Issues with the Infrastructure:
1. **Single Points of Failure (SPOF)**:
   - Load Balancer can be a SPOF if not properly managed.

2. **Security Issues**:
   - Lack of firewall.
   - No HTTPS for secure communication.

3. **No Monitoring**:
   - Absence of monitoring tools to track system performance and detect failures.

## Recommendations:
- Implement multiple load balancers for redundancy.
- Use firewalls and enable HTTPS for better security.
- Integrate monitoring tools like Prometheus and Grafana for real-time monitoring.

