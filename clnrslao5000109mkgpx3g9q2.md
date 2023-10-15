---
title: "The ECR-Lambda Story"
datePublished: Sun Oct 15 2023 18:20:49 GMT+0000 (Coordinated Universal Time)
cuid: clnrslao5000109mkgpx3g9q2
slug: the-ecr-lambda-story
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697393001515/a89cc336-8cfb-4c1b-b0ee-84889885e952.png
tags: lambda, docker, serverless, aws-ecr, containerregistry

---

# Introduction

Customers now have more options for packaging formats thanks to the addition of Lambda support for OCI container images. The event-driven runtime model and cost-savings benefits of AWS Lambda are now available to developers, who can still benefit from the predictability and control provided by a container-based development and deployment cycle

# Understanding the ECR

An entirely managed Docker container registry service is offered by Amazon Web Services (AWS) under the name Amazon Elastic Container Registry (Amazon ECR). Developers can use it to manage, deploy, and store Docker container images. It is simpler to create, store, and deploy containerized apps because to ECR's strong integration with other AWS services.

# Key Features and Aspects of ECR

### **Private Docker Registry**

You can store your Docker images using the secure, private Docker container registry offered by Amazon ECR in a highly available, scalable architecture.

### **Integration with Amazon ECS and Kubernetes**

It is simple to deploy and manage containers using these orchestration services because to ECR's seamless integration with Amazon Elastic Container Service (ECS) and Kubernetes.

### **Security and Access Control**

Using AWS Identity and Access Management (IAM) policies, ECR enables you to restrict access to your container images. To limit who can push, pull, or manage photos within your registry, you can specify granular permissions.

### **Scalability and Availability**

To satisfy the needs of your containerized applications, ECR scales automatically. Your container images will always be accessible thanks to the high availability it offers across several AWS Availability Zones.

### **Lifecycle Policies**

With the help of ECR's lifecycle policies, you may automatically remove outdated or useless pictures. This guarantees that only pertinent photographs are kept and lowers storage expenses.

### **Image Vulnerability Scanning**

ECR offers image vulnerability scanning through an integration with Amazon Inspector. You can do this to find and reduce any potential security issues in your container images.

### **Encryption**

ECR supports encryption both at rest and in transit, ensuring the security of your container images and data.

### **Docker CLI Integration**

Developers are able to push and pull images using well-known Docker commands thanks to ECR's seamless integration with the Docker CLI.

### **Versioning**

Container image versioning is supported by ECR. A distinct version identification is automatically assigned to each new image sent to the registry.

### **Logging and Monitoring**

ECR offers thorough logging and monitoring tools. You may set up CloudWatch Alarms, keep an eye on registry-level events, and learn more about how people use and access images.

### **Cost-Effective**

ECR offers a pay-as-you-go pricing model, ensuring that you only pay for the storage and data transfer you use.

When I started learning more about DevOps, ECR, EKS, ECS, etc., something struck my mind! Yes, I did an academic project with Great Learning with these things on the go. It's a great time to rewind some ECR, Docker, and Lambda concepts and how these can work together. There are multiple ways to perform this project. If you are a DevOps pro and want to use Terraform to create this infrastructure, you sure can!! It will all happen in one go (😉provided all the configuration written will be correct).

# Architecture

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697393122317/8760de45-9ece-45e8-bf51-f9f5305c9e2e.png align="center")

# The Process

[Here](https://github.com/Ghatodghachh/ECR-Lambda.git) is the link to access the repository for the files necessary to perform the same project.

1&gt; Setup an EC2 instance with the below configuration:

Base OS / AMI: Amazon Linux (ami-041feb57c611358bd)

VPC: Default VPC

Instance type: t2.micro

2&gt; I had created a profile on IAM in AWS with administrator access earlier, but you can create one now with the same role and I named the role as LabInstanceProfile

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697365684654/7e237ed2-9e0d-4ade-a083-4c6ffd2476b4.png align="center")

3&gt; Now, once this IAM role is created and we have the instance in the running state, attach the IAM role to the instance using the options "Actions &gt; Security &gt; Modify IAM role".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697365840114/35dca905-af4e-4142-ab36-1ffa8a71e1ce.png align="center")

4&gt; I had the zip folder for the project under the folder structure Desktop &gt; Devops Tasks. So I changed my working directory to the same and checked if all the files were present using the cd and ls commands...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697366261668/467ce935-ad36-4c13-a0d0-fd8221bb3287.png align="center")

Great!! Now all that we need to do is ensure that the key to ssh into the EC2 instance and the OCI folder are in the same folder. So, I just moved it 😁

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697366657925/3e1ae455-8fd5-4e3d-a79a-1fa119e73f58.png align="center")

5&gt; Now, copy the OCI.zip folder into the EC2 instance, specifically under the /home/ec2-user path:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697366809601/c6b872e1-35ba-4cd0-9d10-6a023f9c48ed.png align="center")

Let me break that command for a better understanding:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697367545490/cd7751ef-94dc-4cd8-997b-83adec5dd561.png align="center")

6&gt; ssh into the instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697367705916/128c71c1-ea2c-47d2-a161-735d5f163f5f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697367774199/260845d0-bfb6-489d-a86a-449deb22292b.png align="center")

7&gt; Now update the machine and install the unzip utility using the below commands:

> sudo yum update
> 
> sudo yum install unzip

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697367962111/791b3b5f-d111-4730-badd-ddfff3dcecea.png align="center")

8&gt; We are ready to unzip the folder and check for the contents in OCI folder.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697368350908/63e7ec4b-59be-4dcc-b076-7cb6ee737196.png align="center")

9&gt; Great! Now that the contents have unfolded, let's see what is inside the docker file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697368499009/670bc028-939a-45c2-84a9-4be5dc188078.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697368457872/0ead2992-118c-4f21-b646-559ce34ea510.png align="center")

All the dockerfile is doing is installing the requirements, which are detailed in the requirements.txt file, copied from the content folder.

10&gt; The next step is to install Docker to ensure that we can run Docker-related commands. So we can run the below commands to install Docker and start the Docker service. Once done, check the status.

> sudo yum install docker
> 
> sudo systemctl start docker
> 
> sudo systemctl status docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697370126190/c5203c47-9d92-45af-8ef9-b89a4692b00c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697370290487/fcde5a83-f579-4db6-9006-65cc841a8b5c.png align="center")

11&gt; Start the docker service and ensure that the permissions are set right

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697370481889/6033c8fc-9df8-45d4-8557-05c9dc98c7bf.png align="center")

12&gt; At this point, ensure to logout of the session and connect back so that you can run docker commands without any issues

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697370670848/bc543865-7c32-42f1-95e7-4745ebb0ad00.png align="center")

13&gt; Now is the time to install AWS CLI

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697370807271/54f2f3f6-d963-47d9-928f-f6880582b674.png align="center")

Since I already had it installed on my machine, I was shown a message "Nothing to do."

14&gt; Configure the AWS CLI with the defaults using

> aws configure

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697370928180/4870e58c-78bf-4813-9be1-7c6bddc70f37.png align="center")

> Note: Set everything to default to ensure that there are no boundaries for the CLI and the account to execute.

15&gt; Time to build the Docker image!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697371130815/02d4424c-ace4-4d01-b28b-8eb87da79cfc.png align="center")

Boom!!! The Docker image is now built.

16&gt; Time to check the images

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697371296999/fb3916e8-7e88-419d-8ca9-b63bc0742414.png align="center")

17&gt; Navigate to the ECR service under the homepage of AWS.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697371416203/7aeed2ef-f8b4-4c41-be03-cc03fbfbc66f.png align="center")

18&gt; Click on "**Get Started**" under the "**Create a repository**" section. You can also do this using the Hamburger menu and selecting **Repositories**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697371594823/c1351857-7cdb-4792-9b6f-cfe316f3e0f4.png align="center")

Provide the private repository name. I named mine to be "lambda\_ecr"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697390614315/cea01552-d8fa-49e9-9523-386e24dcfb09.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697390700918/e764d230-1b49-4d94-b378-fcefe48ff5cd.png align="center")

19&gt; Once the repository is created, we can start using the push commands to push the image to the repository we created. Click on the "View Push Commands", to view the commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697390805083/a2ad8c3b-743c-412e-ae14-3ab1b49f625b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697390985922/68cb9902-c151-4a3e-a689-4478034222d2.png align="center")

Follow the set of commands and the process shown to upload the image to the repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697390965951/f45cd6c0-ea31-4d0a-bdb2-c3043beb34b6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697391104375/e8a9ad4e-913c-49fe-9f38-12a684a9afb6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697391198641/29a536d5-a797-41c7-985e-46995d71d2f0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697391287721/e051b2b3-f88a-4352-b2fa-10c78a278a2b.png align="center")

On executing all those commands, the image must now be on the ECR repository that we created. Let's quickly check it out

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697391500473/33fc786a-832d-4133-b0c5-8881c79d3028.png align="center")

Well!! there is our image with the tag as latest😎😎

20&gt; Time to build the Lambda function now. Search for the "Lambda" service from the console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697391718153/a9a026bd-12d9-489b-b286-0abac4807e2f.png align="center")

21&gt; Click on the "Create function" option

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697391823620/63230a7f-61de-40b7-8aef-d3d3fd780772.png align="center")

22&gt; We would need a container image to be deployed so we will choose the "**container image**" option from the list

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697391940681/0a8b8227-1286-4d2f-b581-bed0095d8e53.png align="center")

Fill in the details.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697392157275/adbaa6b6-3627-46fe-a0e9-3c47f15819ed.png align="center")

Once this is done and we select create function, the lambda service starts building

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697392256207/634d2150-5137-4b5e-8975-4b70de67498a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697392300250/5748c688-224b-45c6-a6ff-53c82ed59837.png align="center")

22&gt; Move to the "Test" tab, provide the event name, and then click on "Test".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697392528146/a7fd7471-5042-4931-92d2-f4789d46768f.png align="center")

That's all... This execution will trigger the container we just built😎😎😎!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697392701991/8dfa92e0-8582-4ec8-b4c9-e61af30fba2f.png align="center")

After all the execution, **please make sure you delete all the resources you created to avoid the bill.**

# Conclusion

By offering a safe, scalable, and fully managed container registry service, Amazon ECR makes managing Docker containers easier. Because it offers easy connectivity with other AWS services, it is especially helpful for businesses using containerized applications in AWS settings. ECR is an easy way to store Docker containers for an organization, and when integrated with Lambda functions, this can be a fantastic tool to deploy configurations quickly.