## AWS Core Services

 | *AWS Compute Services* | Purpose |
 |---|---|
 | EC2 |  Virtual servers, fully managed by user (OS, scaling). <br> instances: spot (cheapest can be terminated), reserved (upfront payment, low cost), on-demand (pay for usage). <br> Auto-scaling group: automatically adjusts EC2 instances based on metrics like CPU or network usage. <br> launch configurations |
  | Lambda |  Serverless, event-driven, auto-scaling, pay per execution. |
  | ECS | Container orchestration services |
  | Elastic Load Balancer | ALB (Application Load Balancer): HTTP/HTTPS, layer 7, routing based on content. <br> NLB (Network Load Balancer): TCP/UDP, layer 4, ultra-low latency. <br> CLB (Classic Load Balancer): Legacy, basic load balancing. |

&nbsp;

 | *AWS Storage Services* | Purpose |
 |---|---|
 | S3     | Object storage, unlimited, scalable, highly durable. <br> versioning: Keep multiple versions of objects. <br> lifecycle policies: Automate transition between storage classes or deletion. <br> bucket policies: Control access with JSON-based rules. <br> classes: standard, infrequent access, glacier storage/deep archive |
 | EBS    | Block storage for EC2, persists with instance lifecycle. |
 | EFS    |  NFS file storage for multiple EC2 instances, scalable. |

&nbsp;

| *AWS Database Services* | Purpose |
|---|---|
| RDS      | Managed SQL databases (MySQL, PostgreSQL, etc.) <br> Read replicas: Read-only copy of the database for scaling read operations. |
| DynamoDB | NoSQL, key-value, highly scalable. <br>  partitioning: Data is split across partitions based on the partition key, ensures horizontal scaling. |
| Aurora   | Serverless.  High-performance MySQL/PostgreSQL-compatible RDS |
| Redshift | Data warehouse for analytics |

 &nbsp;
 
 ## *Networking*

 | *AWS Networking Services* | Purpose |
 |---|---|
 | VPC                | Per Region. <br>Virtual Private Cloud, isolated network in AWS. |
 | Subnets            | Per AZ (public + private). <br> Public: Accessible from the internet (via IGW). <br>  Private: Not directly accessible, uses NAT for outbound access. |
 | Route53            | DNS:  translates domain names into IP addresses |
 | IGW                | for public Subnet: Accessible from the internet (via IGW) |
 | NAT Gateway        | <br> Nat instance in public subnet. <br> For private Subnet: Not directly accessible, uses NAT for outbound access |
 | Security Group     | Instance-level firewall, stateful |
 | Network ACL        | Subnet-level firewall, stateless |
 | AWS Direct Connect | Dedicated private network connection between on-prem and AWS. |
 | VPC Endpoint       | If private instances need to access only AWS services (S3, DynamoDB, etc.), you can use VPC Endpoints instead of NAT.|
 
&nbsp;


## *AWS Security*
 | Identity And Access Management | Purpose |
 |---|---|
 | IAM policies | JSON permissions <br>. Resource based. <br>  Identity bases. |
 | IAM roles    | Permissions assigned for temporary access. Used to grant permissions to AWS services, users, or applications without sharing keys.<br> An IAM Role is an identity in AWS (like a user) but without long-term credentials (no password, no access keys). |
 | IAM groups   | Collection of users |
 | IAM Users    | Individual accounts |

&nbsp;
 
 | Data Protection|---|
 |---|---|
 | KMS | AWS Key Management Service, encrypts data at rest, integrates with S3, EBS, RDS. for encrypt data |
 | Secrets Manager | Rotates/manage DB/API credentials securely. |
 | Parameter Store | Stores config values and secrets (basic) |

&nbsp;

 | User identity and authentication|---|
 |---|---|
 | AWS Cognito | Manages authentication, authorization, user sign-up/sign-in, token-based access. <br> Provides user sign-up, sign-in, and access control for web and mobile apps.<br> Supports federated identity (login with Google, Facebook, Apple, Amazon, or enterprise IdPs via SAML/OIDC).<br> Issues JWT tokens (ID, access, refresh) for authenticated sessions. |

&nbsp; 
&nbsp;

---
## *AWS DevOps*

| *IaS, CI/CD* | Purpose |
|---|---|
| CloudFormation | Infrastructure as code using YAML/JSON templates |
| CDK            | Use programming languages (Python, TypeScript) to define infra |
| CodePipeline   | CI/CD workflow orchestration |
| CodeBuild      | Build & test code |
| CodeDeploy     | Deploy applications to EC2, Lambda, or on-prem |

&nbsp; 

 | Monitoring |---|
 |---|---|
 | CloudWatch | Metrics, logs, alarms |
 | CloudTrail | Audit API calls |
 | AWS Config | Track configuration changes |
    
&nbsp;


----
## *Analytics & Data Processing*

 | Data Processing |---|
 |---|---|
 | Athena                  | Serverless query service that uses Presto SQL to query data directly in S3. Pay per query scanned. |
 | EMR (Elastic MapReduce) | Managed Hadoop, Spark, Hive, Presto cluster service for big data. |
 | Glue                    | Serverless ETL (Extract-Transform-Load) service, crawls schema, prepares data for analytics. |

&nbsp;
 
 | Kinesis |---|
 |---|---|
 | Streams | Real-time data ingestion (millisecond latency). |
 | Firehose | Delivery to S3/Redshift/ElasticSearch with transformations. |
 | Analytics | SQL queries on streaming data. |
 
&nbsp;
&nbsp;


## *Application Services*
 
 | Messaging |---|
 |---|---| 
 | SQS (Simple Queue Service)        | Queue, pull-based.<br> Standard: Unlimited throughput, at-least-once delivery, no ordering guarantee.<br> FIFO: Ordered messages, exactly-once delivery, lower throughput. |
 | SNS (Simple Notification Service) | SNS = Pub/Sub, push-based; SQS = Queue, pull-based. Often used together. |

 | Apps |---|
 |---|---|
 | Step Functions |  use Step Functions with Lambda to orchestrate workflows with retries, branching, and error handling. |
 | API Gateway    | API Gateway exposes REST/HTTP/WebSocket APIs. <br> triggers Lambda functions for serverless apps |

&nbps;

## *Edge & IoT*

 | Edge |---|
 |---|---|
 | CloudFront     | Global CDN caches content at edge locations. |
 | AWS Wavelength | use Wavelength with 5G: Brings compute closer to mobile users, reduces latency. |
 | Greengrass     | Runs ML inference and IoT apps on edge devices.|


&nbps;


| AWS IoT Key Services | Purpose |
|---|---|
| IoT Core            |  Connects devices using MQTT, HTTP, WebSockets. Manages secure communication with X.509 certificates, IAM policies, AWS IoT policies. |
| Device Shadow       |  A JSON document that stores the last reported and desired state of a device. Allows apps to interact with devices even if they’re offline. |
| IoT Rules Engine    | Processes incoming device data and routes it to other AWS services (e.g., S3, Lambda, DynamoDB, Kinesis). |
| IoT Greengrass      | Extends AWS IoT to edge devices. Can run AWS Lambda, ML inference, local messaging, and caching without constant cloud connection. |
| IoT Analytics       | Prepares and analyzes IoT data at scale (cleans, enriches, runs SQL queries, integrates with ML). |
| IoT SiteWise        | Collects and analyzes data from industrial equipment. |
| IoT Events          | Detects patterns/events from IoT sensors and triggers alerts/actions. |
| IoT Device Defender | Monitors security policies, detects anomalies, audits devices.

---

