# Web infrastructure design

## Project Authors

Forster Asamany | Github: [fasamany1](https://github.com/fasamany1) 

Emmanuel Yeboah Manu | Github: [Stemmanuel95](https://github.com/stemmanuel95)

## Concepts
* For this project we looked at the following concepts;
- DNS (Domain name systems)
- Monitoring
- Web Sever
- Network Basics
- Load Balancer
- Server
- A brief review of databases
- The difference between a web server and app server
- DNS record types
- Single Point of failure
- How to avoid downtime when deploying new code
- High availability cluster (active-active/active-passive)
- What is HTTPS
- What is a firewall

# Eplanation on Project Tasks
# Task 0. Simple web stack
To design a one server web infrastructure that hosts the website reachable via www.foobar.com, let's start by understanding the user's request. When a user types in www.foobar.com into their web browser and hits enter, the request is sent to the DNS (Domain Name System) server to resolve the IP address associated with www.foobar.com. Once the IP address is resolved, the user's computer sends a request to the IP address to access the website.
## Specifics about this infrastructure
In our infrastructure, we will have one server that will host the web server (Nginx), application server, and the MySQL database. We will install the LAMP stack (Linux, Apache, MySQL, PHP) on the server.
The domain name foobar.com will be configured with a www record that points to our server's IP address 8.8.8.8. This will allow users to access the website using the URL www.foobar.com.
The web server (Nginx) will receive the user's request and serve static files such as HTML, CSS, and images. It will also route dynamic requests to the application server. The application server will handle dynamic requests and generate responses based on the user's request. It will communicate with the MySQL database to fetch and store data.
The MySQL database will store the website's data such as user information, blog posts, and other content.
The server will use HTTP (Hypertext Transfer Protocol) to communicate with the user's computer requesting the website. The web server and application server will generate HTTP responses that will be sent back to the user's computer.

## Issues about this infrastructure
However, this infrastructure has some issues. It is a single point of failure (SPOF), which means that if the server goes down, the website will not be accessible. There will be downtime when maintenance is needed, such as deploying new code, as the web server needs to be restarted. The infrastructure cannot scale if there is too much incoming traffic, as the single server will not be able to handle the load.

## How to address the issues
To address these issues, we can implement load balancing by adding more servers to the infrastructure. We can also implement a CDN (Content Delivery Network) to distribute content globally and reduce the load on the server. Additionally, we can use containerization technology like Docker to simplify deployment and management of the infrastructure.


# Task 1. Distributed web infrastructure
Here is a design for a three-server web infrastructure that hosts the website www.foobar.com:
Load Balancer Server:
This server will act as a load balancer, distributing incoming traffic between the two application servers.
It will run HAproxy, a software load balancer that provides high availability, load balancing, and proxying for TCP and HTTP-based applications.

## Application Server 1:
This server will host the first instance of the application.
It will run Nginx as the web server, serving static files and passing dynamic requests to the application server.
The server will run the application code base and connect to the MySQL database to retrieve and store data.

## Application Server 2:
This server will host the second instance of the application.
It will run Nginx as the web server, serving static files and passing dynamic requests to the application server.
The server will run the application code base and connect to the MySQL database to retrieve and store data.

## Database Server:
This server will host the MySQL database, where the application data will be stored.
It will be configured as a Primary-Replica cluster, where the primary node will handle all the writes, and the replica node will handle the reads.
The application servers will connect to the primary node to write data and connect to the replica node to read data.

## Some specifics about this infrastructure:
We are adding two application servers and a load balancer to handle more incoming traffic and provide high availability for the application.
The load balancer will be configured with a round-robin distribution algorithm, where it will evenly distribute incoming requests to both application servers.
The load balancer will be set up to enable an Active-Active setup, where both application servers are actively serving requests simultaneously.
The database primary node will handle all the writes, and the replica node will handle the reads, providing a fault-tolerant setup and reducing the read traffic on the primary node.
The primary node and the replica node will have different roles in the application. The primary node will handle all the writes, ensuring data consistency, while the replica node will handle the reads, providing faster access to data.

## The issues with this infrastructure:
The load balancer server can be a single point of failure (SPOF). If it fails, the application servers will not be able to handle incoming traffic.
The infrastructure does not have any firewall or HTTPS configured, leaving it vulnerable to security issues.
There is no monitoring set up to track the health of the servers and services, making it difficult to identify and troubleshoot issues.

# Task 2. Secured and monitored web infrastructure
Design for a three-server web infrastructure that hosts the website www.foobar.com:
* Load Balancer Server:
This server will act as a load balancer, distributing incoming traffic between the two application servers.
It will run HAproxy, a software load balancer that provides high availability, load balancing, and proxying for TCP and HTTP-based applications.
* Application Server 1:
This server will host the first instance of the application.
It will run Nginx as the web server, serving static files and passing dynamic requests to the application server.
The server will run the application code base and connect to the MySQL database to retrieve and store data.
* Application Server 2:
This server will host the second instance of the application.
It will run Nginx as the web server, serving static files and passing dynamic requests to the application server.
The server will run the application code base and connect to the MySQL database to retrieve and store data.
* Database Server:
This server will host the MySQL database, where the application data will be stored.
It will be configured as a Primary-Replica cluster, where the primary node will handle all the writes, and the replica node will handle the reads.
The application servers will connect to the primary node to write data and connect to the replica node to read data.
## Some specifics about this infrastructure:
We are adding two application servers and a load balancer to handle more incoming traffic and provide high availability for the application.
The load balancer will be configured with a round-robin distribution algorithm, where it will evenly distribute incoming requests to both application servers.
The load balancer will be set up to enable an Active-Active setup, where both application servers are actively serving requests simultaneously.
The database primary node will handle all the writes, and the replica node will handle the reads, providing a fault-tolerant setup and reducing the read traffic on the primary node.
The primary node and the replica node will have different roles in the application. The primary node will handle all the writes, ensuring data consistency, while the replica node will handle the reads, providing faster access to data.
* The issues with this infrastructure:
The load balancer server can be a single point of failure (SPOF). If it fails, the application servers will not be able to handle incoming traffic.
The infrastructure does not have any firewall or HTTPS configured, leaving it vulnerable to security issues.
There is no monitoring set up to track the health of the servers and services, making it difficult to identify and troubleshoot issues.


# Task 3. Scale up

## Specifics of the infrastructure we're describing.
* Firstly, let's distinguish between an application server and a web server. A web server is responsible for serving static content such as HTML, CSS, and images. It's the first point of contact for a user's request, and it returns the content that matches the user's request. In contrast, an application server handles dynamic content and business logic. It interacts with a database and processes data to create dynamic content that is then served by the web server.

* Now let's move on to the requirements listed.
* Adding a server: 
You're adding a server to distribute the workload and ensure high availability. When you have multiple servers, you can distribute the load across them to avoid overburdening any one server. Additionally, if one server goes down, the others can continue to handle traffic, ensuring the availability of your service.

* Adding a load balancer: 
A load balancer distributes incoming requests across multiple servers to ensure that no one server is overwhelmed. It can also provide redundancy by automatically redirecting traffic to healthy servers if one server goes down. Using HAProxy to configure a cluster provides even greater fault tolerance, as multiple load balancers can work together to ensure that traffic is always directed to healthy servers.

* Splitting components onto separate servers: 
This is a best practice in infrastructure design as it allows you to scale each component independently. For example, if your web server is overloaded but your application server is not, you can simply add more web servers to handle the increased load. Similarly, if your database is struggling, you can scale it up or out to improve its performance. Separating the components also reduces the risk of interference between them and can improve security by ensuring that each component only has access to the resources it needs.
Overall, this infrastructure design improves performance, scalability, and fault tolerance. It also allows you to isolate and scale each component independently, making it easier to manage your infrastructure as your service grows.



