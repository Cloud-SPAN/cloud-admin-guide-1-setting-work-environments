---
layout: lesson
root: .
---
The Bash shell scripts that automatically manage multiple AWS instances will be referred to as the "Scripts" from now on.

The Scripts are to be run in a Linux terminal running the Bash shell.

The Scripts have **not** been tested for compatibility with other shells, or on MacOS or Windows using the Git Bash program. The course does not cover such compatibility issues.

The Scripts make use of the **AWS Command Line Interface** (AWS CLI), an open source software tool that enables you to interact with AWS services using commands either in your command-line shell or within shell scripts. The Scripts invoke the AWS CLI to create, allocate, .., and delete AWS services such as instances, storage, domain names, etc., within an AWS account. Hence, the AWS CLI must both be installed in your Linux environment and be configured to be able to use and manage resources in your AWS account.

# Options to use the AWS CLI
Two options are covered in this lesson for using the AWS CLI in a Linux environment: (1) a Linux machine and (2) the AWS CloudShell. A Linux machine environment must be configured with the credentials (private and public keys) that the AWS CLI will use on requesting AWS service operations when invoked within the Scripts. The credentials will be generated using the AWS Console when configuring your AWS account. 

The AWS CloudShell is "a browser-based \[Linux Bash\] shell that gives you command-line access to your AWS resources". The AWS CloudShell comes with the AWS CLI installed and ready to run using the credentials that you use to login to the AWS Console --- that is: you must be logged in to your AWS account through the AWS Console to be able to run the AWS CloudShell.  

> ## Ways to access and manage AWS services
> There are four ways to access and manage AWS services: 
> 1. the AWS Console, a browser-based graphical user interface (GUI) 
> 2. the `aws` CLI just mentioned
> 3. software development kits (SDKs or libraries) for use with a programming language such as Python, JavaScript, Java, etc.; and
> 4. infrastructure as code (IaC) blueprints, which are textual descriptions of cloud resources and their dependencies. 
>
> The AWS Console is mostly used to open an AWS account, to do one-off configurations, and to browse the overall state of resources used by an account.  Periodic, frequent or many interactions with AWS services are better managed through the other three options. SDKs (libraries) are mostly used to develop browser- based and cloud-based applications for end users.  The `aws` CLI and IaC blueprints are typically used to manage resources under an admin role. The `aws` CLI is probably the fastest way to get started because of familiarity: shell scripts have been used for decades in resource management. IaC blueprints are used with systems such as Terraform or AWS Cloud Formation. Basically, you write a blueprint of your infrastructure (service architecture) as code in a declarative language (that is: you specify "*what you want*", as opposed to "how to do what you want", which is typical of procedural languages, including the Bash shell). On "running" your blueprint, the services making up your infrastructure will be created, configured to some extent, and launched. If later you update your blueprint (say, delete or add more services), your infrastructure will be updated accordingly when you run your blueprint again. As blueprints are simple text files, your can use version control with Git and roll-back to a previous version of your system, etc. The main issue with using IaC blueprints is the steep learning curve to get proficient in using the approach, the language, the target resources, etc. IaC blueprints are suitable for managing systems that *change often* because of continuous improvements.
{: .callout}

# Overview
This lesson will guide you to create and configure your AWS account and to configure your Linux environment with the AWS CLI. 

The content of the lesson is organised around what we call AWS **personal accounts**. A personal account is an account that is created and configured by the end user of the account: the person who is to run the Scripts. In constrast, an **institutional** (or business/school/organisation) **account** is created and configured by the IT department of an institution, and only then passed to the end user of the account who can further configure the account but only to some extent and following institutional policies. For instance, institutional accounts may be configured to use AWS services in a single region only (in USA, Europe, etc.), or to access AWS services using specific security applications, among other regulations. 

> ## Are you using an institutional AWS account?
> If your are using an institutional account, you are very likely to be using specific security applications to access your account. For instance:
> - to access the AWS Console with our institutional AWS account, we use the applications `Shibboleth` and `Duo Mobile`. `Shibboleth` runs in the browser to ask for our username, password, and a pushed notification from `Duo Mobile` in our mobile phone. 
>
> - to access AWS services through the AWS CLI, invoked either from a script or from a terminal in our Linux machine, we first need to run the application `saml2aws` to generate a token that is valid for 1 hour, and run it again as needed.
>
> The course does not cover the configuration and use of those or similar security applications which may be used in your institution. Your IT department will be able to help you. 
{: .callout}

If you already have an AWS account, personal or institutional, you can use that account and skip the first episode (in the Schedule below), *1. Create Your AWS Account*. 

If you are using the AWS CloudShell (Linux) environment, the first part of the third Episode, *3. Configure Your Linux Environment*, shows how to upload the Scripts to your AWS CloudShell and how to run them. 

If you are using a Linux machine environment, you should check the second and third episodes, *2. Configure Your AWS Account* and *3. Configure Your Linux Environment*, second part, as the configuration of your AWS account and the configuration of the AWS CLI in your Linux environment must "match". These configurations will enable a **personal account** to access AWS services through the AWS CLI. **But please note**, most likely, the configurations will also enable an **institutional account** to do so. We have successfully used these configurations with both a personal account and an institutional account that uses the `saml2aws` application mentioned above. 

