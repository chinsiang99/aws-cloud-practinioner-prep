# AWS Global Infrastructure

## Availability Zones (AZs)

An Availability Zone is a single data center or a group of data centers within a Region. Availability Zones are located tens of miles apart from each other. This is close enough to have low latency (the time between when content requested and received) between Availability Zones. However, if a disaster occurs in one part of the Region, they are distant enough to reduce the chance that multiple Availability Zones are affected.

<div align="center">
  <img src="./availability-zone.png" alt="availability-zone" width="300"/>
</div>

- discrete data centers around the world, seperated from each other by network, power source, and a meaningful distance
- high availability: hosting resources in multiple AZs
- Fault tolerance: ability to provide uninterrupted performance even during natural/human-made disasters
- Resiliency: capacity to recover from disasters quickly

## Region
- two or more availability zones
- All AZs within a region are interconnected with high-bandwidth, low-latency networking
- Different regions have different AWS Cloud offerings
- Generally choose the Region closest to your physical location
- Can host resources in multiple regions for many reasons

## AWS Wavelength Zones
- provides ultra-low-latency user experience for application end users by embedding AWS compute and storage services within 5G networks
- provides mobile edge computing infrastructure to develop, deploy, and scale ultra-low-latency application

# Compute Services

## Amazon Elastic Compute Cloud (EC2)
Amazon EC2 is a highly flexible, scalable, and customizable **cloud computing service that provides the virtual infrastructure needed to run various applications and workloads**. It allows businesses to avoid the upfront costs of physical hardware and scale their compute resources dynamically based on demand.

Amazon Elastic Compute Cloud (Amazon EC2) provides secure, resizable compute capacity in the cloud as Amazon EC2 instances. 

Imagine you are responsible for the architecture of your company's resources and need to support new websites. With traditional on-premises resources, you have to do the following:

- Spend money upfront to purchase hardware.
- Wait for the servers to be delivered to you.
- Install the servers in your physical data center.
- Make all the necessary configurations.

By comparison, with an Amazon EC2 instance you can use a virtual server to run applications in the AWS Cloud.

- You can provision and launch an Amazon EC2 instance within minutes.
- You can stop using it when you have finished running a workload.
- You pay only for the compute time you use when an instance is running, not when it is stopped or terminated.
- You can save costs by paying only for server capacity that you need or want.

### How Amazon EC2 works
1. Launch

First, you launch an instance. Begin by selecting a template with basic configurations for your instance. These configurations include the operating system, application server, or applications. You also select the instance type, which is the specific hardware configuration of your instance. 

As you are preparing to launch an instance, you specify security settings to control the network traffic that can flow into and out of your instance. Later in this course, we will explore Amazon EC2 security features in greater detail.

2. Connect

Next, connect to the instance. You can connect to the instance in several ways. Your programs and applications have multiple different methods to connect directly to the instance and exchange data. Users can also connect to the instance by logging in and accessing the computer desktop.


3. Use

After you have connected to the instance, you can begin using it. You can run commands to install software, add storage, copy and organize files, and more.

### Amazon EC2 instance types

Amazon EC2 instance types are optimized for different tasks. When selecting an instance type, consider the specific needs of your workloads and applications. This might include requirements for compute, memory, or storage capabilities.

To learn more about Amazon EC2 instance types, expand each of the following five categories.

1. General purpose instances
General purpose instances provide a **balance of compute, memory, and networking resources**. You can use them for a variety of workloads, such as:

- application servers
- gaming servers
- backend servers for enterprise applications
- small and medium databases

Suppose that you have an application in which the resource needs for compute, memory, and networking are roughly equivalent. You might consider running it on a general purpose instance because the application does not require optimization in any single resource area.

2. Compute optimized instances
Compute optimized instances are ideal for compute-bound applications that benefit from **high-performance processors**. Like general purpose instances, you can use compute optimized instances for workloads such as web, application, and gaming servers.

However, the difference is compute optimized applications are ideal for high-performance web servers, **compute-intensive applications** servers, and dedicated gaming servers. You can also use compute optimized instances for batch processing workloads that require processing many transactions in a single group.

3. Memory optimized instances
Memory optimized instances are designed to deliver fast performance for workloads that process large datasets in memory. In computing, memory is a temporary storage area. It holds all the data and instructions that a central processing unit (CPU) needs to be able to complete actions. Before a computer program or application is able to run, it is loaded from storage into memory. This preloading process gives the CPU direct access to the computer program.

Suppose that you have a workload that requires large amounts of data to be preloaded before running an application. This scenario might be a high-performance database or a workload that involves performing real-time processing of a large amount of unstructured data. In these types of use cases, consider using a memory optimized instance. Memory optimized instances enable you to run workloads with high memory needs and receive great performance.

4. Accelerated computing instances
Accelerated computing instances use hardware accelerators, or coprocessors, to perform some functions more efficiently than is possible in software running on CPUs. Examples of these functions include floating-point number calculations, graphics processing, and data pattern matching.

In computing, a hardware accelerator is a component that can expedite data processing. Accelerated computing instances are ideal for workloads such as graphics applications, game streaming, and application streaming.

5. Storage optimized instances
 
Storage optimized instances are designed for workloads that require high, sequential read and write access to large datasets on local storage. Examples of workloads suitable for storage optimized instances include distributed file systems, data warehousing applications, and high-frequency online transaction processing (OLTP) systems.

In computing, the term input/output operations per second (IOPS) is a metric that measures the performance of a storage device. It indicates how many different input or output operations a device can perform in one second. Storage optimized instances are designed to deliver tens of thousands of low-latency, random IOPS to applications. 

You can think of input operations as data put into a system, such as records entered into a database. An output operation is data generated by a server. An example of output might be the analytics performed on the records in a database. If you have an application that has a high IOPS requirement, a storage optimized instance can provide better performance over other instance types not optimized for this kind of use case.

### Amazon EC2 pricing
With Amazon EC2, you pay only for the compute time that you use. Amazon EC2 offers a variety of pricing options for different use cases. For example, if your use case can withstand interruptions, you can save with Spot Instances. You can also save by committing early and locking in a minimum level of use with Reserved Instances.

Five categories:
1. On-Demand
On-Demand Instances are ideal **for short-term**, **irregular workloads** that cannot be interrupted. No upfront costs or minimum contracts apply. The instances run continuously until you stop them, and you pay for only the compute time you use.

Sample use cases for On-Demand Instances include developing and testing applications and running applications that have unpredictable usage patterns. On-Demand Instances are not recommended for workloads that last a year or longer because these workloads can experience greater cost savings using Reserved Instances.

2. Reserved Instances
Reserved Instances are a billing discount applied to the use of On-Demand Instances in your account. There are two available types of Reserved Instances:

- Standard Reserved Instances
- Convertible Reserved Instances

You can purchase Standard Reserved and Convertible Reserved Instances for a 1-year or 3-year term. You realize greater cost savings with the 3-year option. 

Standard Reserved Instances: This option is a good fit if you know the EC2 instance type and size you need for your steady-state applications and in which AWS Region you plan to run them. Reserved Instances require you to state the following qualifications:

- Instance type and size: For example, m5.xlarge
- Platform description (operating system): For example, Microsoft Windows Server or Red Hat Enterprise Linux
- Tenancy: Default tenancy or dedicated tenancy

You have the option to specify an Availability Zone for your EC2 Reserved Instances. If you make this specification, you get EC2 capacity reservation. This ensures that your desired amount of EC2 instances will be available when you need them. 

Convertible Reserved Instances: If you need to run your EC2 instances in different Availability Zones or different instance types, then Convertible Reserved Instances might be right for you. Note: You trade in a deeper discount when you require flexibility to run your EC2 instances.

At the end of a Reserved Instance term, you can continue using the Amazon EC2 instance without interruption. However, you are charged On-Demand rates until you do one of the following:

- Terminate the instance.
- Purchase a new Reserved Instance that matches the instance attributes (instance family and size, Region, platform, and tenancy).

3. EC2 Instance Savings Plans
AWS offers Savings Plans for a few compute services, including Amazon EC2. EC2 Instance Savings Plans reduce your EC2 instance costs when you make an hourly spend commitment to an instance family and Region for a 1-year or 3-year term. This term commitment results in savings of up to 72 percent compared to On-Demand rates. Any usage up to the commitment is charged at the discounted Savings Plans rate (for example, $10 per hour). Any usage beyond the commitment is charged at regular On-Demand rates.

The EC2 Instance Savings Plans are a good option if you need flexibility in your Amazon EC2 usage over the duration of the commitment term. You have the benefit of saving costs on running any EC2 instance within an EC2 instance family in a chosen Region (for example, M5 usage in N. Virginia) regardless of Availability Zone, instance size, OS, or tenancy. The savings with EC2 Instance Savings Plans are similar to the savings provided by Standard Reserved Instances.

Unlike Reserved Instances, however, **you don't need to specify up front what EC2 instance type and size** (for example, m5.xlarge), **OS**, and **tenancy to get a discount**. Further, you don't need to commit to a certain number of EC2 instances over a 1-year or 3-year term. Additionally, the EC2 Instance Savings Plans don't include an EC2 capacity reservation option.

Later in this course, you'll review AWS Cost Explorer, which you can use to visualize, understand, and manage your AWS costs and usage over time. If you're considering your options for Savings Plans, you can use AWS Cost Explorer to analyze your Amazon EC2 usage over the past 7, 30, or 60 days. AWS Cost Explorer also provides customized recommendations for Savings Plans. These recommendations estimate how much you could save on your monthly Amazon EC2 costs, based on previous Amazon EC2 usage and the hourly commitment amount in a 1-year or 3-year Savings Plan.

4. Spot Instances
Spot Instances are ideal for workloads with flexible start and end times, or that can withstand interruptions. Spot Instances use unused Amazon EC2 computing capacity and offer you cost savings at up to 90% off of On-Demand prices.

Suppose that you have a background processing job that can start and stop as needed (such as the data processing job for a customer survey). You want to start and stop the processing job without affecting the overall operations of your business. If you make a Spot request and Amazon EC2 capacity is available, your Spot Instance launches. However, if you make a Spot request and Amazon EC2 capacity is unavailable, the request is not successful until capacity becomes available. The unavailable capacity might delay the launch of your background processing job.

After you have launched a Spot Instance, if capacity is no longer available or demand for Spot Instances increases, your instance may be interrupted. This might not pose any issues for your background processing job. However, in the earlier example of developing and testing applications, you would most likely want to avoid unexpected interruptions. Therefore, choose a different EC2 instance type that is ideal for those tasks.

5. Dedicated Hosts
Dedicated Hosts are physical servers with Amazon EC2 instance capacity that is fully dedicated to your use. 

You can use your existing per-socket, per-core, or per-VM software licenses to help maintain license compliance. You can purchase On-Demand Dedicated Hosts and Dedicated Hosts Reservations. Of all the Amazon EC2 options that were covered, Dedicated Hosts are the most expensive.

### Scalability

Scalability involves beginning with only the resources you need and designing your architecture to automatically respond to changing demand by scaling out or in. As a result, you pay for only the resources you use. You don’t have to worry about a lack of computing capacity to meet your customers’ needs.

If you wanted the scaling process to happen automatically, which AWS service would you use? The AWS service that provides this functionality for Amazon EC2 instances is Amazon EC2 Auto Scaling.

### Amazon EC2 Auto Scaling

If you’ve tried to access a website that wouldn’t load and frequently timed out, the website might have received more requests than it was able to handle. This situation is similar to waiting in a long line at a coffee shop, when there is only one barista present to take orders from customers.

Amazon EC2 Auto Scaling enables you to automatically add or remove Amazon EC2 instances in response to changing application demand. By automatically scaling your instances in and out as needed, you can maintain a greater sense of application availability.

Within Amazon EC2 Auto Scaling, you can use two approaches: **dynamic scaling** and **predictive scaling**.

- Dynamic scaling responds to changing demand. 
- Predictive scaling automatically schedules the right number of Amazon EC2 instances based on predicted demand.

### Example: Amazon EC2 Auto Scaling

In the cloud, computing power is a programmatic resource, so you can take a more flexible approach to the issue of scaling. By adding Amazon EC2 Auto Scaling to an application, you can add new instances to the application when necessary and terminate them when no longer needed.

Suppose that you are preparing to launch an application on Amazon EC2 instances. When configuring the size of your Auto Scaling group, you might set the minimum number of Amazon EC2 instances at one. This means that at all times, there must be at least one Amazon EC2 instance running.

When you create an Auto Scaling group, you can set the minimum number of Amazon EC2 instances. The minimum capacity is the number of Amazon EC2 instances that launch immediately after you have created the Auto Scaling group. In this example, the Auto Scaling group has a minimum capacity of one Amazon EC2 instance.

Next, you can set the desired capacity at two Amazon EC2 instances even though your application needs a minimum of a single Amazon EC2 instance to run.

The third configuration that you can set in an Auto Scaling group is the maximum capacity. For example, you might configure the Auto Scaling group to scale out in response to increased demand, but only to a maximum of four Amazon EC2 instances.

Because Amazon EC2 Auto Scaling uses Amazon EC2 instances, you pay for only the instances you use, when you use them. You now have a cost-effective architecture that provides the best customer experience while reducing expenses.

## Elastic Load Balancing

Elastic Load Balancing is the AWS service that automatically distributes incoming application traffic across multiple resources, such as Amazon EC2 instances. 

A load balancer acts as a single point of contact for all incoming web traffic to your Auto Scaling group. This means that as you add or remove Amazon EC2 instances in response to the amount of incoming traffic, these requests route to the load balancer first. Then, the requests spread across multiple resources that will handle them. For example, if you have multiple Amazon EC2 instances, Elastic Load Balancing distributes the workload across the multiple instances so that no single instance has to carry the bulk of it. 

Although Elastic Load Balancing and Amazon EC2 Auto Scaling are separate services, they work together to help ensure that applications running in Amazon EC2 can provide high performance and availability. 

### Example: Elastic Load Balancing

1. Low-demand period

Here’s an example of how Elastic Load Balancing works. Suppose that a few customers have come to the coffee shop and are ready to place their orders. 

If only a few registers are open, this matches the demand of customers who need service. The coffee shop is less likely to have open registers with no customers. In this example, you can think of the registers as Amazon EC2 instances.

2. High-demand period

Throughout the day, as the number of customers increases, the coffee shop opens more registers to accommodate them. 

Additionally, a coffee shop employee directs customers to the most appropriate register so that the number of requests can evenly distribute across the open registers. You can think of this coffee shop employee as a load balancer. 

## AWS Elastic Beanstalk (free to use)

With AWS Elastic Beanstalk, you provide code and configuration settings, and Elastic Beanstalk deploys the resources necessary to perform the following tasks:

1. Adjust capacity
2. Load balancing
3. Automatic scaling
4. Application health monitoring

- handles deployment process
- accomodates services developed using Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker
- You retain control over resources at all time
- pay only for other AWS recourses consumed to deploy
- it is autoscaling
- complete freedom to select AWS resources
- allows manual management of infrastructure
- provisions and operates the infrastructure

## AWS CloudFormation

With AWS CloudFormation, you can treat your **infrastructure as code**. This means that you can build an environment by writing lines of code instead of using the AWS Management Console to individually provision resources.

AWS CloudFormation provisions your resources in a safe, repeatable manner, enabling you to frequently build your infrastructure and applications without having to perform manual actions. It determines the right operations to perform when managing your stack and rolls back changes automatically if it detects errors.

## Messaging and Queuing

### Monolithic applications and microservices

Applications are made of multiple components. The components communicate with each other to transmit data, fulfill requests, and keep the application running. 

Suppose that you have an application with tightly coupled components. These components might include databases, servers, the user interface, business logic, and so on. This type of architecture can be considered a monolithic application. 

In this approach to application architecture, if a single component fails, other components fail, and possibly the entire application fails.

To help maintain application availability when a single component fails, you can design your application through a microservices approach.

In a microservices approach, application components are loosely coupled. In this case, if a single component fails, the other components continue to work because they are communicating with each other. The loose coupling prevents the entire application from failing. 

When designing applications on AWS, you can take a microservices approach with services and components that fulfill different functions. Two services facilitate application integration: Amazon Simple Notification Service (Amazon SNS) and Amazon Simple Queue Service (Amazon SQS).

### Amazon Simple Notification Service (Amazon SNS)

Amazon Simple Notification Service (Amazon SNS) is a publish/subscribe service. Using Amazon SNS topics, a publisher publishes messages to subscribers. This is similar to the coffee shop; the cashier provides coffee orders to the barista who makes the drinks.

In Amazon SNS, subscribers can be web servers, email addresses, AWS Lambda functions, or several other options. 

<div align="center">
  <img src="./sns.png" alt="simple notification service" width="300"/>
</div>


Suppose that the coffee shop has a single newsletter that includes updates from all areas of its business. It includes topics such as coupons, coffee trivia, and new products. All of these topics are grouped because this is a single newsletter. All customers who subscribe to the newsletter receive updates about coupons, coffee trivia, and new products.

After a while, some customers express that they would prefer to receive separate newsletters for only the specific topics that interest them. The coffee shop owners decide to try this approach.

<div align="center">
  <img src="./sns2.png" alt="simple notification service 2" width="300"/>
</div>

Now, instead of having a single newsletter for all topics, the coffee shop has broken it up into three separate newsletters. Each newsletter is devoted to a specific topic: coupons, coffee trivia, and new products.

Subscribers will now receive updates immediately for only the specific topics to which they have subscribed.

It is possible for subscribers to subscribe to a single topic or to multiple topics. For example, the first customer subscribes to only the coupons topic, and the second subscriber subscribes to only the coffee trivia topic. The third customer subscribes to both the coffee trivia and new products topics.

### Amazon Simple Queue Service (Amazon SQS)

Amazon Simple Queue Service (Amazon SQS) is a message queuing service. 

Using Amazon SQS, you can send, store, and receive messages between software components, without losing messages or requiring other services to be available. In Amazon SQS, an application sends messages into a queue. A user or service retrieves a message from the queue, processes it, and then deletes it from the queue.

To review two examples of how to use Amazon SQS, choose the arrow buttons to display each one.

<div align="center">
  <img src="./sqs.png" alt="simple queue service" width="300"/>
</div>

Suppose that the coffee shop has an ordering process in which a cashier takes orders, and a barista makes the orders. Think of the cashier and the barista as two separate components of an application. 

First, the cashier takes an order and writes it down on a piece of paper. Next, the cashier delivers the paper to the barista. Finally, the barista makes the drink and gives it to the customer.

When the next order comes in, the process repeats. This process runs smoothly as long as both the cashier and the barista are coordinated.

What might happen if the cashier took an order and went to deliver it to the barista, but the barista was out on a break or busy with another order? The cashier would need to wait until the barista is ready to accept the order. This would cause delays in the ordering process and require customers to wait longer to receive their orders.

As the coffee shop has become more popular and the ordering line is moving more slowly, the owners notice that the current ordering process is time consuming and inefficient. They decide to try a different approach that uses a queue.

<div align="center">
  <img src="./sqs2.png" alt="simple queue service 2" width="300"/>
</div>

Recall that the cashier and the barista are two separate components of an application. A message queuing service, such as Amazon SQS, lets messages between decoupled application complements.

In this example, the first step in the process remains the same as before: a customer places an order with the cashier. 

The cashier puts the order into a queue. You can think of this as an order board that serves as a buffer between the cashier and the barista. Even if the barista is out on a break or busy with another order, the cashier can continue placing new orders into the queue. 

Next, the barista checks the queue and retrieves the order.

The barista prepares the drink and gives it to the customer. 

The barista then removes the completed order from the queue. 

While the barista is preparing the drink, the cashier is able to continue taking new orders and add them to the queue.

## Serverless computing

Earlier in this module, you learned about Amazon EC2, a service that lets you run virtual servers in the cloud. If you have applications that you want to run in Amazon EC2, you must do the following:

1. Provision instances (virtual servers).

2. Upload your code.

3. Continue to manage the instances while your application is running.

<div align="center">
  <img src="./serverless.png" alt="serverless" width="300"/>
</div>

The term “serverless” means that your code runs on servers, but you do not need to provision or manage these servers. With serverless computing, you can focus more on innovating new products and features instead of maintaining servers.

Another benefit of serverless computing is the flexibility to scale serverless applications automatically. Serverless computing can adjust the applications' capacity by modifying the units of consumptions, such as throughput and memory. 

An AWS service for serverless computing is AWS Lambda.

### AWS Lambda

AWS Lambda(opens in a new tab) is a service that lets you run code without needing to provision or manage servers. 

While using AWS Lambda, you pay only for the compute time that you consume. Charges apply only when your code is running. You can also run code for virtually any type of application or backend service, all with zero administration. 

For example, a simple Lambda function might involve automatically resizing uploaded images to the AWS Cloud. In this case, the function triggers when uploading a new image. 

### How AWS Lambda works

<div align="center">
  <img src="./how-serverless.png" alt="how serverless works" width="300"/>
</div>

1. You upload your code to Lambda. 

2. You set your code to trigger from an event source, such as AWS services, mobile applications, or HTTP endpoints.

3. Lambda runs your code only when triggered.

4. You pay only for the compute time that you use. In the previous example of resizing images, you would pay only for the compute time that you use when uploading new images. Uploading the images triggers Lambda to run code for the image resizing function.

## Containerized applications

### Containers

Containers provide you with a standard way to package your application's code and dependencies into a single object. You can also use containers for processes and workflows in which there are essential requirements for security, reliability, and scalability.

To review an example on how containers work, choose the arrow buttons.

<div align="center">
  <img src="./container.png" alt="container" width="300"/>
</div>

Suppose that a company’s application developer has an environment on their computer that is different from the environment on the computers used by the IT operations staff. The developer wants to ensure that the application’s environment remains consistent regardless of deployment, so they use a containerized approach. This helps to reduce time spent debugging applications and diagnosing differences in computing environments.

<div align="center">
  <img src="./container2.png" alt="container2" width="300"/>
</div>

When running containerized applications, it’s important to consider scalability. Suppose that instead of a single host with multiple containers, you have to manage tens of hosts with hundreds of containers. Alternatively, you have to manage possibly hundreds of hosts with thousands of containers. At a large scale, imagine how much time it might take for you to monitor memory usage, security, logging, and so on.

### Amazon Elastic Container Service (Amazon ECS)

Amazon Elastic Container Service (Amazon ECS) is a highly scalable, high-performance container management system that enables you to run and scale containerized applications on AWS. 

Amazon ECS **supports Docker containers**. Docker is a software platform that enables you to build, test, and deploy applications quickly. AWS supports the use of open-source Docker Community Edition and subscription-based Docker Enterprise Edition. With Amazon ECS, you can use API calls to launch and stop Docker-enabled applications.

### Amazon Elastic Kubernetes Service (Amazon EKS)

Amazon Elastic Kubernetes Service (Amazon EKS) is a fully managed service that you can use to run Kubernetes on AWS. 

Kubernetes is open-source software that enables you to deploy and manage containerized applications at scale. A large community of volunteers maintains Kubernetes, and AWS actively works together with the Kubernetes community. As new features and functionalities release for Kubernetes applications, you can easily apply these updates to your applications managed by Amazon EKS.

### AWS Fargate

AWS Fargate is a **serverless compute engine for containers**. It works with both Amazon ECS and Amazon EKS. 

When using AWS Fargate, you do not need to provision or manage servers. AWS Fargate manages your server infrastructure for you. You can focus more on innovating and developing your applications, and you pay only for the resources that are required to run your containers.

## Difference between Lambda and Fargate

AWS Lambda and AWS Fargate are both serverless computing services provided by AWS, but they serve different purposes and are used for different types of workloads. Here's a breakdown of the differences between the two:

AWS Lambda:
1. Purpose:

Function-as-a-Service (FaaS): AWS Lambda is designed for running small, single-purpose functions or tasks that are triggered by events. It is best suited for event-driven architectures, where your code is executed in response to specific events like changes in data, user actions, or HTTP requests.
2. Execution Model:

Short-lived and Stateless: Lambda functions are short-lived and stateless. They are meant to execute quickly (with a maximum execution time of 15 minutes) and do not retain state between invocations. If you need to maintain state, you would typically use external services like Amazon S3, DynamoDB, or RDS.
3. Scaling:

Automatic Scaling: Lambda automatically scales the number of instances of your function to handle incoming requests. You don't need to manage scaling manually; Lambda will scale up and down based on demand.
4. Cost:

Pay-per-Execution: With Lambda, you only pay for the compute time your code consumes, measured in milliseconds, and the number of requests. This makes it cost-effective for workloads with unpredictable or sporadic demand.
5. Use Cases:

Event-driven tasks: Such as file processing in S3, responding to API Gateway requests, or processing messages in an SQS queue.
Automated backend tasks: Like triggering functions based on events in your application.
Microservices: Running small, modular services that perform specific functions.
AWS Fargate:
1. Purpose:

Container-as-a-Service (CaaS): AWS Fargate is designed for running containerized applications without needing to manage the underlying infrastructure. It is used with Amazon ECS (Elastic Container Service) or Amazon EKS (Elastic Kubernetes Service) to run containers in a serverless manner.
2. Execution Model:

Long-lived and Stateful/Stateless: Fargate can run both long-running services and short-lived tasks. Containers can be stateful or stateless, depending on how you design your application. You can use persistent storage like EBS or EFS if needed.
3. Scaling:

Managed Scaling: Fargate automatically provisions the necessary compute resources for your containers. You can scale your containers based on demand, either manually or through Auto Scaling policies.
4. Cost:

Pay-for-Resources: With Fargate, you pay for the vCPU and memory resources that your containers use. This makes it suitable for more predictable workloads where you need finer control over the resources allocated to your containers.
5. Use Cases:

Microservices: Running containerized microservices with a focus on portability and consistency across environments.
Batch Processing: Running batch jobs in containers that may require more resources or longer execution times.
Web Applications: Deploying web applications and APIs in containers that need to run continuously.
CI/CD Pipelines: Running containerized tasks for continuous integration and deployment workflows.
Key Differences:
Execution Model:

Lambda: Stateless, short-lived functions triggered by events (maximum execution time of 15 minutes).
Fargate: Long-lived or short-lived containers that can be stateful or stateless, with more flexibility in execution time.
Workload Type:

Lambda: Best for event-driven tasks and small, modular functions.
Fargate: Best for running containerized applications and services, whether they are short-lived tasks or long-running services.
Scaling:

Lambda: Automatically scales based on the number of incoming requests or events.
Fargate: Scales based on the number of running containers, with finer control over resources.
Pricing:

Lambda: Pay-per-execution, measured in milliseconds.
Fargate: Pay for vCPU and memory resources used by containers.
Use Cases:

Lambda: Ideal for lightweight, event-driven tasks or automation scripts.
Fargate: Ideal for running full-fledged containerized applications, microservices, or batch processing tasks.
When to Use AWS Lambda:
When you need to run small, event-driven functions that execute in response to specific triggers.
For workloads with unpredictable demand, where you only want to pay for the actual compute time used.
For scenarios where you don't need to manage servers or containers and prefer a fully managed experience.
When to Use AWS Fargate:
When you need to run containerized applications that require specific resources, such as CPU and memory.
For workloads where you want the flexibility of containers but without the need to manage the underlying infrastructure.
When you need long-running or stateful applications, and want to leverage container orchestration with ECS or EKS.
In summary, while both services offer serverless compute capabilities, AWS Lambda is better suited for short-lived, event-driven functions, whereas AWS Fargate is designed for running containerized applications that may need more control over resources and execution time.

## Amazon Lightsail

Amazon Lightsail is a simplified, cost-effective cloud platform provided by AWS. It is designed to make it easy for developers, small businesses, and individuals to deploy and manage small-scale applications or websites without needing to deal with the complexity of more advanced AWS services.

### Key Features of Amazon Lightsail:

#### Virtual Private Servers (VPS)
- Lightsail provides pre-configured virtual private servers (instances) with a fixed amount of compute, memory, and storage. These servers are easy to deploy and manage, and you can choose from a range of operating systems and application stacks.

#### Preconfigured Application Stacks
- Lightsail offers blueprints for popular applications and development stacks, such as WordPress, LAMP (Linux, Apache, MySQL, PHP), Node.js, and more. This allows you to quickly launch applications with minimal setup.

#### Simplified Management
- Lightsail provides an easy-to-use interface for managing your resources, including instances, databases, load balancers, and networking. The interface is designed to be user-friend
