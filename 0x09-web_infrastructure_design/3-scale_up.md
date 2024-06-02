# Scale Up Infrastructure Design

## Components:
1. **1 Additional Server**
2. **1 Load Balancer (HAProxy) configured as a cluster**
3. **Separate Servers for Web Server (Nginx), Application Server, and Database Server (MySQL)**

## Overview:
This design scales up the infrastructure for the website reachable via `www.foobar.com` by adding redundancy and distributing roles across multiple servers.

![Scale Up Infrastructure](./scale_up.png)

## Additional Elements and Their Roles:
1. **Additional Server**:
   - Provides redundancy and helps in balancing the load across the infrastructure.

2. **Load Balancer Cluster (HAProxy)**:
   - Distributes incoming traffic across multiple servers, ensuring high availability and reliability.
   - Configured with a distribution algorithm such as round-robin to evenly distribute traffic.

3. **Separate Servers for Each Component**:
   - **Web Server (Nginx)**: Handles HTTP requests and serves static content.
   - **Application Server**: Processes dynamic content and business logic.
   - **Database Server (MySQL)**: Manages data storage, retrieval, and transactions.

## Explanation:
- **Load Balancer Configuration**:
  - **Distribution Algorithm**: Round-robin, least connections, or IP hash to distribute traffic efficiently.
  - **Active-Active Setup**: Both load balancers actively distribute traffic.
  - **Active-Passive Setup**: One load balancer is active while the other is on standby, ready to take over if the active one fails.

- **Primary-Replica (Master-Slave) Database Cluster**:
  - **Primary Node**: Handles write operations and propagates changes to the replica nodes.
  - **Replica Node**: Handles read operations and ensures data redundancy.

## Issues with This Infrastructure:
1. **SPOF**: Redundancy in load balancers and database setup reduces single points of failure.
2. **Security Issues**: Ensure firewalls and HTTPS are configured correctly.
3. **Monitoring**: Set up monitoring for all servers to track performance and detect issues.

## Recommendations:
- Implement firewall rules to secure each server.
- Use SSL termination at the load balancer and re-encrypt traffic to the web servers.
- Monitor web server QPS and database performance.


