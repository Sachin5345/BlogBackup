---
title: "Getting started with Terraform Enterprise Basics.. The Terraform Cloud Console!"
datePublished: Fri Nov 17 2023 13:06:39 GMT+0000 (Coordinated Universal Time)
cuid: clp2mwdxw000d09l22m5p3bek
slug: getting-started-with-terraform-enterprise-basics-the-terraform-cloud-console
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700226219625/e6356784-ec33-424a-a367-05361b0636ea.jpeg
tags: terraform, iac, terraform-cloud, tws, terraformenterprise

---

With the help of the robust infrastructure as code (IaC) platform Terraform Enterprise Cloud, businesses can effectively automate and manage their cloud infrastructure. The widely used open-source tool Terraform was developed by HashiCorp, who also created Terraform Enterprise Cloud. Terraform Enterprise Cloud expands on Terraform's fundamental features to satisfy the demands of enterprise-scale systems.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700226153876/17db5ab1-3c7a-48f9-9d7f-cc8a292eec97.jpeg align="center")

Fundamentally, Terraform Enterprise Cloud allows customers to declaratively and version-controllably define, deploy, and manage infrastructure resources across various cloud providers and on-premises settings. Unmatched consistency and agility in infrastructure management are provided by this method, which enables enterprises to embrace multi- or hybrid-cloud strategies, grow their infrastructure with ease, and keep an easily accessible and auditable record of all infrastructure modifications. Terraform Enterprise Cloud's governance and collaboration tools are among its main advantages. It gives groups a centralized platform to work together on infrastructure modifications, guaranteeing that these are examined, accepted, and implemented in a safe and regulated way. This helps firms implement security policies, compliance regulations, and best practices throughout their infrastructure in addition to improving cooperation.

With support for numerous cloud providers, Terraform Enterprise Cloud provides a vendor-neutral solution that enables businesses to select the ideal combination of services to meet their unique requirements and prevent vendor lock-in. The platform creates a smooth and automated workflow for infrastructure updates by integrating with common version control systems, continuous integration/continuous delivery pipelines, and other tools.

This is how you can take a look at the Terraform Enterprise or Terraform Cloud

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700205211708/0952e37f-8c74-4556-ba15-cfcd63bbb2a6.png align="center")

Once you register for the account and log in, the homepage looks like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700205899203/7678b4de-8f7b-44a0-bb46-8e927ee3976a.png align="center")

## Provision Example Resources

This is Block #1 from the screenshot which shows you samples of how you can provision the resources. Once you click on the block you can see a screen like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700206130144/a06951e7-6cdb-4ec6-b160-9b92b3179736.png align="center")

If you have your favorite IDE (like mine is VS Code) installed with the terraform, you can run this code presented and see how it works. This is just a sample of how you can structure your resource creation using code.

## Migrating Local State

Block #2, is about state file management. This is used to migrate your existing state file to the Terraform cloud and manage the currently created config from the cloud.

## Create a new organization

Look at Block #3. This is like a blank canvas. You can create your infrastructure from scratch. When you click on "***Create a new Organization***", the next screen you will look at is

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700220758071/cbd290cd-6f5b-42a5-9852-db436f57cebb.png align="center")

### Projects and Workspaces

On creating the Organization and selecting the Projects & Workspaces from the pane on the left-hand pane and creating a workspace, you will have the liberty to select the type of workflow

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700220932411/29adfb7a-ef29-433a-81dd-4e0b97d36305.png align="center")

### Registry

Heading to the registry on the left-hand pane, you can see this screen below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700221117014/9ab03224-4ff1-47d8-8c51-6f750ea1edf4.png align="center")

If your organization has any published modules and providers, they will show up here.

### Explorer

Let's quickly navigate to the Explorer and see what the content inside

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700221216671/7e98fa02-d5f8-4111-acc1-87792d3aa7f9.png align="center")

Anything that has been created internally in your organization is visible here and this tab can be useful for exporting reports of your configurations.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700221521599/917f3e55-c7b2-409e-af14-973870860299.png align="center")

Fantastic! If you were able to do it till this point and understand what this was, you are awesome! Stay tuned for the next steps or maybe even a quick implementation of the product!

Happy Learning!