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
## Task 0. Simple web stack
To design a one server web infrastructure that hosts the website reachable via www.foobar.com, let's start by understanding the user's request. When a user types in www.foobar.com into their web browser and hits enter, the request is sent to the DNS (Domain Name System) server to resolve the IP address associated with www.foobar.com. Once the IP address is resolved, the user's computer sends a request to the IP address to access the website.
# Specifics about this infrastructure
In our infrastructure, we will have one server that will host the web server (Nginx), application server, and the MySQL database. We will install the LAMP stack (Linux, Apache, MySQL, PHP) on the server.
The domain name foobar.com will be configured with a www record that points to our server's IP address 8.8.8.8. This will allow users to access the website using the URL www.foobar.com.
The web server (Nginx) will receive the user's request and serve static files such as HTML, CSS, and images. It will also route dynamic requests to the application server. The application server will handle dynamic requests and generate responses based on the user's request. It will communicate with the MySQL database to fetch and store data.
The MySQL database will store the website's data such as user information, blog posts, and other content.
The server will use HTTP (Hypertext Transfer Protocol) to communicate with the user's computer requesting the website. The web server and application server will generate HTTP responses that will be sent back to the user's computer.

# Issues about this infrastructure
However, this infrastructure has some issues. It is a single point of failure (SPOF), which means that if the server goes down, the website will not be accessible. There will be downtime when maintenance is needed, such as deploying new code, as the web server needs to be restarted. The infrastructure cannot scale if there is too much incoming traffic, as the single server will not be able to handle the load.

# How to address the issues
To address these issues, we can implement load balancing by adding more servers to the infrastructure. We can also implement a CDN (Content Delivery Network) to distribute content globally and reduce the load on the server. Additionally, we can use containerization technology like Docker to simplify deployment and management of the infrastructure.


