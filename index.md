---
layout: lesson
root: .
---
The Bash shell scripts that automatically manage multiple AWS instances will be referred to as the "Scripts" from now on.

We have successfully run the Scripts on:
- a **Linux machine** using the **terminal** program configured to run the Bash shell
- the **AWS CloudShell**, a Linux terminal configured likewise that is hosted on AWS and is used through the browser.

We **have not tested** the Scripts with other shells, or on MacOS or Windows using the Git Bash program. The course does not cover such compatibility or configuration issues.

The Scripts make use of the **AWS Command Line Interface** (AWS CLI), a software tool that enables you to interact with AWS through **commands** that can be run either in the **terminal** or within **shell scripts**. The Scripts run the AWS CLI to make requests to manage (create, allocate, ..., and delete) AWS services such as instances, storage, domain names, etc. For such requests to be successful, the **AWS CLI** and the target **AWS account**, wherein services will be managed, **must be properly configured**.

# Overview
This lesson will guide you to:
- create your AWS account.
- configure your AWS account for daily work, including **enabling access with the AWS CLI**.
- configure your Linux terminal environment with the Scripts and the AWS CLI, the AWS CLI configured to manage resources within your AWS account --- you can use either of these environments or both:
  - a Linux machine 
  - the AWS CloudShell

### Your AWS account
Episodes 1 and 2 provide the instructions to create and configure your AWS account. 

Note that we organised the instructions in all episodes (4 episodes in lesson 1 and 4 in lesson 2) assuming that you are going to **create and use your own** AWS account, and hence you have full permissions to configure it as instructed in the course --- we refer to such an account as an AWS **personal account**. 

However, **you can use an existing AWS account** you have access to. Throughout the course, where relevant, we point out what "extra" you may need to do to configure your account as required to run the Scripts. 

If you already have an AWS account that you would like to use to run the Scripts, skip Episode 1 and configure your account as described in Episode 2. Specifically, to enable **access with the AWS CLI**, you need to have/create an IAM (Identity and Access Management) user account enabled with **programmatic access** based on **Access key ID** and **Secret access key** credentials, see Episode 2, Section [3. Create an IAM user account to create and manage AWS resources](02-configure-aws-account.md#3-create-an-iam-user-account-to-create-and-manage-aws-resources). If the AWS account your are using is your personal account, you have full permissions to do the configuration presented in that section.

If the AWS account that you would like to use to run the Scripts is an **institutional account**, meaning that it was **provided to you by your institution** (company, school, organisation), skip Episode 1 and configure your  account with **programmatic access** as mentioned above, if possible. However, **you may need to contact** your IT department to help you configure your account as required to run Scripts. Typically, institutional accounts are created and **somewhat configured** by the **IT department** of the institution first, and only then passed to a person for that person's individual use. The configuration by an IT department may include using AWS services in a **single region** only (in USA, Europe, etc.), or accessing AWS services using **specific security applications**, among other regulations, see the callout below. 

> ## Are you using an institutional AWS account?
> If your are using an institutional account, you are very likely to be using specific security applications to access your account. For instance:
> - to access the AWS Console with our institutional AWS account, we use the applications `Shibboleth` and `Duo Mobile`. `Shibboleth` runs in the browser to ask for our username, password, and a pushed notification from `Duo Mobile` in our mobile phone. 
>
> - to access AWS services through the AWS CLI, invoked either from a script or from a terminal in our Linux machine, we first need to run the application `saml2aws` to generate a token that is valid for 1 hour, and run it again as needed.
>
> The course does not cover the configuration and use of those or similar security applications which may be used in your institution. Your IT department will be able to help you. 
>
> **Note that**, using our institutional account, we have successfully run the Scripts to access AWS services through the AWS CLI using either `saml2aws` or the keys credentials mentioned above, which we created in the AWS Console. Thus our institutional account, as configured by our IT department, enables access through both `saml2aws` and keys credentials. Only the creation and use of keys credentials is presented in Episodes 2 and 3.
{: .callout}
 
### Your Linux terminal environment
To run the Scripts you need to **configure only one** of these environments:
- a Linux machine
- the AWS CloudShell 

Episode 3 provides the instructions to configure your Linux machine with the Scripts and the AWS CLI. The AWS CLI will be configured to use credentials (private and public keys) when invoked within the Scripts to request AWS service operations. The credentials will be generated using the AWS Console when you configure your AWS account in Episode 2. 

Episode 4 provides the instructions to configure the Scripts in the AWS CloudShell. The AWS CloudShell is "a browser-based \[Linux Bash terminal\] shell that gives you command-line access to your AWS resources" and **has the AWS CLI** already **installed and ready to run** using "credentials" derived from the information you use to login to the AWS Console. Hence you only need to configure the Scripts, but **you must be logged in** to your AWS account through **the AWS Console** to be able **to run the AWS CloudShell** and the Scripts.

In this course you will be using the AWS Console and, through the Scripts, the AWS CLI to manage AWS services but there are other ways to manage AWS services, see the callout below.

> ## Ways to access and manage AWS services
> There are four ways to access and manage AWS services: 
> 1. the AWS Console, a browser-based graphical user interface (GUI) 
> 2. software development kits (SDKs or libraries) for use with programming languages such as Python, JavaScript, Java, etc.
> 3. the AWS CLI 
> 4. infrastructure as code (IaC) blueprints, which are textual descriptions of cloud resources and their dependencies. 
>
> The AWS Console is mostly used to open an AWS account, to do one-off configurations, and to browse the overall state of resources used by an account.  Periodic, frequent or many interactions with AWS services are better managed through the other three options. SDKs are mostly used to develop browser- based and cloud-based applications for end users.  The AWS CLI and IaC blueprints are typically used to manage resources under an admin role. The AWS CLI is probably the fastest way to get started because of familiarity: shell scripts have been used for decades in resource management. IaC blueprints are used with systems such as Terraform or AWS Cloud Formation. Basically, you write a blueprint of your infrastructure (service architecture) as code in a declarative language (that is: you specify "*what you want*", as opposed to "how to do what you want", which is typical of procedural languages, including the Bash shell). On "running" your blueprint, the services making up your infrastructure will be created, configured to some extent, and launched. If later you update your blueprint (say, delete or add more services), your infrastructure will be updated accordingly when you run your blueprint again. As blueprints are simple text files, your can use version control with Git and roll-back to a previous version of your system, etc. The main issue with using IaC blueprints is the steep learning curve to get proficient in using the approach, the language, the target resources. IaC blueprints are suitable for managing systems that *change often* because of continuous improvements.
{: .callout}
