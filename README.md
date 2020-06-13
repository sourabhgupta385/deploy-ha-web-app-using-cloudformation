# Deploy a high-availability web app using CloudFormation
This is one of the project in Udacity Cloud DevOps Engineer Nanodegree.

## Project Overview
Assume that one company is creating Instagram like application. Developers have developed the code and pushed the code into the S3 bucket on AWS. Now the task is to create the infrastructure for deploying that application in an automated way using CloudFormation following the best practices and once infrastructure is ready, deploy that application code onto that HA infrastructure.

## Project Files

- `/scripts`: This folder contains script to create, delete and update CloudFormation stack.
- `architecture-diagram.jpg`: This describes the architecture diagram of this project.
- `index.html`: This is main html file of application.
- `network-params.json`: Parameters file for network cloud formation stack.
- `network.yml`: CloudFormation template for creating networking resources for this project.
- `servers-params.json`: Parameters file for servers cloud formation stack.
- `servers.yml`: CloudFormation template for creating servers for this project.

## Project Setup

- Create networking resources using cloud formation template.
```
$ scripts/create.sh udagram-network-stack network.yml network-params.json
```
-   Following resources are created after executing above command:
    -   VPC
    -   Subnets
    -   Route Tables
    -   Routes
    -   Internet Gateway
    -   NAT Gateways
- Create servers for Udagram App which pulls source code from S3 bucket automatically while starting.
```
$ scripts/create.sh udagram-servers-stack servers.yml servers-params.json
```
-   Following resources are created after executing above command:
    -   Security Groups
    -   IAM Role, Policy, Instance Profile
    -   Launch configuration
    -   Auto Scaling Group
    -   Load Balancer
    -   Target Group
- Once the above steps are complete, you can find the URL of application in the outputs section of `udagram-servers-stack` CloudFormarion stack.
