---
title: "The Simple Storage Service: AWS's Superpower for Storage"
datePublished: Thu Jan 25 2024 19:49:45 GMT+0000 (Coordinated Universal Time)
cuid: clrtmok0m000409lg0mqm1zae
slug: the-simple-storage-service-awss-superpower-for-storage
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706212064112/72a1c9c4-5a28-4967-a52b-8c87a1ade735.png
tags: aws, cloud-computing, storage, s3, simplestorageservice

---

If you have spent any time researching AWS, you are probably familiar with the S3 service. The service is known as Simple Storage Service, or S3, as its first letters were combined to create an acronym.

When I first started learning about AWS, I wasn't sure what services the company offered to users looking to store large volumes of data in the cloud. That's precisely when I got to know S3. Although S3 is primarily a storage service, it may also be used for a variety of other things, including software distribution, disaster recovery, archiving, application hosting, and media hosting.

A simple analogy of how S3 stores objects is like how you store files inside the folders on your local machine. Now that we know what S3 does, let's talk some more about this. S3 stores objects in buckets. These buckets must have unique names. Let's check out some console looks for the S3 service:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706208985818/ae1f4d8b-d3d7-4678-a623-d0759355dff9.png align="center")

That's how a homepage looks when you click on the S3 service from the console (I directly went to the S3 console, assuming you know how to search for the service). We click on **Create Bucket** from the top right, and that is our first step to creating buckets.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706209379264/61f9c2b5-9c17-4a9d-b1f5-f2914ec67aff.png align="center")

Let's first talk about #2 from the screenshot above. I thought of creating a test bucket but when I gave the name test and tried creating one, it stopped me right there!! told me I could not create a bucket since the name is not unique. Now let's head back to #1 from the screenshot.

There are two distinct features in the box. The first one is the General Purpose Bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706209642806/2625b4e6-be1c-4948-9d4a-95351577eea1.png align="center")

Reading through the description itself helps us understand why this is used. As it states, it is a generic one used for regular purposes.

Let us see the other one...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706209794201/363cd9e0-ebc2-44e9-87eb-80b119227b42.png align="center")

These are specific buckets recommended for low-latency use cases. When we look at the description, it says these are the buckets that use only the S3 Express One Zone Storage Class to provide faster data processing within a single AZ. So that is something very specific!!!

Alright!! While I was checking out these, I saw something very catchy: the region! I was trying to create this bucket in the N.Virginia region, and I could see these options, but if I switched regions, these options vanished:

N-Virginia Region:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706210144047/6c831f75-ab74-4675-9ef8-6cbf2824209a.png align="center")

Ohio Region:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706210212332/87a6e39a-d673-46a3-81fd-171b9b0b3884.png align="center")

So this tells me that, even though the service S3 is global, the buckets created and the features are unique to the region.

Great! isn't it? So I moved back to my initial choice of N.Virginia region and provided a unique name to the bucket name field "**jan2024bucketfortest**" 😁😁😁Very unique.... I know. Something else to look for is the ACL.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706210526262/64eedb36-f190-4597-afbb-a43910fd30c1.png align="center")

By default, this is disabled. If we need access from other AWS accounts, enable this feature. Since I was just doing a test to understand this feature, I left it default.

The next thing that decides a whole lot of operations is public access. By default, this is blocked. If we need this to be available, just uncheck the box and that should do the trick:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706210695277/68d98715-1a50-420a-aa61-a969f145f290.png align="center")

Acknowledge the disclaimer and head down to the next section... Look at this one talking about versioning. When I say versioning, this means when you just update your existing content from the local to the cloud, instead of overwriting this same file, it creates a different version and makes it available for us:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706210867574/c30506e1-7a75-44ca-9dc4-97e1e5fe1224.png align="center")

By default, versioning will be disabled; if need be, you can enable it. The next section is for tagging your bucket, which provides you with better tracking or reporting functionality.

Leave the encryption method to default now and click on "Create" at the end of the page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706211054929/1158fd5a-3ef1-49b9-bc1b-399f858b70f6.png align="center")

The next question I had in mind was to read through the naming convention. So here is what I found out about how to name the buckets:

* The name should be unique
    
* The name should start with a lowercase letter or a number
    
* The name must NOT start with an uppercase letter or an underscore
    
* The name must NOT have the suffix -s3alias at the end
    
* The name must NOT start with xn--
    
* The name must NOT be an IP
    

Great!! We are now done with the first part of understanding some basics of S3. In the following blog, we will delve into the object and its storage in the S3 buckets.

If you are happy with what you read, or if you felt that there could have been something better than this, feel free to write a comment.

Happy Learning!!