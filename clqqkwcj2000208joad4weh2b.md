---
title: "Keeping Kubernetes Healthy: Liveness and Readiness Probe Explained"
datePublished: Fri Dec 29 2023 11:56:48 GMT+0000 (Coordinated Universal Time)
cuid: clqqkwcj2000208joad4weh2b
slug: keeping-kubernetes-healthy-liveness-and-readiness-probe-explained
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703767568908/f02125da-244f-4bd5-9043-2555b71e753a.jpeg
tags: kubernetes, kubernetes-livenessprobe, kubernetes-readiness-probe, liveness-probe, readiness-probe

---

So you’ve built an amazing app and deployed it to Kubernetes — congrats! But how do you make sure your app stays up and running as intended? That’s where liveness and readiness probes come in. These probes allow Kubernetes to monitor your app and ensure it’s healthy, responsive, and ready to handle requests. Without them, Kubernetes would have no way of knowing if your app has crashed or isn’t functioning properly.

In this article, we’ll walk through what liveness and readiness probes do, why they’re important, and how to configure them for your Kubernetes deployments. You’ll see how to set up simple HTTP checks as well as more complex exec probes. By the end, you’ll know how to keep your apps healthy and humming along in Kubernetes. Sounds good? Then let’s dive in!

### What Are the Liveness and Readiness Probes in Kubernetes?

![Image Credits: Qovery](https://cdn.hashnode.com/res/hashnode/image/upload/v1703767674760/a677d2d2-a59c-4046-b8e8-5ed665f24add.jpeg align="center")

Liveness and readiness probes are checks that Kubernetes performs on your pods to determine their health. Liveness probes check if your application is still running, while readiness probes check if your application is ready to receive traffic.

Liveness probes are crucial for ensuring your application stays up and running. If a liveness probe fails, Kubernetes will restart the pod to restore service. For example, if you have an application that can get stuck, a liveness probe can catch that and restart the pod.

Readiness probes, on the other hand, check if your application is ready to receive requests. If a readiness probe fails, Kubernetes will remove the pod’s IP address from the service load balancer. This ensures no requests are forwarded to the pod until it becomes ready again. For example, if your application has a slow startup, a readiness probe can delay traffic until it’s fully started up.

You define probes in your pod specs. There are three types:

* Exec probes: Run a shell command in the pod
    
* HTTP probes: Perform HTTP requests against the pod
    
* TCP probes: Perform TCP checks against the pod
    

For most applications, HTTP probes are a good choice. You specify a path to probe, and Kubernetes will send an HTTP GET request to that path. If it gets a successful response, the probe passes. With liveness and readiness probes, you can ensure your Kubernetes applications stay highly available and ready to receive traffic at all times. Your users and customers will appreciate the reliability!

### How Do Liveness Probes Work?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703847444426/e5d23184-9ff0-4463-9196-87e7bf5dd1ed.png align="center")

Liveness probes check if your application is up and running. They ensure that if a pod goes down for any reason, Kubernetes can restart it and get your app back online.

How do liveness probes work? Kubernetes will periodically execute the liveness probe on your application’s container(s) to check the health status.

There are three types of liveness probes:  
1\. HTTP probe: checks for a successful HTTP response (status code 200–399). This is good for web apps and REST APIs.  
2\. TCP probe: Checks if a TCP port is open. Use this for non-HTTP apps.  
3\. Exec probe: Executes a command inside the container. Checks the exit code to determine health.

If the liveness probe fails, Kubernetes will restart the pod to restore service. The pod will then be subjected to the startup probe to determine if it should receive traffic. The liveness probe should check for basic signs of life and ensure that your app is functioning properly. It ensures availability, but not necessarily responsiveness.

You define liveness probes in the Pod specification, for example:

```yaml
livenessProbe:
httpGet:
path: /healthz
port: 8080
initialDelaySeconds: 30
timeoutSeconds: 2
periodSeconds: 10
timeoutSeconds: 1
failureThreshold: 3
```

This would hit http://&lt;pod\_ip&gt;:8080/healthz every 10 seconds. If it fails for three consecutive tries, the pod is marked as not ready.  
Keeping pods healthy and available is crucial. Readiness probes are a key tool in your Kubernetes reliability toolkit to ensure stable, robust apps.

### Liveness vs Readiness: Key Differences

Liveness and readiness probes are two types of health checks in Kubernetes that monitor your application pods. While they may sound similar, they serve different purposes. Understanding the distinction between them is key to keeping your Kubernetes cluster in good health.

### Liveness probes

Liveness probes Check if your application pods are still running. If a liveness probe fails, Kubernetes will restart the pod. This ensures that your application is always available and running. Liveness probes are important for applications that run for a long time and need to be restarted if they crash for some reason.

Some examples of liveness probes include:

* Checking if a web server returns a 200 OK response
    
* Seeing if a process is still running in a container
    

### Readiness probes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703847635889/4cf678f8-ca1f-40f4-b424-93887da6d723.png align="center")

Readiness probes check if your application pods are ready to accept traffic. If a readiness probe fails, Kubernetes will remove the pod from service load balancers and endpoints. This ensures that clients don’t access pods that are not ready to handle requests. Readiness probes are important for applications that take time to start up and be ready to serve traffic.

Some examples of readiness probes include:

* Checking if a web server returns a 200 OK response on a certain endpoint
    
* Seeing if a database connection can be established
    

The key differences to remember are:  
• Liveness probes determine if a pod should be restarted  
• Readiness probes determine if a pod should receive traffic

Keeping on top of your application’s health and understanding how liveness and readiness probes work will help ensure maximum uptime and a good experience for your users. Your Kubernetes pods will be monitored and kept in working order, just like a mechanic keeps your car running well with regular checkups.

### Best Practices for Configuring Probes in Kubernetes

When configuring probes in Kubernetes, following some best practices will help keep your application healthy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703850489106/f51c7bb0-5ce6-43a4-a983-2567719acb70.png align="center")

### Choose probe types carefully

Select the probe type that best fits your needs. Liveness probes check if the container is still running, while readiness probes confirm if the container is ready to accept traffic. For most applications, a combination of both is ideal.

### Set appropriate thresholds

The thresholds you define determine how long Kubernetes waits before acting on probe failures. Set these thoughtfully based on your application requirements. For example, a liveness probe with a timeout of 1 second and a failure threshold of 3 means Kubernetes will restart the container after 3 consecutive failures, each within 1 second.

### Probe endpoints

For HTTP probes, choose an endpoint that fully represents the health of your app. Avoid endpoints that only check a small part of your system. For TCP or command probes, configure them to check essential parts of your application.

### Set sane probe intervals

The probe interval controls how often Kubernetes checks the probe. Set this to an interval that provides a quick response but doesn’t overload your system. A good rule of thumb is 10–60 seconds for liveness probes and a bit longer for readiness probes.

### Use probe delays

Add initial delays to your probes, especially readiness probes. This gives your container time to start up before the probe begins checking. A delay of 15–30 seconds is typical. Without a delay, there’s a chance your probe may fail incorrectly when the container is still initializing.

### Final thoughts

Keep in mind that probes are a key part of a self-healing Kubernetes system. Configure them thoughtfully, test them thoroughly, and monitor how they impact your deployments. Well-designed probes can help keep your application stable and responsive. Poorly designed probes may cause unexpected behavior!

### Conclusion

So there you have an overview of liveness and readiness probes in Kubernetes and how they help keep your applications and deployments running smoothly. By configuring these health checks, you’re ensuring your pods stay in a healthy state and your services remain available to users. Kubernetes will automatically restart unhealthy pods or remove them from load balancers to prevent issues from impacting your users. While it may seem like extra work upfront to define health checks, the time savings from automated self-healing and reduced troubleshooting make it well worth the effort. Your Kubernetes cluster will be humming along nicely, and you’ll have more time to focus on building great applications.

If you feel this was informative or if there was something that could have been added to this article, feel free to drop me a note here or on LinkedIn.