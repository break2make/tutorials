
# Web System Design

General reading resources:
- Architecting Large Scale Systems | Creating Scalable Web Application Architecture [[video](https://www.youtube.com/watch?v=6pjGuuGsqxE&ab_channel=CuelogicTechnologies%7CAnLTICompany)]


## Monolithic vs Microservice Architecture
## API Gateway
## Proxy vs Reverse Proxy
In brief, (forward) proxy is used to protect clients while reverse proxy is used to protect servers. Sometimes, reverse proxy is also used as load balancer.

> Question: Half vs Full proxy?

For more details, check:

- What is a Proxy? [[vodeo](https://www.youtube.com/watch?v=jGQTS1CxZTE&ab_channel=F5DevCentral)] Great explanation.
- Proxy vs reverse proxy vs load balancer (2020) | Explained with real life examples [[video](https://www.youtube.com/watch?v=MiqrArNSxSM&ab_channel=ITkFunde)]
- Forward proxy vs reverse proxy difference explained - Brain Bytes (Java Brains) [[video](https://www.youtube.com/watch?v=AuINJdBPf8I&ab_channel=JavaBrains)]
- Proxy vs Reverse Proxy Server Explained [[video](https://www.youtube.com/watch?v=SqqrOspasag&ab_channel=HusseinNasser)]

## Load Balancing 
- Objective of load balancing is to distribute the loads instead of sending the request to a single server. 
- Load balancer is a server that forward internet traffic to multiple servers (downstream instances). 
- If one of the downstream server is down, it send the request to another server and hides this fact from the client. The load balancer, checks the helath of the downstream server on a regular basis or before fowarding a request to the request to it.
- It helps to manage 
  - Scalability (horizontal scaling)
  - Availability
  - Flexibility

Load balancer tyeps:
- Application load banalcer (layer 7): For example, it handles http-based traffic
- Network load balancer (layer 4): For example, it handales TCP-based traffic.

> Question: 
> How to scale load balancer?
> What are the different load balancing approaches?

For more details, checks:
- System Design: What is Load Balancing? [[video](https://www.youtube.com/watch?v=gMIslJN44P0&ab_channel=BeABetterDev)]
- AWS Elastic Load Balancing Introduction [[video](https://www.youtube.com/watch?v=qpHLRc4Qt1E&ab_channel=StephaneMaarek)]
- Load Balancer vs Reverse Proxy (Explained by Example) [[video](https://www.youtube.com/watch?v=S8J2fkN2FeI&ab_channel=HusseinNasser)]

## Scaling: Horizontal vs Vertical
Scalable dimensions:
- Cocurrent Connections
- CPU
- Moemory (Volume and speed)
- Network interfaces

For more details:
- System Design: What is Horizontal vs Vertical Scaling? [[video](https://www.youtube.com/watch?v=p1YQU5sEz4g&ab_channel=BeABetterDev)]
- Vertical and horizontal autoscaling on Kubernetes Engine [video](https://www.youtube.com/watch?v=XpeAITE4uqA&ab_channel=GoogleCloudTech)]
- How I scaled a website to 10 million users (web-servers & databases, high load, and performance) [[video](https://www.youtube.com/watch?v=yPF94QiI2qk&ab_channel=TechLead)]
- 

## Content Delivery Network

Good for static content distribution.


## Direct Server Return

## Event Driven Architecture
## Session, Token and Cokies
## Asynchronus vs Synchronus request

## Database



### Sharding

**Copied!**

Before you Shard, try the following first
0. Understand what your actual problem is before optimizing(too slow reads vs too slow writes)  Analyze your slowest queriers and see why its slow: https://youtu.be/-qNSXK7s7_w?t=237 Create indexes on appropriate columns and tune your data schema.

1. Horizontal Partitioning - Have partition key(mostly on primary key) and split database into different ranges.  This will create smaller B-trees on the indexes.

2. Vertical Partitioning - When you have columns that you rarely access, and you cut a column out of the main database. This will make reads faster for frequent queries and slower for not frequent queries and make your B-trees smaller(less space in memory also)

Partitioning Video: https://www.youtube.com/watch?v=QA25cMWp9Tk
---- << Database still in one machine when you do Partitioning.  Partitioning is done automatically by most modern DB systems and client doesn't have to know any difference).>>--


3. (Read Optimization) Master-Slaves replications, with master handling all writes and slaves handling all reads.  Masters sync with slaves with latest data
4. (Write optimization) Master-Master-Slaves replication in multi-regions(i.e. EAST vs WEST) with multiple masters handling writes, slaves handling reads, sync handled between masters<->masters and masters->read

5. Finally shard when you REALLY have to.  Sharding adds complex client logic and couples with your data base.  You also lose ACID as you cannot guarantee transactions and isolation between your shards.   You can use Vitess to help you manage your sharding query logic https://vitess.io/

### Resources
- When should you shard your database? [[video](https://www.youtube.com/watch?v=iHNovZUZM3A&ab_channel=HusseinNasser)]
- Scaling Databases - Web Development  [[video](https://www.youtube.com/watch?v=dkhOZOmV7Fo&ab_channel=HusseinNasser)]

## Docker

### Nginx as Reverse Proxy
- Docker and Nginx Reverse Proxy [[video](https://www.youtube.com/watch?v=hxngRDmHTM0&ab_channel=WesDoyle)]
- Putting it All Together - Docker, Docker-Compose, NGinx Proxy Manager, and Domain Routing - How To. [[video](https://www.youtube.com/watch?v=cjJVmAI1Do4&ab_channel=AwesomeOpenSource)]

## API

# Links
- [Microservices + Events + Docker = A Perfect Trio](https://www.youtube.com/watch?v=sSm2dRarhPo)
- [Developing microservices with aggregates - Chris Richardson](https://www.youtube.com/watch?v=7kX3fs0pWwc)
- [Bosch IoT Permissions](https://permissions.s-apps.de1.bosch-iot-cloud.com/docs/developer-guide/index.html#Best-Practices-when-using-JWTs_191598815)
- [he Art of Scalability: Scalable Web Architecture, Processes, and Organizations for the Modern Enterprise](https://www.oreilly.com/library/view/the-art-of/9780134031408/)



