---
title: "Deploying a Microservices based application with Kubernetes"
datePublished: Wed Sep 06 2023 13:51:49 GMT+0000 (Coordinated Universal Time)
cuid: clm7st52h000e09ik5jefg0v4
slug: deploying-a-microservices-based-application-with-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693990420162/c8036227-f286-44d3-b8c4-926ee7ed779c.png
tags: microservices, kubernetes, trainwithshubham, tws, hands-onproject

---

Hey Folks! I started my week with a fantastic workday!

While I posted my last blog on deploying NGINX with Kubernetes, I was wondering if I could do something similar with Microservices Applications too.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693995159687/c0c42dd4-5546-4528-8743-767ef3ebdf98.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693995678447/73897785-7b12-4360-81ab-95ab398d25e5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694007288568/b299cdf1-abe5-498c-b945-20b5850aadf4.png align="center")

# ***<mark>Microservices and their benefits</mark>***

A complex application is divided into several small, independent, and loosely linked services using the software architectural paradigm known as microservices. Each service oversees a distinct aspect of the application's functionality and interacts with other services via clearly defined APIs (application programming interfaces).

Here are the basics of microservices and why they are used:

* ### ***Service Decoupling***
    

A monolithic application's tightly linked components make it challenging to change or scale individual pieces without doing so inadvertently to the system as a whole. These components can be built, deployed, and maintained independently thanks to the decoupling provided by microservices.

* ### ***Small and Focused***
    

Microservices are often compact and concentrated on a small set of tasks or processes, making them simpler to comprehend, create, and maintain. Development teams can specialize on particular services thanks to this granularity, which boosts productivity.

* ### ***Technology Diversity***
    

The programming languages, frameworks, and technologies that are most appropriate for each microservice's unique set of responsibilities can be used. Teams can select the best tool for the job because to this flexibility.

* ### ***Scalability***
    

Depending on demand, microservices can scale independently. The efficient use of resources is ensured by allocating more resources to those services that need them without hurting others.

* ### ***Fault Isolation***
    

In a monolithic architecture, a single bug or failure can bring down the entire application. In microservices, failures are isolated to individual services, reducing the impact on the overall system and making it easier to diagnose and recover from issues.

* ### ***Continuous Deployment***
    

Microservices are well-suited for continuous integration and continuous deployment (CI/CD) practices. Each service can be developed, tested, and deployed independently, speeding up the development and release cycle.

* ### ***Improved Maintainability***
    

It is simpler to make changes, repair issues, and add new features since each service has a well-defined scope, which prevents changes from having an impact on other areas of the application. This enhances the system's overall maintainability.

* ### ***Team Autonomy***
    

Microservices encourage team autonomy and ownership of particular features by enabling development teams to operate independently on their assigned services.

* ### ***Resilience***
    

Microservices can be designed with redundancy and failover mechanisms, enhancing the resilience of the overall system. If one service fails, others can continue to function.

## ***<mark>Benefits of Microservices</mark>***

By dividing complicated programs into smaller, more manageable, and loosely linked services, microservices enable the development of scalable and complex applications. They provide advantages such as increased fault tolerance, scalability, maintainability, and agility. However, introducing microservices also presents difficulties, such as the necessity for a strong infrastructure and monitoring tools to support them and the difficulty of managing interactions between services.

Now that we know what microservices are and why they would be used to build an application, let's focus on deploying the application that has been built and learn how to deploy these kind of applications using Kubernetes.

# ***<mark>Phase - 1: Construction of the Master and Worker Nodes</mark>***

* ## ***<mark>Master Node</mark>***
    

I started the project by spinning up two machines on AWS EC2 with the below configurations:

* Ubuntu OS (Xenial or later)
    
* sudo privileges
    
* Internet access
    
* t2.medium instance type
    

Once these machines were created, I renamed one of the machines to Master Node and performed SSH into the instance. Once the shell opens up, the first step is to update the machine.

Run the below command:

> sudo apt update

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693995790442/d7f28499-86a2-42d8-a78d-da24ef38da92.png align="center")

The next step is to install the certificates needed. Run the below command:

> sudo apt-get install -y apt-transport-https ca-certificates curl

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693996135325/f307c43a-b156-4486-b5c9-c5c0a1a7023f.png align="center")

Now install Docker to ensure we can build and deploy images

> sudo apt install [docker.io](http://docker.io) -y

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693999565757/2dd68db7-8738-4266-be61-3e7c662a0b6c.png align="center")

Enable the service and start the docker service

> sudo systemctl enable --now docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693999613098/1cb8f9ea-82ec-4ae7-9330-8b4a94a6b806.png align="center")

Once we start and enable the Docker service, it's time to add the GPG keys

> curl -fsSL "[https://packages.cloud.google.com/apt/doc/apt-key.gpg](https://packages.cloud.google.com/apt/doc/apt-key.gpg)" | sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/kubernetes-archive-keyring.gpg

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693999874834/8c1fe895-cb02-40d3-af71-94f65e9da40d.png align="center")

Post the addition of the GPG keys, it's time to add the repository to the sourcelist

> echo 'deb [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) kubernetes-xenial main' | sudo tee /etc/apt/sources.list.d/kubernetes.list

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000022969/1caf8e3b-d0a6-47e4-b9dc-5ed9a532adef.png align="center")

Once all this has been completed, we need to update the system

> sudo apt update

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000070831/edd7ea90-726b-4f80-af86-915b83c3f434.png align="center")

Once the system updates, it's time to install kubeadm

> sudo apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000165999/099db9ec-c957-4d1e-bdad-292a1ff2b6d7.png align="center")

Initiate the kubeadm mode using the below command

> sudo kubeadm init

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000246809/593a959a-9f7e-4a87-ade0-34575df0a382.png align="center")

Once this completes, you should be able to see the message that control-plane has initialized successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000271473/488643a6-84b5-4b8b-879a-213a66316176.png align="center")

We can use the export command highlighted to export the configuration so that it can be reused in case of requirements.

The next steps are to create a folder called kube and then copy the configuration over and change the ownership of this file.

Run the set of commands from the previous output to perform the actions mentioned above.

> mkdir -p $HOME/.kube
> 
> sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
> 
> sudo chown $(id -u):$(id -g) $HOME/.kube/config

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000639041/b216d6fc-cb1d-45e9-a50e-341a1cc3c876.png align="center")

Next two steps are to create a CNI using the weave-net and to generate a join token:

> kubectl apply -f [https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml](https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml)
> 
> sudo kubeadm token create --print-join-command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000938400/e737b946-10a0-4abd-9373-16183ca71446.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000944886/ff134c48-ec8d-46b3-99ee-88d715de0351.png align="center")

Just to confirm everything went well,

> kubectl get nodes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694000988220/e40d1077-03b7-425a-98fa-3359efce36b4.png align="center")

* ## ***<mark>Worker Node</mark>***
    

The set of commands to be run on the worker node until initiating kubeadm

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694002689747/0d34febc-5ca1-442c-96ae-ba17ae0fbdac.png align="center")

Follow the below steps:

Update the instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694003075111/d44008f0-67d3-426c-a7d9-ab3aa604fe83.png align="center")

Install Docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694002961106/27ddd649-3a9e-44bc-8d00-4a9f597f88a1.png align="center")

Start and Enable Docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694002959554/0913a128-8700-4d0b-9aa3-80680c8d1159.png align="center")

Add the GPG keys

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694002963476/b4ea82e1-1195-4a9c-abc5-7f3fa2c05c96.png align="center")

Add the repository to the sourcelist

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694003112975/3ea3f34d-79da-46c2-8a1b-a22727b87e9b.png align="center")

Update the instance again

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694002973291/df53a19b-2f8d-442f-b869-7c258a54092f.png align="center")

The next step now is reset the pre-flight checks. This is a precautionary step done to ensure that if the init has been performed, it will be reset.

Run the command below to execute the task:

> sudo kubeadm reset pre-flight checks

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694004090814/6b97b8f4-61d5-4aed-9f36-b049cfa66c78.png align="center")

The last step of phase 1 is to join the worker node to the master. Use the join statement output that we got from the master node. Also add --v=5 at the end. Execute the command below to get this task done (this command is specific to the instance you create so make sure to copy one from your instance)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694004572540/6d6bf74e-e730-4efd-8c88-ad6323fa3637.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694004581229/8eb7e3fd-73a8-4d4f-ac83-fb432deb7d9c.png align="center")

On a successful join, you should see the message: "This node has joined the cluster".

# ***<mark>Phase - 2 Create the yml files needed to execute the project</mark>***

Fork the [Git repository](https://github.com/LondheShubham153/microservices-k8s.git) for all the necessary files.

Once you fork this repo, clone it to your master node (note that the prerequisite here is the master node must have the git installed, if you would like, as an additional step, execute sudo apt install git)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005041359/29c04c80-fa71-47b7-9885-c2c0953e219b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005046313/33b37a4f-3807-48a7-bc04-72b02cb2a82d.png align="center")

Once you clone the repo, navigate to the folder containing the yml files and apply all the configurations:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005057870/efbeaf23-24b0-4d48-98a6-6e1cae367c34.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005060533/dce8d64b-4d71-4d3a-9859-86f051397890.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005069569/65d6e956-1973-4868-a72f-7d13ee80f430.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005073628/1222ff0e-6627-405b-a264-7ad93e2cb1dd.png align="center")

To verify the deployment's success, execute the command below:

> kubectl get deployments,services

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005145710/d0269ca2-144d-4bc0-aca9-9305d31dd93e.png align="center")

We are now all set to move to Phase - 3

# ***<mark>Phase - 3 Test the deployed application</mark>***

Now that we have deployed all the necessary files and the app is ready to be tested, run the curl command to test the deployment.

> curl http://&lt;service-ip&gt;:&lt;service-port&gt;

Service IP is nothing but the public IP of the master node and the port that has been assigned for the application. In my case the application is hosted on the EC2 instance with the public IP 3.21.242.206 and the port 30007. So the command (in my case) is:

curl [http://3.21.242.206:30007](http://3.21.242.206:30007)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694005578094/335cbf79-aa5f-488c-9e39-2f3f0e693692.png align="center")

That's all folks! There we have it! An application that is based on microservices architecture deployed using Kubernetes.

I would love to hear back on how was this project execution and if there is any scope for improvements!

Happy learning!