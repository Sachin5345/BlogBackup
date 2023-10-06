---
title: "Understanding Variables, Datatypes and Expressions in HCL"
datePublished: Fri Oct 06 2023 06:03:36 GMT+0000 (Coordinated Universal Time)
cuid: clne7ak7j000708mhcmln14l8
slug: understanding-variables-datatypes-and-expressions-in-hcl
tags: devops, terraform, trainwithshubham, tws, terraweekchallenge

---

Day 2 - Terraweek! A road to terraform mastery

# ***<mark>Introduction</mark>***

Terraform is a flexible and reliable solution for managing resources across many cloud platforms in the infrastructure as code (IaC) space. Terraform's adaptability goes beyond the cloud, even though managing cloud resources is its main use case. In this post, we'll look at a real-world application where Terraform excels at handling local files by utilizing HCL variables, data types, and expressions.

## ***<mark>Defining the Objective</mark>***

Consider a scenario where you need to generate a local file with specific content. Instead of manually creating and updating files, we can harness Terraform to automate this task. Let's dive into the steps involved.

### **<mark>Variables in Terraform</mark>**

The use of variables is a key component of Terraform. We may parameterize our configurations using these variables, which makes them more adaptable and reusable. In our use case, we create a [variables.tf](http://variables.tf) file with the name "file\_content" as a variable:

> variable "file\_content" {
> 
> description = "Content to write to the local file"
> 
> type = string
> 
> default = "Default content if not provided"
> 
> }

The string value of this variable, "file\_content," includes a default value in the event that it is not explicitly specified during configuration.

### ***<mark>Creating the Local File Resource</mark>***

We now go to the core of our operation, where we use Terraform's "local\_file" resource to build a local file. The configuration is shown below from our [main.tf](http://main.tf) file:

> resource "local\_file" "example" {
> 
> filename = "example.txt"
> 
> content = var.file\_content
> 
> }

In this [main.tf](http://main.tf) file, we're using the local\_file resource to create a local file named "example.txt." We set the content attribute to the value of the file\_content variable using var.file\_content.

# ***<mark>How do I run this configuration?</mark>***

To use these configuration files, you'll need to initialize and apply the Terraform configuration. Here are the steps:

Step 1: Initialize Terraform in your working directory:

> terraform init

Step 2: If you need a preview of what happens when you run the terraform file, you can run:

> terraform plan

Otherwise, skip Step 2 and continue to Step 3. It is always recommended to check for changes before applying the configuration.

Step 3: Apply the configuration to create the local file:

> terraform apply

Terraform will create a file named "example.txt" in the same directory with the content specified in the file\_content variable. You can customize the content by changing the value of the file\_content variable or using different filenames as needed.

# **<mark>Writing a quick configuration for deploying an S3 bucket using AWS provider</mark>**

Let's write a simple Terraform configuration using HashiCorp Configuration Language (HCL) to create an AWS S3 bucket. We'll also add the required AWS provider configuration and test it using the Terraform CLI. Make sure you have the AWS CLI configured with the necessary credentials before proceeding.

[main.tf](http://main.tf):

Create a [main.tf](http://main.tf) file with the following content to define the AWS provider and an S3 bucket resource:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694498200087/cc64145c-236c-4350-8c87-83d7a25a49f3.png align="center")

In this [main.tf](http://main.tf) file:

We specify the AWS provider configuration with the provider block, setting the AWS region to "us-east-1." You should replace this with your desired AWS region. We define an S3 bucket resource using the aws\_s3\_bucket resource block, giving it the name "my-example-bucket" and setting its ACL to "private." I have named the bucket as "terraweek\_project\_S3\_bucket"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694498707432/e1a7f321-8a56-471a-8688-0a113de82763.png align="center")

I created a separate file called providers.tf so that I can add all the necessary providers and run them at once.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694498758657/47668545-e1e2-4601-9701-5d268af84528.png align="center")

[version.tf](http://version.tf):

Create a [version.tf](http://version.tf) file to specify the required Terraform version and AWS provider version:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694498267410/1d0cfe5c-0837-4ce3-9396-9eb16761a132.png align="center")

In this [version.tf](http://version.tf) file:

We specify the minimum required Terraform version (0.15 or higher). We declare the required AWS provider version, specifying that it should be at least version 3.0.

Usage:

Now, you can use the Terraform CLI to initialize and apply the configuration:

Initialize Terraform in your working directory:

> terraform init

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694499045475/281bcc25-2119-46e5-85c6-c5af9c649a3e.png align="center")

Check what happens if you apply this configuration using:

> terraform plan

Apply the configuration to create the AWS S3 bucket:

> terraform apply

Terraform will prompt you to confirm the resource creation. Type "yes" to proceed.

After Terraform successfully applies the configuration, it will display the output showing the resource creation status.

You can also use terraform destroy to destroy the resources created by this configuration when you no longer need them.

Remember to replace the AWS region and bucket name with your desired values. This example demonstrates the basics of creating an AWS resource using Terraform and specifying the required AWS provider version. You can extend and customize this configuration as needed for your specific use case.

That's all for day 2 folks! Happy Learning!

#TWS #Terraweek\_day2