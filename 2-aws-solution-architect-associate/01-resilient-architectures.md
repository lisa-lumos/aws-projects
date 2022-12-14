# 1. Resilient Architectures
We see this architecture often: Web Servers - App Servers - Database Servers. Having multi-tier because if one tier breaks down, the other tiers can serve the traffic. They are easy to separate in AWS by putting into different subnets. 

Q1: A database is running on an Amazon EC2 instance. The database software has a backup feature that requires block storage. What storage option would be the lowest cost option for the backup data? 
- Answer: Amazon EBS Cold HDD Volume (sc1). 
- Note: Amazon S3 is an object storage, not a block storage. Amazon EBS Throughput Optimized HDD Volume (st1) is more expensive than the answer. Block storage (EBS) is more like a hard drive volume, is flexible. Object storage (S3) contains ID, Data, and Metadata, it is more like a hard bound book, not flexible, need to remove an object to update an object. File storage (EFS, works on the NSFv4 protocol, not compatible with Windows which is FSX) is like a block storage, but multiple computers can access this storage at the same time, like a shared storage. For EC2 storage, refer `https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html`. Cold storage means infrequently accessed storage. 

Q2: Which set of database engines does Amazon Relational Database Service (Amazon RDS) currently support?
- Answer: Oracle, Microsoft SQL Server, MySQL, PostgreSQL, MariaDB, Amazon Aurora (RDBMS built for the cloud with full MySQL and PostgreSQL compatibility)
- Note: Cassandra, MongoDB are not relational databases. 

Q3: Your web service has a performance SLA to respond to 90% of requests in <5 seconds. Under normal and heavy operations, disbributing requests over four instances meets performance requirements. What architecture ensures cost efficient high availability of your service if an Availability Zone becomes unreachable? 
- Answer: Deploy the service on four servers with auto scaling across two availability zones. 
- Note: if one zone becomes unavailable, because it is an auto scaling group, it will quickly add two more servers, which will then meet the requirements on performance. 

Q4: You wish to deploy a microservices-based application without the operational overhead of managing infrastructure. This solution needs to accommodate rapid changes in the volume of requests. What do you do?
- Answer: Run the microservices in AWS Lambda behind an API Gateway
- Note: Do not want to manage infrastructure, so not EC2. Containers also relies on EC2. While Lambda is a fully managed, serverless service. What beanstalk does is that it spins up a cloud formation template which automatically spins up EC2 instances - so there's still server involved, and has maintenance overhead compared with Lambda or API Gateway. 

Q5: Using Amazon Elastic Container Service (ECS) to run a containerized we application, you wish to minimize costs by running multiple copies of a task on each container instance. What do you do?
- Answer: Configure an Application Load Balancer to distribute the requests using path-based routing. 
- Note: ... (needs further research). Application Load Balancer, Network Load Balancer, Gateway Load Balancer, Classic Load Balancer. Route 53 - routing policy: simple RR, weighted, geo-location.  

Q6: An application consists of Amazon EC2 instances placed in different Availability Zones. The EC2 instances sit behind an Application Load Balancer, and are managed via an Auto Scaling group. A network address translation (NAT) instance is used for the Amazon EC2 instances to download updates from the internet. Which option is a bottleneck in the architecture?
- Answer: NAT instance. 
- Note: has multiple EC2 instances which is good, elastic load balancing and auto scaling group are both managed by AWS, so probably good. NAT instance is in a singular form, may have problem.  

Q7: A company must store around 500GB of files, and expects the data size to increase to 80TB over the next couple of months. The company needs access to this data at all times. Which would be an ideal storage option for these requirements? 
- Answer: S3.
- Note: looking for file storage, so cannot choose databases. They always need access to data, so cannot be S3 Glacier. This leaves us S3 only. 

Q8: You are designing a leaderboard that expects to have millions of users. You want to ensure the lowest latency for this leaderboard. What datastore would be best suited? Amazon DynamoDB? Amazon RDS? AWS Glue? Amazon Redshift?
- Answer: Amazon DynamoDB
- Note: AWS Glue is for data catalog, crawler, ETL service. Redshift is for analytics, not transactions. Requires low latency, so should pick DynamoDB. RDS is slightly older technology and hasn't been designed for web-scale apps. 
















