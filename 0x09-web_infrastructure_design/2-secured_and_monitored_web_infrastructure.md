# Secured and Monitored Web Infrastructure Design

## Components:
1. **3 Firewalls**
2. **1 SSL Certificate (HTTPS)**
3. **3 Monitoring Clients (Data collectors for Sumologic or other services)**
4. **1 Load Balancer (HAProxy)**
5. **1 Web Server (Nginx)**
6. **1 Application Server**
7. **1 Database (MySQL)**

## Overview:
This design hosts a website reachable via `www.foobar.com` using a secured and monitored web infrastructure.

![Secured and Monitored Web Infrastructure](./secured_and_monitored_web_infrastructure.png)

## Additional Elements and Their Roles:
1. **Firewalls**:
   - Protect each server by controlling incoming and outgoing traffic based on security rules.

2. **SSL Certificate**:
   - Ensures that traffic between the user and the web server is encrypted and secure via HTTPS.

3. **Monitoring Clients**:
   - Collect data for monitoring tools like Sumologic, helping to track performance and detect issues.

## Explanation:
- **Firewalls**: Used to protect servers from unauthorized access and potential attacks.
- **HTTPS**: Encrypts data in transit, providing security for users’ data and improving trust.
- **Monitoring**: Helps in tracking system performance, identifying issues, and maintaining uptime.
- **Data Collection**: Monitoring clients gather metrics, logs, and performance data to send to a centralized monitoring service.
- **QPS Monitoring**: To monitor queries per second (QPS) on your web server, configure the monitoring tool to track incoming requests and analyze the data.

## Issues with This Infrastructure:
1. **SSL Termination at Load Balancer**:
   - Can expose internal traffic to potential security risks if not re-encrypted before reaching web servers.

2. **Single MySQL Server for Writes**:
   - Creates a single point of failure and potential performance bottleneck.

3. **Homogeneous Servers**:
   - Running all components on each server can lead to resource contention and complicate scaling.

## Recommendations:
- Implement redundant load balancers for high availability.
- Use a firewall management solution to simplify rule management.
- Re-encrypt traffic between the load balancer and web servers for added security.
- Set up a MySQL replication cluster to distribute write operations.


