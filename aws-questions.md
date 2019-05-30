# AWS Technical Screening Question

1. ### What is AWS?

    AWS is a public cloud computing platform. 

    >Amazon Web Services (AWS) is the world’s most comprehensive and broadly adopted cloud platform, offering over 165 fully featured services from data centers globally. Millions of customers —including the fastest-growing startups, largest enterprises, and leading government agencies—trust AWS to power their infrastructure, become more agile, and lower costs. -[Amazon](https://aws.amazon.com/what-is-aws/)

1. ### What are the core services of AWS?

    - #### AWS Compute
        - **EC2** – Elastic Compute Cloud allows you to easily scale virtual machines for your main compute horsepower; note that an opposite approach in AWS is serverless compute with Lambda AWS Storage
        - **S3** – Simple Storage Services is object-based, key/value storage for many purposes in AWS
        - **EBS** – Elastic Block Store permits the use of MDD or SDD storage for many purposes, including boot volumes for EC2 instances
    - #### AWS Database
        - **RDS** – Relational Database Service allows you to host many database types in the cloud; this includes Oracle, MS SQL Server, and even Amazon’s own Aurora
        - **DynamoDB** – a NoSQL database option in the cloud that performs blazing performance and on-demand scalability
        - **ElastiCache** – creates in-memory caches for impressive performance interaction; this service also supports open standards in caching
    - #### AWS Networking
        - **VPC** – Virtual Private Cloud provides the networking components needed for an infrastructure including subsets, gateways, routing tables, and security mechanisms
    - #### AWS Management
        - **CloudWatch** – Permits the monitoring of key services; uses metrics and alarms for a familiar monitoring approach
        - **CloudTrail** – Permits the tracking of potentially all the API calls to AWS; this allows you detailed analysis of all events no matter the source – Web Console, CLI, SDK, etc.
    - #### AWS Security
        - **IAM** – Identity and Access Management allows the creation of users, groups, and roles for interacting securely with AWS
    - #### AWS Application Integration
        - **SNS** – the Simple Notification Service allows the generation of email and text notifications based on AWS events
        - **SQS** – the Simple Queue Service assists you in decoupling components and queuing messages between these components; this service helps the use of micro services for your processing needs

1. ### Explain S3?

    S3 stands for *Simple Storage Service*.  It is an object store exposed via a REST API.

    >Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics. Amazon S3 provides easy-to-use management features so you can organize your data and configure finely-tuned access controls to meet your specific business, organizational, and compliance requirements. Amazon S3 is designed for 99.999999999% (11 9's) of durability, and stores data for millions of applications for companies all around the world. -[Amazon](https://aws.amazon.com/s3/)

1. ### What is AMI?

    AMI stands for Amazon Machine Image.  It’s a template that provides the information (an operating system, an application server, and applications) required to launch an instance, which is a copy of the AMI running as a virtual server in the cloud.  You can launch instances from as many different AMIs as you need.

1. ### Mention what the relationship between an instance and AMI is?

    From a single AMI, you can launch multiple types of instances.  An instance type defines the hardware of the host computer used for your instance. Each instance type provides different computer and memory capabilities.  Once you launch an instance, it looks like a traditional host, and we can interact with it as we would with any computer.

1. ### What does an AMI include?

    - A template for the root volume for the instance
    - Launch permissions decide which AWS accounts can avail the AMI to launch instances
    - A block device mapping that determines the volumes to attach to the instance when it is launched

1. ### How can you interact with Amazon S3?

    You can use the console, command-line interface (CLI) or directly via the REST API.

1. ### How many buckets can you create in AWS by default?

    By default, you can create up to **100 buckets** in each of your AWS accounts.

1. ### How do you vertically scale an Amazon instance? How?

    - Automatically
        - Use AWS Ops Automator which has vertical scaling features
    - Manually
        - Spin up a new larger instance than the one you are currently running
        - Pause that instance and detach the root webs volume from the server and discard
        - Then stop your live instance and detach its root volume
        - Note the unique device ID and attach that root volume to your new server
And start it again

1. ### Explain what T2 instances are?

    T2 instances are Burstable Performance Instances that provide a baseline level of CPU performance with the ability to burst above the baseline. The baseline performance and ability to burst are governed by CPU Credits. T2 instances accumulate CPU Credits when they are idle, and consume CPU Credits when they are active.

1. ### In a VPC with private and public subnets, database servers are most commonly attached to which subnet?

    Private subnets.

1. ### Mention what the security best practices for Amazon EC2 are?

    - Least Access: Restrict server access from both the network and on the instance, install only the required OS components and applications, and leverage host-based protection software.
    - Least Privilege: Define the minimum set of privileges each server needs in order to perform its function.
    - Configuration Management: Create a baseline server configuration and track each server as a configuration item. Assess each server against the current recorded baseline to identify and flag any deviations. Ensure each server is configured to generate and securely store appropriate log and audit data.
    - Change Management: Create processes to control changes to server configuration baselines.
    Audit Logs: Audit access and all changes to EC2 instances to verify server integrity to ensure only authorized changes are made.

    More info at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-best-practices.html

1. ### While connecting to your instance what are some possible connection issues one might face?

    - Connection timed out
    - User key not recognized by the server
    - Host key not found, permission denied
    - An unprotected private key file
    - Server refused our key or No supported authentication method available
    - Security group incorrectly configured
    - Instance IP not reachable e.g. private IP

1. ### What are key-pairs used for in EC2 instances?

    Key-pairs are secure login information for your virtual machines. To connect to the instances, typically over SSH, you can use key-pairs which contain a public-key and private-key.

1. ### What are the different types of instances?

    - General purpose
    - Computer Optimized
    - Memory Optimized
    - Storage Optimized
    - Accelerated Computing

1. ### How do you configure broadcast or multicast in a VPC?

    You can't.  Currently Amazon VPC does not provide support for broadcast or multicast.

1. ### How many Elastic IPs are allowed per region?

    **5 Elastic IP** addresses are allowed for each AWS account.

1. ### Explain default storage class in S3

    The default storage class is Standard frequently accessed.

1. ### What are roles?

    Roles are used to map security policy to resources. Roles are granted to users, identities and even other resource e.g. EC2 instances.

1. ### What is VPC?


    VPC stands for *Virtual Private Cloud*. It allows you to customize your networking configuration. It is a network which is logically isolated. It allows you to have your own IP address range,  internet gateways, subnets and security groups.

1. ### Explain snowball

    Snowball is a petabyte-scale data transport solution that uses portable, secure devices to physically (i.e. you carry it) transfer large amounts of data into and out of the AWS Cloud.

1. ### What is a redshift?

    Redshift is a fully managed big data warehouse service.

1. ### What are the advantages of auto-scaling?

    - Availability
    - Performance
    - Cost management

1. ### Can you establish a Peering connection to a VPC in a different region?

    No, It’s only possible between VPCs in the same region.

1. ### How many subnets can you have per VPC?

    You can have 200 subnets per VPC.

1. ### What is the role of AWS CloudTrail?

    AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account. With CloudTrail, you can log, continuously monitor, and retain account activity related to actions across your AWS infrastructure. CloudTrail provides event history of your AWS account activity, including actions taken through the AWS Management Console, AWS SDKs, command line tools, and other AWS services. This event history simplifies security analysis, resource change tracking, and troubleshooting.

1. ### What is SimpleDB?

    Amazon SimpleDB is a highly available NoSQL data store that offloads the work of database administration. Developers simply store and query data items via web services requests and Amazon SimpleDB does the rest.

1. ### Explain Amazon ElasticCache

    Amazon ElastiCache offers fully managed Redis and Memcached. Seamlessly deploy, run, and scale popular open source compatible in-memory data stores. Build data-intensive apps or improve the performance of your existing apps by retrieving data from high throughput and low latency in-memory data stores. Amazon ElastiCache is a popular choice for Gaming, Ad-Tech, Financial Services, Healthcare, and IoT apps.

1. ### What is AWS Lambda?

    AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume - there is no charge when your code is not running.

1. ### List the types of storage backing for the root device of an AMI

    - Instance store backed
    - EBS backed

1. ### Explain Geo Restriction in CloudFront

    A Geo-restriction feature helps you to prevent users of specific geographic locations from accessing content which you’re distributing through a CloudFront web distribution.

1. ### What is Amazon EMR?

    Amazon EMR provides a managed Hadoop framework that makes it easy, fast, and cost-effective to process vast amounts of data across dynamically scalable Amazon EC2 instances.

1. ### Do you need an internet gateway to use peering connections?

    Yes, the Internet gateway is needed to use VPC (virtual private cloud peering) connections.

1. ### How do you connect an EBS volume to multiple instances?

    You can't.  EBS volumes may only be connect to a single instance.

1. ### Name the different types of Load Balancers in AWS and describe the primary differences?

    - **Application Load Balancer**
        - makes routing decisions at the application layer (HTTP/HTTPS)
        - supports path-based routing
        - can route requests to one or more ports on each container instance in your cluster
        - supports dynamic host port mapping. 
    - **Classic Load Balancer**
        - makes routing decisions at either the transport layer (TCP/SSL) or the application layer (HTTP/HTTPS)
        - requires a fixed relationship between the load balancer port and the container instance port.
    - **Network Load Balancer**
        - makes routing decisions at the transport layer (TCP/SSL)
        - can handle millions of requests per second
        - forwards the request without modifying the headers
        - supports dynamic host port mapping.

1. ### Can vertically scaling is allows in  Amazon Instance?

    Yes, it can be done manually or automatically with AWS Ops Automator v2

1. ### What are lifecycle hooks in Auto Scaling?

    Lifecycle hooks enable you to perform custom actions by pausing instances as an Auto Scaling group launches or terminates them. When an instance is paused, it remains in a wait state until either you complete the lifecycle action using the complete-lifecycle-action CLI command or CompleteLifecycleAction API action, or the timeout period ends (one hour by default).

1. ### Name and describe the storage classes available in Amazon s3?

    - Standard for general-purpose storage of frequently accessed data
    - Intelligent-Tiering for data with unknown or changing access patterns
    - Standard-Infrequent Access (S3 Standard-IA) and S3 One Zone-Infrequent Access (S3 One Zone-IA) for long-lived, but less frequently accessed data
    - Glacier and Glacier Deep Archive for long-term archive and digital preservation
    - Amazon S3 also offers capabilities to manage your data throughout its lifecycle. Once an S3 Lifecycle policy is set, your data will automatically transfer to a different storage class without any changes to your application.  

1. ### Name some of the DB engines which can be used in AWS RDS

    - MS SQLServer
    - MariaDB
    - MySQL
    - Oracle
    - PostgreSQL
    - Aurora
