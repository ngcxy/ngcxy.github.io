---
layout: page
title: Cloud Course Registration System
description: a C++ socket project deployed on AWS
img: assets/img/1/1-network.png
importance: 50
category:
giscus_comments: true
---

[code link](https://github.com/ngcxy/Network-Socket-Programming)

Web registration system is the crucial place for students to plan their future courses. 
When registration for a new semester begins, hundreds of students will flood into the registration website. 
In such a situation, a stable and efficient system is indispensable.

In this project, I built a course registration backend using sockets, which provides fast and reliable connections between hundreds of clients and our servers. 
It includes five communication end-points:

- Client: used by a student to access the registration system
- Main server (serverM): coordinate with the backend servers
- Credential server (serverC): verify the identity of the student
- Department servers (serverCS and serverEE): store the information of courses offered by this department

Input data:

- Credential server: cred.txt for encrypted usernames and passwords
- Department servers: ee.txt and cs.txt for course information

I implemented both TCP and UDP sockets for connection, with a TCP socket for client-serverM communication, and UDP sockets for all backend servers' communication.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/1/1-network.png" title="network illustration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

The code is written in C++ and built in the linux environment, you can access it [here](https://github.com/ngcxy/Network-Socket-Programming).
After learning cloud computing with AWS, I deployed it onto AWS EC2 instances.
I assigned a VPC for all the backend servers to ensure an isolated working space, and then associated an elastic IP for the public interface of the main server.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/1/1-vpc.png" title="network illustration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

After all the implementations are completed, clients can now access from outside to this system to login, and acquire information about the course they want to register.

Here's a demo for the application.

<iframe width="780" height="400" src="../../../assets/img/1/1-demo.MP4" frameborder="0" allowfullscreen></iframe>

Backup for the demo is on [YouTube](https://youtu.be/E1aWdYwHuns)
