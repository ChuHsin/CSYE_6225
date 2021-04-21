# Microservices
An Architectural style that structures an application as a collection of loosely couple servicse.

Small, and focused on doing one thing well. Autonomous.

Are a separate entity. Are deployed as isolated service. All communication betwwen services themselves are via network calls, to enforce separation between the services and avoid the perils of tight coupling.
Service Expose an API and other services communicate with it via those APIs.

## Benefits
### Technology Heterogeneity
pick right tool for the job.
### Resiliency
A service failue does not cascade into total system failure.
### Scaling
Scale on the services that need to be scaled.
### Ease of Deployment
Service deployments are independent of the rest of the components.
### Composability
designed to allow its functionality be consumed in many different ways for different purposes.
### Optimizing for Replaceability
Easy to kill a service when not needed.

## Good Service
Loose Coupling, change to one service should not require change to another
High Cohesion. related sit together

---
# Serverless Computing aka Function as a Service (FaaS)
Developer doesn't see the server.

### AWS Lambda Concepts
Function
Runtimes
Event Source
Downstream Resources
Log Streams

## Programming Model

### Handler
function AWS Lmabda calls to start execution of your Lambda function
event data as the first parameter
### Context
second parameter, your code can interact with AWS Lambda
asynchronous platform 
### Logging
writes these logs to CloudWatch Logs
logging is subject to CloudWatch Logs limits.
Log data can be lost due to throttling or, when the execution context is termindated.
### Exceptions
if you invoke the function synchronously, then aws lambda forwards the result back to the client.
### Concurrency
scale up automatically, each instance of your function handles only one request at a time.
save data to the /tmp directory for use in future invocations on the same instance.

Lambda is the web server,
OS abstractions
Stateless - application state must be stored elsewhere.

Startup Latency
takes time to set up a container and do the necessary botstrapping.

## Best Practices
### Container Re-use
sotre and reference externalized config or dependencies that your code retrieves, locally after inital execution.
limit the re-initialization of variables/objects on every invocation.
keep alive and reuse connections during a previous invocation
### Use env variables
### Control Dependencies
recommend packaging all your dependencies with your deployment package.
### Manage Deployment Package Size
minimize, will reduce the amount of time it takes for downloaded and uppacked ahead of invocation.
avoid uploading the entire aws sdk lib, pick up components of the SDK you need.
### Optimize Deployment Packages
### Reduce Complexity
### AWS Lambda Limits
allocated with a fixed amount of specific resources regardless of the memory allocation

### Benefits of Serverless computing
no servesrs to manage
continuous scaling
never pay for idle servers
reduced operational costs
### Drawbacks
Loss of Server optimizations
no in-server state for serverless faas
startup latency
vendor lockin
### Use Cases
Event Driven programming
on-demand lambda function invocation over https
scheduled events

# Email Service & Amazon Simple Email Service

Send Transactional Messages - purchase, shipping, order status, policy change

Send Notifications - timely information, system health reports, application alerts, workflow status updates.

Receive Incoming Email - 

## Amazon Simple email Service (Amazon SES)
Amazon SES becomes your outbound email server.
### Deliverability
the percentage of your emails that arrive inyour recipients' inboxed.
you need to proactively take steps to prevent issues.

### Bounce
Your recipient's receiver fails to deliver your message to the recipient, the receiver bounces the message back to Amazon SES.
#### Hard bounce
A persistent email delivery failure. Mailbox does not exist, SES doesn't retry.
#### Soft bounce
A temporary email delivery failure. Mailbox is full, too many connections, connection times out. SES retries multiple times, until stop retrying.

### Complaint
mark as spam, forwards it to the ISP
most ISPs maintian an abuse address where users can forward unwanted email messages
ISP send the complaint back to Amazon SES

### Suppression list
A list of recipient email addresses that have recently caused a hard bounce for any SES customer.
SES will treat it as a hard bounce.
you can submit a supression list removal request.

## Be Proactive
### Verification
Ensure that its senders are who they say they are.
Can verify entire domains
### Authentication
Provice evidence that you are the owner of the account and that your emails have not been modified in transit.
Two methods of authentication
SPF, DKIM
### Sender Policy Framework (SPF)

### DomainKeys Indentified Mail (DKIM)
Standard that allows senders to sign their email messages with a cryptographic key.

### Reputation
---
# Event Driven 
## Amazon Simple Notification Service
SNS is a web service that coordinates and manages the delivery or sending of messages to subscribing endpoints or clients.
2 Types of clients
- Publishers: producing and sending a message to a topic, which is a logical access point and communication channel.

- Subscribers: consume or receive the message over one of the supported protocols when they are subscribed to the topic.
  
### Common SNS Scenarios
app, system alerts, such as auto scaling group
push email and text messaging, transmit messages to individuals or groups via email or sms
Mobile push notification
Message Durability
### Fanout
A SNS message is sent to a topic and then replicated and pushed to multiple SQS queues, HTTP endpoints or emails. Allows for parallel asynchronous processing.

## Amazon Simple Queue Service SQS
decouple and scale microservices, distributed systems, and serverless applications
send, store and receive messages between software components at any volume, without losing messages or requiring other services to be available.

Two types of mesage queues
### Standard Queues
Unlimited Throughput
At least one processing 
Best-Effort Ordering, messages mighe be delivered in an order different from which they were sent.

### FIFO Queues
High Throughput

Exactly Once Processing

First In First Out Delivery


----
## Assignment Workflow

### Infra
Create IAM role for Lambda Execution


### Webapp
API create a book -> post a message on SNS topic 
SNS message contains
Book id, user's email address
HTTP link to the book
**IAM policy** for publish on SNS
clear~  [16:19 Apr 5th]

### SNS

SNS notification will invoke Lambda function,

### Lambda Function
 Lambda function will send email to the user with SES.

 Terraform create aws_lambda_function
 Terraform create IAM role for lambda_function and SNS permission
 Terraform create Lambda subscription for sns topics

CodeDeploy
1. update lambda function
2. publish version
3. get the version number from output
4. appspec content to use new appspec

DynamoDB for duplicate message
store MessageID in DynamoDB,
lambda function check if MessageID already existed before sending SES

EC2 Service Role DynamoDB
### SES
Sending email to the user.

### ENV process
profile - for 
run profile - for the http link of SNS

### QA
prod account SES
