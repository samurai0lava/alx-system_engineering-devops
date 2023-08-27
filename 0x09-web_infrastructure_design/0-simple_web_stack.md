[![web-infrastructure-task-1.png](https://i.postimg.cc/brLqq01m/web-infrastructure-task-1.png)](https://postimg.cc/xNkwRzxm)


# Simple Web Infrastructure

## User Accessing the Website
A user types "www.foobar.com" in their web browser and hits Enter.

## Domain Name (DNS)
The domain name "foobar.com" is a human-readable address that is used to identify the website. The "www" is a subdomain and acts as a hostname prefix. The DNS system translates this domain name into an IP address, which is essential for routing traffic to the correct server.

## DNS Record
The DNS record for the www subdomain of foobar.com should be a type A record. This record associates the domain name with an IP address, in this case, pointing to the server's IP address, 8.8.8.8.

## Server
A server is a computer system that responds to requests made by other computers, known as clients. In this case, the server with IP address 8.8.8.8 is responsible for handling incoming requests for the website.

## Web Server (Nginx)
The web server (Nginx) is responsible for serving static content, handling incoming HTTP requests, and forwarding dynamic requests to the application server. It listens for incoming requests on port 80 (HTTP) and 443 (HTTPS), and then routes those requests appropriately.

## Application Server
The application server hosts the application codebase and processes dynamic content requests. It communicates with the web server to handle these requests, perform necessary computations, access databases, and generate dynamic content. This separation of concerns helps in scaling and maintaining the application more effectively.

## Application Files (Code Base)
The application files contain the code that makes up the website. This includes HTML, CSS, JavaScript, and any server-side code (e.g., Python, PHP) that generates dynamic content.

## Database (MySQL)
The database (MySQL) stores structured data for the website. This can include user accounts, content, settings, and more. The application server interacts with the database to read and write data as required by the application.

## Communication with User's Computer
When the user's computer sends a request to access the website, it makes an HTTP request to the server's IP address (8.8.8.8). The request is processed by the web server, which might then forward dynamic requests to the application server. The application server interacts with the database if necessary and generates a response. This response travels back through the same path to reach the user's computer and is displayed in their browser.

## Issues with this Infrastructure
1. **Single Point of Failure (SPOF):** Since there is only one server, if it fails for any reason, the entire website becomes inaccessible. This creates a single point of failure and poses a significant risk to the availability of the website.

2. **Downtime During Maintenance:** When maintenance is needed (e.g., deploying new code), the web server often needs to be restarted. This can lead to downtime where the website is inaccessible to users.

3. **Limited Scalability:** With only one server, it's challenging to handle a large influx of incoming traffic. As the website gains popularity, it might become slow or crash under the load.

