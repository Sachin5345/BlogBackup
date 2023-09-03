---
title: "Deploy NGINX using Kubernetes in the easiest way possible."
datePublished: Sun Sep 03 2023 20:18:56 GMT+0000 (Coordinated Universal Time)
cuid: clm3wbfb8000009lf66k4bcsi
slug: deploy-nginx-using-kubernetes-in-the-easiest-way-possible
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693767064739/9596e418-18ed-4a12-bfd8-3746eb0fd93c.jpeg
tags: deployment, nginx, k8s, trainwithshubham, tws

---

Although the Kubernetes universe, also known as K8s, might be intimidating and overwhelming at the same time, it provides benefits for application deployment.

Alright... When we speak of K8s and app deployment, the first question that hits our mind is:

# ***<mark>Why deploy apps using Kubernetes?</mark>***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693768220965/880fc669-6525-4f36-a48d-bc29eddb308b.png align="center")

Here are a few reasons why:

* ***<mark>Container Orchestration</mark>***
    

Kubernetes provides a robust container orchestration platform. It allows you to automate the deployment, scaling, and management of containerized applications. Containers provide consistency across different environments, making it easier to develop and deploy applications.

* ***<mark>Scalability</mark>***
    

Your applications can withstand higher demand thanks to Kubernetes' horizontal scalability feature by adding additional containers or pods as necessary. This aids in preserving application availability and performance during traffic peaks.

* ***<mark>High Availability or HA</mark>***
    

Load balancing, automatic pod rescheduling, and health checks are just a few of the capabilities that Kubernetes offers to keep your applications responsive and accessible even in the event of hardware or software failures.

* ***<mark>Resource Optimization</mark>***
    

Kubernetes intelligently distributes containers across the available infrastructure to maximize resource utilization. This guarantees that resources are used efficiently and affordably, which is crucial in cloud environments where you pay for the resources you use.

* ***<mark>Rolling Updates</mark>***
    

Applications can be updated and rolled back without interruption using Kubernetes. Without any downtime, you may upgrade your application while keeping an eye out for any problems. Old containers can be gradually replaced with new ones. You can quickly revert to an earlier version if issues emerge.

* ***<mark>Declarative Configuration</mark>***
    

To specify the desired state of your applications and infrastructure, Kubernetes uses a declarative approach. Kubernetes strives to realize what you specify while automatically resolving any inconsistencies.

* ***<mark>Service Discovery and Load Balancing</mark>***
    

Applications can more easily discover and communicate with one another because to Kubernetes' built-in service discovery and load balancing. In a containerized system, networking is made simpler by this.

* ***<mark>Secrets Management</mark>***
    

Through Secrets, Kubernetes offers a method for securely managing sensitive data, such as API keys and passwords, which lowers the chance of exposing sensitive data.

* ***<mark>Ecosystem and Community</mark>***
    

A sizable and engaged community supports the growth of Kubernetes and offers a robust ecosystem of plugins and solutions. Helm for package management, Prometheus for monitoring, and Istio for service mesh are just a few of the ecosystem's components.

* ***<mark>Multi-cloud and Hybrid Support</mark>***
    

You may execute your applications on several cloud providers or on-premises infrastructure thanks to Kubernetes' cloud-agnostic nature. For organizations using multi-cloud or hybrid cloud strategies, this flexibility is crucial.

* ***<mark>Cost Management</mark>***
    

Kubernetes can assist businesses in keeping cloud infrastructure expenses under control by efficiently utilizing resources and growing as necessary. Making educated judgments about resource provisioning is made easier by the tools it offers for resource allocation and monitoring.

And definitely topping all the above is...

* ***<mark>Security</mark>***
    

Role-based access control (RBAC), network policies, and pod security policies are just a few of the capabilities that Kubernetes offers to help you secure your containerized applications and safeguard your infrastructure and data.

*In conclusion, Kubernetes increases application scalability, availability, and resource utilization while making the deployment and maintenance of containerized applications simpler. It also offers a wide range of capabilities that are advantageous to both the development and operations teams. It is a tempting option for delivering and administering modern apps in a variety of scenarios because of these benefits.*

Let's quickly hop in to the talk where Ryan wants to deploy an application using K8s and the application is Nginx.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693767475833/97208c67-8d18-4906-985d-fb021c1da3aa.png align="center")

While the deployment of this project is easy, it comes with some pre-requisites:

* Ubuntu (Xenial or Later)
    
* Superuser or Sudo access
    
* Internet access
    
* T2.medium or higher type of AWS EC2 instance.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693768549956/86fe5f97-d11c-40f2-beeb-61457a910217.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693768688166/f6efa7bc-a046-488e-b533-5e7ce74b1973.png align="center")

# ***<mark>Constructing the Master and Worker Nodes</mark>***

1&gt; Login to the AWS console and spin up two EC2 instances with t2.medium as the size and Ubuntu (Xenial or later) as the OS.

2&gt; Once the machines are ready, ssh on each of the machines, execute the following commands:

* sudo apt update
    
* sudo apt-get install -y apt-transport-https ca-certificates curl
    
* sudo apt install [docker.io](http://docker.io) -y
    
* sudo systemctl enable --now docker
    
* curl -fsSL "[https://packages.cloud.google.com/apt/doc/apt-key.gpg](https://packages.cloud.google.com/apt/doc/apt-key.gpg)" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg
    
* echo 'deb [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) kubernetes-xenial main' | sudo tee /etc/apt/sources.list.d/kubernetes.list
    
* sudo apt update
    
* sudo apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
    

Phew. What did we do on both machines here? Let me explain:

> we updated the machine in the first statement/bullet point
> 
> we installed the necessary certificates required using command line in bullet point #2
> 
> we installed Docker since it necessary to pull the images from the Dockerhub repository using bullet point #3
> 
> We enabled and started Docker service in single command using bullet point #4
> 
> We added GPG keys using bullet point #5
> 
> Next task was to add the repository to the sourcelist. Command is bullet point #6
> 
> Once all this is done, update the machine again using bullet point #7
> 
> Install kubelet and kubeadm for using kubernetes using command line in bullet point #8

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769831906/f809842d-d614-43bc-b48c-6c6e023f8283.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769844817/b2e0e355-7410-4be7-a282-2b36bfc1f80b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769860732/6fab6d9a-2e1f-40fe-94ce-37bae1417ffd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769864998/e9071060-870a-4ba8-b868-b52dce4343ea.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769873874/ac7b5972-0dfa-4c66-807e-8e6f6db1508a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769880805/7ede1bcf-32a4-415c-8cb7-48ce19c2cc1b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769885126/0c069117-9af5-4f6e-baa4-271be9e09ac4.png align="center")

## ***<mark>The Master Node has a few more actions</mark>***

* sudo kubeadm init
    

> This command initiates kubernetes in the master node

* > mkdir -p $HOME/.kube
    > 
    > sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    > 
    > sudo chown $(id -u):$(id -g) $HOME/.kube/config
    
    These set of commands help us to setup local kubeconfig (both for root user and normal user)
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769911458/53afd5c2-a52e-4d1d-871e-23c1bf91ab07.png align="center")

* kubectl apply -f [https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml](https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml)
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769928710/762e1b89-81a0-4068-a467-3a9d38a84143.png align="center")

> Applies the weave network

* sudo kubeadm token create --print-join-command
    

> This command provides us a string that can be used to join the worker node machine on to the master node.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769945326/e3a1b367-d825-42e1-9947-a09ae554fcdd.png align="center")

The last but not the least task, outside this master node to be done is to navigate into the security groups of the EC2 instance created for the master node and add port number 6443 into the inbound rules for the kubernetes to function without issues.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693769958114/f1b79302-10d2-43e2-b9ea-5d3145017ddb.png align="center")

***<mark>All set with Master Node!</mark>***

## ***<mark>The Worker Node has a few more actions</mark>***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770027772/1ee76374-2f2a-46e3-97e8-f9343687a91e.png align="center")

Execute the following commands to setup the worker node

> sudo kubeadm reset pre-flight checks

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770232086/6411ed24-9ee6-43ee-88a6-e7bf00c2b109.png align="center")

Next, paste the join command you got from the master node and append `--v=5` at the end. *Make sure either you are working as sudo user or use* `sudo` before the command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770243822/8fcd0136-0731-4913-8218-ecee6ca38ffa.png align="center")

All set!! Now the worker node has successfully joined the Master node... If the join is successful, you should see the below message:

![image](https://user-images.githubusercontent.com/40052830/261848460-c530b65a-4afd-4b1d-9748-421c216d64cd.png align="left")

## ***<mark>Verify Cluster Connection</mark>***

On the master node:`kubectl get nodes`

On the worker node:`docker ps`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770443896/2378523c-8a36-4a1b-9d1c-130ece64d5dd.png align="center")

# **Running Nginx Pod on Kubernetes**

There are two phases in this next stage of deployment. Let's begin with Part 1.

> Creating a directory to host all the manifest files and namespace for the application.

Using the mkdir and cd commands, create the project folder. For my convenience, I have constructed a folder by the name "nginx". Very creative 😎 I know 😂

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770902751/6cb29f3e-7071-48ab-a149-0b62ad41318a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770940636/0f34ed87-2876-4279-ad99-e71fb88a34be.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770714429/ad72d080-7c74-47f5-8bfb-60bd9e631e1a.png align="center")

Ryan had this question for me: why create a namespace?

The answer is:

Within a cluster, namespaces are used to establish distinct contexts. They provide the segmentation and organization of resources like deployments, services, and pods. You can share the same cluster with numerous projects or teams while preventing resource conflicts by utilizing namespaces. Additionally, it lessens the chance of name disputes and improves resource management and access control.

To create a namespace, use the following command:

> kubectl create namespace &lt;name of the namespace you want to create&gt;

For my convenience again, I used nginx 😁

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693770944327/f702152c-6c6a-41ec-b324-8faade9b9eb4.png align="center")

Once the namespace is created, we are all set to move into Part 2 of the deployment. The actual application deployment!

> Create a file called pod.yml and host all the data into the file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771071613/d021a606-c555-4766-98bd-77c72609db39.png align="center")

The next step is to apply this configuration

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771110579/66e101f5-4aad-4dc4-884d-09868918c169.png align="center")

> Once the pod file executes, the next step is to create a deployment manifest

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771204735/83e4f901-51a0-4e3f-a642-ab710a6a56ca.png align="center")

> Now apply the deployment configuration created using kubectl apply command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771283537/e556903d-f6fc-4aed-af7a-4c12af289d33.png align="center")

To understand if my deployment has succeeded and if my pod has been created, use:

> kubectl get pods -n nginx

This command lists all the pods within the namespace nginx

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771377533/302b54d5-40bd-4144-b009-beb697daab4c.png align="center")

To see a more descriptive state, use kubectl describe deployment command as shown below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771430182/ae095862-aa22-4427-99cb-25cb28a8589a.png align="center")

While I was trying to execute this, I also wondered if rolling update works! So... I tried this 😎

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771517213/ccf6b371-518b-4922-9eee-5597804fdcfa.png align="center")

and boom!! the deployment scaled!!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771653907/cf3952b4-3e65-49bc-a99a-c4f534be13c7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771576962/aca8fd5e-69f9-4d93-bc3f-d861d82b9e6c.png align="center")

Once this is completed, all you have to do is add port 30007 to the inbound rules of the security group attached to the worker node. This basically exposes the deployment you have created to the outside world.

All that is left to do is check the cluster IP:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771802365/5d62263a-4e1b-4101-a430-be47af37f6e0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771882599/93c37ce6-e87b-4a78-abf2-489e6d9268b0.png align="center")

**<mark>🎯🎯Target Hit 🎯🎯 Nginx is now set and running!!!</mark>**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693771952981/9f8060d4-6407-46a6-b812-80e7750fc2cd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693772071910/ab709e11-a8c7-4889-b400-8743e0794576.png align="center")

# Pro-tip

***<mark>Once all this is completed, make sure to terminate the instances created, else the bill will skyrocket in your account</mark>***

Happy Learning!!