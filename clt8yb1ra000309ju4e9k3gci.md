---
title: "Replication in S3: The technique which makes your data available all the time"
datePublished: Fri Mar 01 2024 17:51:25 GMT+0000 (Coordinated Universal Time)
cuid: clt8yb1ra000309ju4e9k3gci
slug: replication-in-s3-the-technique-which-makes-your-data-available-all-the-time
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709300514019/4d979a31-f0dc-48c0-a5e5-d8c6698225fd.png
tags: aws, s3, replication, s3replication, crossregionreplication, sameregionreplication, storageservice

---

# Recap and Intro to this blog

The previous two blogs in the S3 series expressed some views about what S3 is and some security aspects of S3. If you have not read those two blogs, don't worry. Here are the links:

[Blog -1: The Simple Storage Service: AWS's Superpower for Storage](https://hashnode.com/post/clrtmok0m000409lg0mqm1zae)

[Blog -2: S3: The storage wonder](https://hashnode.com/post/clrxj60xs000a09jubo08flal)

Now, in this blog, I will be writing about the replication methods and storage classes in S3.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709301233270/9f7bcd7b-44c4-4e4a-a5ab-848bd7ed80ee.png align="center")

As is customary for engineers working with cloud platforms like AWS, S3 is crucial to the day-to-day management of storage-related tasks. Assume Sachin, our developer, and Rahul, our IT specialist, are chatting, and Rahul would like to know more about this storage solution that Amazon is offering.

# Availability and Durability in S3

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709301830071/a799f1bc-ae06-49d0-91e1-38a89f31fb86.png align="center")

## Availability

We can define availability as the measure of how ready the service is.

## Durability

In the context of Amazon S3 (Simple Storage Service), durability refers to the service's dependability in holding onto stored objects over time without loss or corruption.  

When it comes to defining availability for S3, it is 99.99% which means, in a whole year of it's operation S3 can be down or inaccessible for 53 minutes (that is what Amazon guarantees us). Now, when I said 99.99% available, I was talking about the S3 standard class here. Let me also give you a reference table that talks about the availability that S3 offers with its storage classes:

| Storage Class | Availability | Suitable Use Cases |
| --- | --- | --- |
| S3 Standard | 99.99% | Frequently accessed data, general-purpose storage |
| S3 Intelligent-Tiering | 99.90% | Variable or unknown access patterns |
| S3 Standard-IA | 99.90% | Long-lived, infrequently accessed data |
| S3 One Zone-IA | 99.50% | Infrequently accessed data stored in a single AZ |
| S3 Glacier Deep Archive | 99.99% | Archival data, data with retrieval times in minutes |
| S3 Glacier Instant Retrival | 99.90% | Ideal for archive data that needs immediate access, such as medical images, news media assets, or user-generated content archives. |
| S3 Glacier Flexible Retrieval | 99.99% | The perfect option for offshore data storage requirements, backup, catastrophe recovery, and situations when you occasionally need to retrieve some data quickly without worrying about expenses |

Similarly, these classes have a durability index too. I would recommend a good read on [this link](https://aws.amazon.com/s3/storage-classes/) from the Amazon Web site for more information.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709301676934/e6f74416-df09-4a3e-9161-9a4349aa23d3.png align="center")

Quickly heading to the next pitstop of the replication methods, we have:

1. Same Region Replication
    
2. Cross Region Replication
    

Simple as that, the Same Region Replication, also known as SRR, happens between the source and target buckets in the same region.

Let's understand what cross-region replication is and how this helps in the cloud.

For the CRR to work,

> * Source and target buckets must have the versioning enabled
>     
> * Enable the IAM permissions to S3 for a seamless replication experience
>     

Also, the CRR works asynchronously. Here, the buckets can be in different AWS accounts.

Some sample use cases for each:

> CRR: Compliance based activities, Lower latency access replication across accounts
> 
> SRR: Log aggregation, Live replication between test and production accounts

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709307966351/ff40cb33-a1e1-434f-8ac5-fe33b0449ffe.png align="center")

When we activate the replication processes, will everything begin to replicate automatically? No, is the response. Only the more recent things begin to replicate once we enable it. How then may the older and unsuccessful objects be moved to the intended bucket?

S3 provides a unique mechanism known as S3 Batch Processing. The older objects and the objects that were unable to reproduce are handled by this process. Replication steps for delete operations also involve deleting markers from the source bucket to the destination bucket. This ensures that no objects designated for deletion are overlooked. What about malicious deletes, in my opinion? To prevent malicious deletes, objects that have been tagged for deletion and versioning are not taken into account for replication. Isn't that a pleasant feature?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709309432376/8d6bc465-ffed-45b7-88d8-f42f1d370490.png align="center")

# Storage Classes

Let me tell you about the storage classes in S3.

1. S3 Standard
    
2. S3 Standard Infrequent Access (IA)
    
3. S3 Standard One-Zone IA
    
4. S3 Intelligent Tiering
    
5. S3 Glacier Instant Retrieval
    
6. S3 Glacier Flexible Retrieval
    
7. S3 Glacier Deep Archive
    

Let's take a look on each of these with some use cases:

## S3 Standard

S3 Standard is the default storage class and offers high durability, availability, and performance for frequently accessed data. It is suitable for a wide range of use cases, including:

* Hosting static websites: S3 Standard provides fast and reliable storage for website assets such as HTML, CSS, and images.
    
* Content distribution: Delivering frequently accessed content, such as videos or software downloads, to users worldwide with low latency.
    
* Application data storage: Storing data used by cloud-native applications, databases, and analytics platforms that require high throughput and low latency access.
    

## S3 Standard-IA (Infrequent Access)

S3 Standard-IA is ideal for data that is accessed less frequently but requires rapid access when needed. It offers lower storage costs compared to S3 Standard while maintaining high durability and availability. Use cases for S3 Standard-IA include:

Long-term storage: Archiving data that needs to be retained for compliance or regulatory purposes with occasional access requirements. Disaster recovery: Storing backup copies of critical data that may need to be accessed in the event of a disaster or system failure. Media and entertainment: Storing large media files, such as video libraries or image archives, with occasional access for content distribution.

## S3 One Zone-IA

S3 One Zone-IA provides cost-effective storage for infrequently accessed data that does not require multi-AZ redundancy. It stores data in a single Availability Zone, offering slightly lower availability compared to S3 Standard-IA. Use cases for S3 One Zone-IA include:

* Secondary backups: Storing additional copies of backup data in a different AWS Region for added redundancy and disaster recovery.
    
* Development and testing: Storing non-production data sets and environments where durability requirements are lower, and cost optimization is a priority.
    
* Collaborative projects: Sharing large files and datasets among team members or partners with infrequent access requirements.
    

## S3 Intelligent-Tiering

S3 Intelligent-Tiering is designed for data with unpredictable or changing access patterns. It automatically moves objects between two access tiers – frequent access and infrequent access – based on their usage patterns. Use cases for S3 Intelligent-Tiering include:

* Data lakes and analytics: Storing large volumes of data for analytics and machine learning workloads where access patterns may vary over time.
    
* Backup and recovery: Storing backup data that may be accessed infrequently but requires immediate availability when needed.
    
* Archiving: Managing datasets that transition between active and archival states, optimizing storage costs without sacrificing accessibility.
    

## S3 Glacier Instant Retrieval

When it comes to archive storage, Amazon S3 Glacier Instant Retrieval is the most affordable option for storing data that needs to be retrieved in milliseconds and has a long shelf life. When your data is accessed once every quarter, you can save up to 68% on storage expenses by using S3 Glacier Instant Retrieval instead of the S3 Standard-Infrequent Access (S3 Standard-IA) storage class. With the same throughput and milliseconds of access as the S3 Standard and S3 Standard-IA storage classes, S3 Glacier Instant Retrieval offers the quickest access to archive storage. Use cases for this include:

For archived data that requires instant access, including medical photos, news media assets, or archives of user-generated material, S3 Glacier Instant Retrieval is perfect. S3 Glacier Instant Retrieval allows you to upload items directly, and S3 Lifecycle rules allow you to transfer data from the S3 storage classes.

## S3 Glacier Flexible Retrieval

S3 Glacier Flexible Retrieval offers inexpensive storage for archive data that is recovered asynchronously and accessed one to two times a year, at a cost up to 10% less than S3 Glacier Instant Retrieval. S3 Glacier Flexible Retrieval (previously S3 Glacier) is the best storage class for archive material that doesn't need to be accessed right away but needs to be flexible enough to retrieve big amounts of data for free, like in backup or disaster recovery use cases. With access times ranging from minutes to hours and free bulk retrievals, S3 Glacier Flexible Retrieval offers the most flexible retrieval options while maintaining cost-effectiveness.

Use cases:

It is the best option for offshore data storage, backup, disaster recovery, and situations where you need to occasionally access some data quickly without worrying about costs.  

## S3 Glacier Deep Archive

S3 Glacier Deep Archive is the lowest-cost storage class designed for data that is accessed infrequently and stored for long-term retention. It offers the highest durability and lowest storage costs among all S3 storage classes but with retrieval times measured in hours. Use cases for S3 Glacier Deep Archive include:

* Legal and regulatory archives: Storing legal documents, contracts, and audit logs that require retention for decades or longer with minimal ongoing costs.
    
* Medical and healthcare data: Archiving patient records, medical images, and research data for compliance with data retention regulations and patient privacy laws.
    
* Historical and research archives: Preserving historical records, archaeological data, and research datasets for academic and cultural institutions with limited budgets.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1709315315098/13ab59af-73fb-48a4-9c82-c85eb1f43422.png align="center")

# Conclusion

To accommodate the various demands of contemporary enterprises and organizations, Amazon S3 provides a wide variety of storage classes. You can efficiently optimize your storage prices, performance, and durability while making sure your data is accessible and secure in the cloud by being aware of the features and use cases of each storage class. Whether you're keeping massive video files, long-term archive records, or application data that is accessed often, Amazon S3 has a storage class that will meet your needs.

Phew!! This wonderful storage service is a never ending subject for any research and Amazon keeps coming up with new updates and features to its services... So keep an eye on the documentation from Amazon too.

Happy learning!