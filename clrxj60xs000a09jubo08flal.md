---
title: "S3: The storage wonder"
datePublished: Sun Jan 28 2024 13:22:26 GMT+0000 (Coordinated Universal Time)
cuid: clrxj60xs000a09jubo08flal
slug: s3-the-storage-wonder
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706448013620/f2a7dbfc-aa50-4c8b-8fc1-237fa4ce46ad.png
tags: aws, storage, s3, bucketpolicies, s3-buckets, resourcepolicies

---

In my earlier article, I wrote about what the S3 service was doing for us and how we used it to create a bucket. In this article, let's talk about how the objects are stored and what policies will govern the access for these objects.

Objects in general, when we talk about with reference to cloud and specifically S3 buckets are nothing but files. These can be images, scripts, text files, excel files, word documents, pdfs etc... When you store these objects in S3 buckets these will be stored with the key. This key that I mentioned has a prefix and an object name in it. It sounds a bit confusing? Let me explain that.

Let's imagine that I have a text file called "file.txt" and I put this file straight into my bucket that I created earlier, which was "jan2024bucketfortest", there will be a key generated for this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706376454074/7cc1d3e6-9db2-463d-b583-bf0a3391c612.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706376464147/5cfe8316-95c5-4f90-8bd2-dfb374a4bf9d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706376505974/61b3b185-47b8-42f1-808e-fb74d1ff482d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706376520972/9a6444b5-2580-4a3e-981e-bd4946f59399.png align="center")

Let me tell you about the key now...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706376416509/19f9f72f-4e47-4dd3-aa75-d607eeeeb606.png align="center")

Now, let us discuss some of the security measures that S3 provides. These characteristics can be categorized into two types: resource-based and user-based.

1. User-based
    
    IAM policies dictate which API should be allowed for a specific user from IAM.
    
2. Resource-based
    
    This can be further split into three tunnels:
    
    1. Bucket Policies
        
    2. Bucket ACL
        
    3. Object ACL
        

* Bucket Policies: Bucket-wide rules from the S3 console allow cross-account access
    
* Bucket Access Control List: These are less common and can be disabled
    
* Object Access Control List: These are fine-grained policies and can be disabled.
    

Noting when the IAM principal can access an S3 object is just as important as knowing how the bucket policies are written, which is the next item I believe will be useful to know.

> <mark>Condition:</mark>
> 
> If user IAM permissions ALLOW **<mark>OR</mark>** If the resource policy ALLOWS <mark>AND</mark> there is <mark>NO explicit DENY</mark>
> 
> Result:
> 
> IAM principal can access the S3 object

Let's talk in brief about the S3 bucket policies...

* These are JSON-based policies
    
* The structure of these policies involve Resource, Effect, Action and Principal.
    

Let me show you a sample of how these policies look:

![How to secure AWS S3 buckets with sensitive data — Kloudle Website](https://imgs.kloudle.com/academy/how-to-secure-aws-s3-buckets-with-sensitive-data/1673703080-aws-s3-bucket-policies-to-restrict-access.png align="left")

This policy specified above is used to secure AWS S3 buckets with sensitive data. You can read more about the policy and even more on security on [Kloudle's Site](https://kloudle.com/academy/how-to-secure-aws-s3-buckets-with-sensitive-data/)

So what do we use this S3 bucket policy for?

This bucket policy can be used for:

* Granting access to another account (Cross-Account Access)
    
* Force the objects to be encrypted
    
* Grant public access to the bucket.
    

Hmm... Well, that's all for this blog. If you feel that something is missing, you can always write to me through the comments here or feel free to drop me a note on the LinkedIn page. Happy Learning!