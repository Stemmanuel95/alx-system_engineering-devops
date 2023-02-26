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
