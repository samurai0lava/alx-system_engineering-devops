[![web-infrastructure-task-2.png](https://i.postimg.cc/brLqq01m/web-infrastructure-task-2.png)](https://postimg.cc/xNkwRzxm)



# Three-Server Web Infrastructure Design

## Server 1 (Web Server):
- Nginx installed as the web server, serving static content and forwarding dynamic requests to the application server.
- Hosts the application files (code base).

## Server 2 (Application Server):
- Application server hosts the dynamic part of the website, processing user requests, accessing the database, and generating dynamic content.
- Communicates with the web server for routing requests and handling computations.

## Server 3 (Database):
- MySQL database used to store structured data, including user accounts, content, and settings.
- Operates as a primary-replica (master-slave) cluster for data redundancy.

## Load Balancer (HAProxy):
- HAProxy configured as the load balancer, distributing incoming traffic across the application servers for performance and fault tolerance.
- Implements a round-robin distribution algorithm for even load sharing.

## Domain Name (DNS):
- The domain name "foobar.com" is configured with a DNS record that points to the IP address of the load balancer.

## Load Balancer Setup:
- HAProxy configured with round-robin distribution, sending requests to available application servers in a cyclic manner.

## Active-Active vs. Active-Passive:
- Active-active load balancer setup, where both application servers handle traffic simultaneously for improved resource utilization and response times.

## Primary-Replica (Master-Slave) Database Cluster:
- MySQL database operates as a primary-replica cluster. Primary node handles writes and replicates data changes to replicas.
- Replicas are used for read operations, offloading the primary node and enhancing read scalability.

## Difference between Primary and Replica:
- Primary node handles write operations, updating the database with new or modified data.
- Replica nodes replicate data from the primary node and handle read operations, providing a read-only copy for better performance and scalability.

## Issues with this Infrastructure:
1. **Single Point of Failure (SPOF):** The load balancer can become a single point of failure. Load balancer failure affects traffic distribution and access to application servers.

2. **Security Issues:** Absence of a firewall exposes servers to security threats. No HTTPS implementation risks user data and sensitive information.

3. **No Monitoring:** Lack of monitoring system hinders proactive problem identification and resolution.

To address these issues, consider redundancy for the load balancer, implementing security measures like firewalls, HTTPS, and integrating monitoring and alerting systems.

