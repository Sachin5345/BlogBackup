---
title: "Jenkins: The OpenSource CICD weapon for a better  operation of your infrastructure"
datePublished: Wed Mar 06 2024 17:53:39 GMT+0000 (Coordinated Universal Time)
cuid: cltg3l60q000d08jrhmby6pnc
slug: jenkins-the-opensource-cicd-weapon-for-a-better-operation-of-your-infrastructure
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709747542710/f67d5367-a4a6-4632-b26f-d3cb3452fb8f.png
tags: devops, jenkins, how-to-install-jenkins, cicd-jenkins-goal

---

## Introduction to Jenkins and its Benefits

Looking to streamline your software development process? Jenkins is here to save the day! This powerful automation tool is a game-changer for teams looking to enhance their continuous integration and delivery practices. In this blog post, I'll guide you through the process of installing Jenkins on an EC2 instance on AWS. Let's dive in and unleash the full potential of Jenkins together!

## Setting up an EC2 Instance on AWS

Setting up an EC2 instance on AWS is the first step towards leveraging the power of Jenkins for your continuous integration and deployment needs. To begin, log in to your AWS account and navigate to the EC2 dashboard. Click on "Launch Instance" to start the instance creation process.  
  
Next, choose an Amazon Machine Image (AMI) that suits your requirements. Select an instance type based on the computational resources you need for running Jenkins smoothly. Configure security groups to control access to your instance by defining inbound and outbound rules.  
  
After configuring storage options, review your settings and launch the EC2 instance. Make sure to create or use existing key pairs for secure access via SSH. Once launched, note down the Public DNS or IP address for connecting to your EC2 instance.  
  
With these steps completed, you are now ready to proceed with installing Java and setting up Jenkins on your newly created EC2 instance!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709739682799/8de7536c-d24a-45f9-917a-8ea898f9bb4c.png align="center")

Let's connect to this machine now...

# SSH into the EC2 instance

The command to connect or ssh into this instance is simple.

> ssh -i &lt;keypair name&gt; &lt;username@publicip address of the instance&gt;

Since the IP address of the machine that I created was 34.228.30.172, the user name was ec2-user (since it was Amazon Linux), and my keypair name was jenkins.pem, my SSH command turned out to be:

> ssh -i jenkins.pem ec2-user@34.228.30.172

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709739845208/d541643d-e0cf-40c2-bd24-b78efc2de9aa.png align="center")

Let's update this EC2 instance now. Run the command below:

> sudo yum update

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709740033921/9661a5d3-1d81-4c55-898a-d32bafe7a10b.png align="center")

Since my EC2 instance was already on the newest version with all the updates installed, the command line displayed me a message that there was "Nothing to do", else this command would run a couple of checks and install all the dependencies.

## Installing Java on the EC2 Instance

So, you've set up your EC2 instance on AWS and now it's time to get Java installed. Java is a key component for running Jenkins smoothly on your server.  
  
To install Java on your EC2 instance, you can use the package manager specific to your Linux distribution. For example, since I was using the Amazon Linux, I ran the command `sudo dnf install java-17-amazon-corretto -y`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709740364364/7183c592-a1bc-4119-a263-169380b7cdeb.png align="center")

Once Java is successfully installed, make sure to verify the installation by running `java -version` in the terminal. This command should display the version of Java that was just installed.  
  
Now that Java is ready to go, we can move forward with downloading and configuring Jenkins on our EC2 instance for seamless automation workflows!

## Downloading and Configuring Jenkins

Now that you have your EC2 instance up and running with Java successfully installed, it's time to move on to the next step: downloading and configuring Jenkins.  
  
Head over to the [official Jenkins website](https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/#installing-and-configuring-jenkins) and download the latest version of Jenkins. Once the download is complete, SSH into your EC2 instance and navigate to the directory where Jenkins was downloaded.  
  
Next, run the command to start Jenkins using Java; this will initiate the installation process. Make sure to follow any prompts or instructions that may appear during installation. Here are the steps that I took to install Jenkins:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709740798556/1cdd73f7-8c41-40ea-9a0d-86d06dac9e8d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709740841099/28198b6f-dc74-4915-8cc4-c71807ece3c6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709740878051/47876e77-6050-49a0-b179-1f9ca9e8ea82.png align="center")

## Start the Jenkins and enable the service

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709740927688/85c43b97-3a17-40a0-9ef8-144337b86c21.png align="center")

After successful installation, open a web browser and access Jenkins by entering your EC2 instance's public IP address followed by port 8080 (e.g., [http://your-ec2-ip-address:8080](http://your-ec2-ip-address:8080)). You will be prompted to enter an initial admin password generated during setup - follow instructions on-screen.  

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709740977623/e252944f-943a-4301-8d17-583a0a0028b7.png align="center")

Now run the command below to see the admin password for the first login:

> sudo cat /var/lib/jenkins/secrets/initialAdminPassword

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709741059784/5f3c9e32-00d0-4409-8c04-162865182230.png align="center")

Once you enter the admin password on the Unlock Jenkins page, you will be able to see this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709741096103/34646af3-b88b-4cd3-93c3-ece24c880d4b.png align="center")

I selected the first option "Install suggested plugins":

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709741126446/8427413f-3afd-4221-9d1b-ffbbec326e5e.png align="center")

Upon successful login, configure basic settings such as creating an admin account and selecting plugins for additional functionalities.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709741158916/d5933209-7f1f-4b81-b7d9-522e318dc99c.png align="center")

Ignore the warning message in the screenshot, as that email address was rectified.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709741168621/7fa88c90-9cd1-4420-97eb-0817258c9d6a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709741181928/fca0ad47-fa9e-4813-a314-812e456871e6.png align="center")

And there you have it—Jenkins is now downloaded and configured on your EC2 instance!

## Conclusion and Next Steps

Installing Jenkins on an EC2 instance on AWS opens up a world of possibilities for continuous integration and continuous delivery. With Jenkins, you can automate your software development processes, increase productivity, and ensure the quality of your codebase.  
  
As a next step after setting up Jenkins on your EC2 instance, explore the various plugins available to customize and enhance its functionality. Additionally, consider integrating Jenkins with other tools in your development pipeline to further streamline your workflows.  
  
By leveraging the power of Jenkins and AWS together, you can take your software development practices to the next level. Stay updated with best practices in utilizing Jenkins for CI/CD pipelines to continually improve efficiency and quality in your projects.

Oh yes!! I forgot to tell you the most important thing: if you want to continue learning about Jenkins, like creating jobs, setting up pipelines, etc., keep the EC2 instance running. Otherwise, if you just want to learn how to install Jenkins, please make sure that you terminate the instance to avoid unnecessary bills.

Happy Learning!