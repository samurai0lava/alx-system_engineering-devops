[![web-infrastructure-task-2.png](https://i.postimg.cc/NMzWDN7q/web-infrastructure-task-2.png)](https://postimg.cc/VrXGLWVD)

# Secure and Monitored Three-Server Web Infrastructure Design

## Server 1 (Web Server):
- Nginx installed as the web server to serve static content and forward dynamic requests to the application server.
- Hosts the application files (code base).

## Server 2 (Application Server):
- Application server hosts the dynamic part of the website, processing user requests, accessing the database, and generating dynamic content.
- Communicates with the web server and database server.

## Server 3 (Database):
- A MySQL database operates as a primary-replica (master-slave) cluster for data redundancy.
- Both primary and replica nodes can accept read requests.

## Load Balancer (HAProxy):
- HAProxy is configured to distribute traffic across application servers, enhancing performance and fault tolerance.

## Firewalls:
- Three firewalls are added to enhance security by controlling incoming and outgoing traffic at different layers of the infrastructure.

## SSL Certificate (HTTPS):
- An SSL certificate is implemented to enable secure communication over HTTPS, encrypting data between the user's browser and the server.

## Monitoring Clients (Data Collectors):
- Three monitoring clients are integrated to collect data for monitoring services like Sumo Logic.
- These clients gather performance metrics, logs, and other data for analysis and proactive issue identification.

## Terminating SSL at Load Balancer Level:
- Terminating SSL at the load balancer level can be an issue because while data is encrypted between the user and the load balancer, it's decrypted before being forwarded to the application servers. This creates a security vulnerability if the internal network isn't well-secured.

## Single MySQL Server for Writes:
- Having only one MySQL server capable of accepting writes is problematic as it becomes a single point of failure. If the server fails, write operations become unavailable.

## Servers with Identical Components:
- Servers with identical components (database, web server, and application server) might be problematic as they create uniform dependencies. If one component fails, it could affect all servers at once, leading to widespread service disruption.

## Why Serve Traffic Over HTTPS:
- Serving traffic over HTTPS ensures data privacy and integrity by encrypting communication between the user's browser and the server. It protects sensitive information from eavesdropping and tampering.

## What Monitoring Is Used For:
- Monitoring is used to track the health, performance, and availability of the infrastructure. It helps in identifying issues proactively, optimizing resource utilization, and ensuring a seamless user experience.

## How Monitoring Tool Collects Data:
- Monitoring tools collect data through monitoring clients or agents installed on each server. These clients gather performance metrics, logs, and other relevant data, which is then sent to the monitoring service for analysis and visualization.

## Monitoring Web Server QPS:
- To monitor web server queries per second (QPS), you would set up appropriate metrics collection and alerts. This involves configuring the monitoring tool to track request rates and set thresholds for notification when QPS surpasses acceptable levels.

By addressing these issues and implementing the additional elements like firewalls, SSL certificates, and monitoring clients, the infrastructure can become more secure, resilient, and easier to manage.

