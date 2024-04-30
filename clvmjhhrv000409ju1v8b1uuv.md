---
title: "The CICD pipeline with Jenkins"
datePublished: Tue Apr 30 2024 15:24:43 GMT+0000 (Coordinated Universal Time)
cuid: clvmjhhrv000409ju1v8b1uuv
slug: the-cicd-pipeline-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714490483809/f462e974-5176-473d-b493-26f1f0e98bfc.png
tags: docker, security, sonarqube, devops, devsecops, trivy, cicdpipe

---

In one of my previous blogs, I wrote about Jenkins and how it can help in creating CICD, which enhances the quality of the product and the way it is deployed in one of my previous [blogs.](https://hashnode.com/post/cltg3l60q000d08jrhmby6pnc)

This article details a project that employs the concepts of Jenkins, Sonarqube, and Trivy and ways to deploy and configure them in AWS. Let us begin.

Before we begin, there are some basic points we need to know about these tools.

# SonarQube

![SonarQube Analysis](https://media.licdn.com/dms/image/D4D12AQHzE1oIZYll5w/article-cover_image-shrink_720_1280/0/1674467662411?e=2147483647&v=beta&t=GS0gLQDx5zjLsfWlJUHbC08_mxhfyom4VJJVTROFoKY align="left")

An open-source tool called SonarQube is made to constantly check the quality of code in software projects to find errors, security holes, and bad code. Since its creation by SonarSource, it has grown in favor among programmers and companies that want to keep their codebases in top condition.

Here's an overview of its key features and functionalities:

## Code Quality Analysis

Programming languages written in Java, C#, JavaScript, Python, and other languages are all analyzed by SonarQube. To identify problems that can affect the code's quality, maintainability, reliability, and security, it compares the code to a set of predetermined standards.

## Static Code Analysis

Static code analysis is what it does; it looks at code without running it. Early in the development process, this analysis aids in locating possible bugs, security flaws, and other problems.

## Code Smell Detection

Code smells, or specific patterns or structures in code that can point to a more serious issue or inefficiency, are recognised by SonarQube. Code that is too complicated, redundant, or uses inconsistent coding practices are a few examples.

## Security Vulnerability Detection

SonarQube not only identifies problems with code quality but also security flaws in the source. It looks for typical security flaws such exposed sensitive data, cross-site scripting (XSS), and injection attacks.

## Integration with Development Tools

Popular development tools including IDEs (Integrated Development Environments) like Eclipse, Visual Studio, and IntelliJ IDEA, as well as CI/CD (Continuous Integration/Continuous Deployment) pipelines, are all integrated with SonarQube. This makes it possible for developers to get feedback on problems and the quality of their code right within their development process.

## Customizable Rules

Although SonarQube has a default set of rules, customers can expand and modify these rules to better fit their own project objectives, best practices, and coding standards.

## Reporting and Dashboards

It offers thorough reports and dashboards that give historical trends in code quality. These reports can be used by developers and project managers to monitor work progress, set priorities, and make data-driven choices that will enhance the quality of the code.

## Support for Multiple Languages

SonarQube is appropriate for a variety of software development projects because it supports a large number of programming languages.

# Trivy

![Using Trivy to discover vulnerabilities | by Bharat Mallavarapu | Medium](https://miro.medium.com/v2/resize:fit:1078/1*eS-YJ22e7UZY_0nUYM_jXw.png align="left")

An open-source vulnerability scanner for OS systems, package managers, and containers is called Trivy. Its purpose is to assist security teams and developers in finding holes in container images and making sure their software stack has secure components.

Here's an overview of Trivy's key features and functionalities:

## Container Image Scanning

Trivy's main objective is to find vulnerabilities in container images. It investigates a container image's layers, looking for known vulnerabilities in the installed dependencies and packages at each level.

## Support for Multiple Artifact Types

Although Trivy is frequently used for scanning container images, it may also be used to scan other types of artifacts, including operating system packages (like RPM and DEB) and package managers specialized to a given language (like npm and pip). Because of its adaptability, users may conduct thorough vulnerability scans on various software stack components.

## Integration with CI/CD Pipelines

Software development processes can automate vulnerability scanning by integrating Trivy into CI/CD pipelines. By doing this, it is made sure that vulnerabilities are found early in the lifecycle and fixed before deployment.

## Database of Vulnerabilities

To find known vulnerabilities, Trivy uses a variety of community-maintained sources as well as vulnerability databases like the National Vulnerability Database (NVD). To make sure it recognizes the most recent security threats, it updates its vulnerability database regularly.

## Fast Scanning

Because of its speed, Trivy can complete scans rapidly, even on big container images. This reduces the overhead associated with integrating vulnerability screening into development operations.

## Detailed Reports

Trivy creates thorough reports listing all of the vulnerabilities discovered in the analyzed artifacts after a scan is finished. Each vulnerability's details, including its severity rating, impacted packages, and suggested repair actions, are usually included in the reports.

## Customizable Policies

Trivy allows users to create bespoke vulnerability scanning policies depending on their specific needs and risk tolerance. This adaptability allows organisations to modify the scanning process to their specific security policies and compliance criteria.

## Open-Source and Community-Supported

Trivy is an open-source project with a vibrant community of contributors and users. This community-driven development strategy ensures that Trivy remains current and responsive to the changing threat scenario.

# Jenkins

![Your Jenkins Belongs to Us Now: Abusing Continuous Integration Systems](https://www.crowdstrike.com/wp-content/uploads/2018/10/Jenkins-blog-image-1.jpg align="left")

I wrote about this tool already [here](https://hashnode.com/edit/cltg3l60q000d08jrhmby6pnc).

# Docker

![A Suggestion on Docker Whale Logo RE:"The Wave" - General Discussions -  Docker Community Forums](https://global.discourse-cdn.com/docker/original/2X/8/8351f7d7a14db3035713b6ef8fdd7484088e03fb.png align="left")

Docker is a platform that lets developers create, deploy, and operate applications in containers. Containers are lightweight, portable, and self-sufficient environments that contain all of the components (code, runtime, system libraries, and dependencies) required to run an application.

Here are some key aspects of Docker:

## Containerization

Docker employs containerization technology to encapsulate applications and their dependencies. This enables programs to run reliably across several settings, from development to production, without being influenced by variances in the underlying infrastructure.

## Docker Engine

Docker's key component is the Docker Engine, which is in charge of container creation, execution, and management. The Docker Engine is made up of a daemon process named dockerd, a REST API for communicating with the daemon, and a command-line interface (CLI) tool called docker that allows users to communicate with Docker.

## Docker Images

Containers are built from Docker images, which are lightweight, standalone, and portable packages that include everything required to run an application, such as the application code, runtime, libraries, and dependencies. Docker images are created using a Dockerfile, which is a text file that includes instructions for creating the image.

## Docker Hub

Docker Hub is a cloud-based registry service offered by Docker that allows users to locate, distribute, and save Docker images. It functions as a central repository for Docker images, allowing users to quickly download images from public repositories or publish their own images, either privately or publicly.

## Docker Compose

Docker Compose is a tool for creating and managing multi-container Docker apps. It defines the services, networks, and volumes that comprise an application using a YAML file, allowing complicated application architectures to be defined and managed as a single entity.

## Orchestration with Docker Swarm and Kubernetes

Docker Swarm and Kubernetes are container orchestration solutions for deploying, scaling, and managing containerized applications across a cluster of servers. Docker Swarm is the native orchestration tool for Docker, whereas Kubernetes is a Google-developed open-source platform.

## Portability and Consistency

Docker containers are highly portable and consistent across a variety of contexts, making it simple to create, test, and deploy apps reliably. Developers can build and test programs locally in Docker containers before deploying them to production with no modifications, assuring consistency and stability.

# The concept of Webhooks

Webhooks are a way for web applications to communicate with each other in real time. They are a mechanism for automatically sending notifications or data from one application when a specific event occurs to another application, usually through HTTP POST requests.

Great!! Now that we know what tools are we using, let's start with the project. To begin with, we need an EC2 instance that can manage all these workloads, so I would say to use the below combination (make sure that you finish the project in one go and delete the infra once this is complete since the instance is not in the free tier configuration).

> EC2 Configuration:
> 
> Type: t2.medium
> 
> Base Image: Ubuntu (I have used ami-080e1f13689e07408)
> 
> Storage: 30GiB

While configuring the security groups, open the ports 8080(for docker), 9000(for SonarQube), 22 (for SSH), and 80 and 443(for HTTP and HTTPS).

> Pro-tip: Use an Elastic IP address so that in case if you stop your instance between the project, even if the IP address of the instance changes, the elastic IP keeps the configuration same when you configure the applications.

Let's begin configuring the instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714048941356/b2625528-e781-40a3-b1e3-5f42f7397e68.png align="center")

Let's configure the ports in the security group

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714048951210/d5369233-bb57-4e83-ac20-457fd244875a.png align="center")

Create an Elastic IP and attach it to the EC2 instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714049076182/6d4681a3-24b1-4331-b40e-7f5334550e92.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714049171716/bb1a88b1-ef1e-4974-b35f-504a0911b622.png align="center")

Now let's connect to the EC2 instance using the cloudshell (you can ssh into the instance too 😎😉 but since I configured my instance without the keypair, I used cloudshell) and elevate the privileges.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714049316808/5b6726ca-188e-400f-ba2b-d0eacff49639.png align="center")

Let's update the instance using:

> apt update -y

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714049330922/d26fb344-b758-4424-8528-1c380fe10d59.png align="center")

Let's upgrade our configuration inside the instance using:

> apt upgrade -y

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714049430961/85b0b2a7-04b9-45d8-a30c-22e794e901d7.png align="center")

Alright! Now we are ready for phase 1.

# Phase - 1: Installing Jenkins

We need to install Java first, which is a prerequisite for installing and configuring Jenkins. You can visit the Jenkins documentation before you decide on the Java version.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714049529546/7c28a20c-d895-431b-9001-8d2a1c4a6e21.png align="center")

Every 12 weeks, an LTS (Long-Term Support) release is selected from the stream of regular releases as the stable release for that time period. It can be installed via the Debian-stable apt repository. Let's install the same and then update our instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714099731153/8598fae5-b0ed-4233-a603-8951ddc346da.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714099958583/ba2af594-5548-4917-be95-29a361888643.png align="center")

Once the machine is updated using the apt update command, we are ready to install Jenkins. Let's install Jenkins now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714100033362/6891d638-51c6-4bb8-a6f5-569db5d33a0f.png align="center")

Once this is installed, it is now time to enable the Jenkins service and start it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714139697761/f1894ae9-6d0b-48eb-a356-a61c04843dd1.png align="center")

Great! Once all this is done, the only thing left is to add the plugins.

Let's configure Jenkins

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714139771236/370cb0f8-883a-49cd-96e9-2d9007ef8530.png align="center")

since we are already in elevated user mode, just do a

> cat /var/lib/jenkins/secrets/initialAdminPassword

to view the initial config password.

Once you get the admin password, configure the admin account and also install the suggested plugins.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714139951972/c5cf9e6b-40d1-4091-a21e-37d3440b0603.png align="center")

Once all this is complete, you should be able to see the Jenkins dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714472913045/7c8ed677-10c5-4fa0-9bc8-27f8c91cdc5d.png align="center")

Let's configure the plugins now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714472918320/72479402-5fa9-4f32-8b0a-e8180084e45f.png align="center")

Using the available plugins on the left-hand pane, we can search for the required plugins. In our case:

1&gt; SonarQube Scanner

2&gt; Sonar Quality Gates

3&gt; Sonar Gerrit

4&gt; SonarQube Generic Coverage

5&gt; JFrog

6&gt; Quality Gates

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714473135432/93ade2f2-1c63-4d11-9745-9b3c6080a2a2.png align="center")

Once these are installed, it is now time to configure our pipeline. Navigate to the job and click on the "**Pipeline**" on the left. Configure the rest of the options:

> Definition: Pipeline script from SCM
> 
> SCM: GIT
> 
> Repository: &lt;your GIT repository URL where you are hosting the application code&gt;

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714473186020/c8315f0e-29f0-434c-aca4-7b95d244fdea.png align="center")

Click on Save once these are set.

# Phase - 2 Installing Docker

Let's install the dependencies first

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714473711588/e179f325-0bd9-4a9d-95e9-74bc6e77cb74.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714473785176/56ac00e7-7af5-4567-bbad-4510d53c3a35.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714473791422/d6616566-5204-4895-9459-c5a16124944e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714473759494/cd40c9c5-ce29-4291-8935-97078e335fe0.png align="center")

> Pro-tip: Change the permissions for the docker.sock to avoid any issues while running your code for containerizing your application.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714473784875/d7b1a143-1188-48aa-9c9c-4c3284ecf176.png align="center")

# Phase - 3 Running SonarQube

Let us make the Docker run the SonarQube application on port 9000

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474121871/fdd38a5f-6f14-424c-9708-b00ff4b9b2f1.png align="center")

Great! Now since Docker is running the SonarQube application it's time to test our implementation and configure SonarQube application

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474270132/f99c53b7-8531-42cf-a151-d0616873bcc4.png align="center")

## Configuring SonarQube Application

You will first be required to reset your password after accessing the SonarQube application's login page, where the default username and password are admin. Once you have successfully logged in, the SonarQube application's homepage appears.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474669645/1bbc927b-5a15-46a5-af93-dfa089bd806a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474669645/dab38b84-80f6-45bc-b384-7665d283b732.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474677033/91f0c7bc-3b03-4f17-a07a-6ad309e6c728.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474744789/2b1c22f8-880f-4256-bf77-a0e9df0e18bf.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474802672/a0a1e2ee-2ab7-4627-840e-10b43a397531.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474821831/0a96979f-17fe-4722-b832-088ff93c3305.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474832513/7b3b443d-9b0b-456a-b93a-2a27cdb1d143.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714474846368/7827a6b9-fb68-4a34-ba14-27433ead3263.png align="center")

Fantastic! We were able to construct a webhook for the sonar application with the help of that little configuration.

# Phase - 4 Time to install and configure Maven and Trivy

As with all installations, you just need to run:

> apt install maven -y

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475159036/3b89caa9-6e20-4698-9478-5465e79bfa4e.png align="center")

We need to install trivy so that we can inspect and find the vulnerabilities in the docker container that will be used in the pipeline. Here is how you install it:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475231361/89aa39e5-e496-469c-8d52-8af367402e20.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475276993/d9f712ca-ff77-4651-9a44-6fbf832d41c0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475266850/1817a018-7348-4ce1-9e0d-d7e3d812f3b4.png align="center")

If you have completed it until now, well done!! It is time for the final phase, configuring all these on Jenkins and building the pipeline.

# Phase - 5 Configuring the Tools installed on Jenkins

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475564751/e82e97fd-3c50-4340-96df-b6b3ff212ae3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475576561/8539cb8f-e891-49dd-b47a-ef575b402c16.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475588385/eea78d24-31d9-497f-858c-3853699bae67.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475620948/65ed7935-474b-40a8-bedf-0e936cb847f0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475601604/54103c5b-a750-4a68-ad44-f00751b1c59c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475644710/81570221-5ca3-485e-ae9b-4f6f89e9ed07.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475660178/15de48fa-03db-4823-a18b-b713516b02c8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475678455/ca9d646a-d583-465b-822d-20df3a33fce4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714475721287/515c5780-9d8b-4148-b00b-ada98a448efb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714477644398/ca44867e-f6df-4454-98a1-bf7e01023461.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714477652047/cd14ffc4-de16-4916-8bdd-15ccdba1a66e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714477672661/6987eae9-a9dc-4849-8b52-ff61b469c876.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714477761310/9acde124-bcff-4ab3-b92a-bad19b861c1a.png align="center")

The pipeline state shows failed in my case since I used the incorrect credentials for docker to showcase how the pipeline status looks. I later rectified the same and re-built the pipeline and it started showing green.

# Logging/Monitoring

While all this process is going on, we can have a look on various logs. Here are a few snapshots for reference from Jenkins build, SonarQube and Trivy

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714477914785/9f94b055-9455-47d1-af71-c1a809486c24.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714477963435/17cb59d5-3366-4b1f-87ea-dbf5d01c3744.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714477929198/788671de-411e-46dd-a0c6-38334f14bcfa.png align="center")

# Conclusion

So by doing all this what do we understand? The answer to this question is the importance of building CICD pipelines and integrating various tools with it. In a nutshell, CI CID pipelines are absolutely useful in deploying and automating tasks that can take a long time to execute if they are to be manually run. However, with the introduction of CICD everything gets streamlined. It is also worth noting that tools like Docker have been playing marvelous role in making the application lightweight and also deployable anywhere with all the required dependencies. With tools like Trivy and SonarQube administrators/DevOps engineers can be absolutely sure about the quality of the code and threat analysis in the environment.

Last but not the least:  

**<mark>Remember to clean up the resources you have created on the project since these can incur a good amount of billing.</mark>**

I hope you found this project helpful. Do let me know if there was something that could have been done better.