---
layout: lesson
root: .
---
The Bash shell scripts that automatically manage multiple AWS instances will be referred to as the "Scripts". 

The Scripts are to be run in a Linux terminal running the Bash Shell.

The Scripts have **not** been tested for compatibility with other shells, or on MacOS or Windows using the Git Bash program. The course does not cover such compatibility issues.

The Scripts make use of (invoke) the `aws` CLI (command line interface), a program that is able to request operations (create, allocate, .., delete) on any AWS service: an instance, storage, a domain name, etc. Hence, you will download and configure the `aws` CLI on your Linux machine. The configuration needs to be made only once and consists of setting up the credentials (private and public keys) that `aws` CLI will use on requesting services operations. The credentials will be generated from within your AWS Account using the AWS Console when configuring your AWS account.

> ## Note --- There are four ways to access and manage AWS services:
> (1) the AWS Console, a browser-based graphical user interface (GUI); (2) the `aws` CLI just mentioned; (3) software development kits (SDKs or libraries) for use with a programming language such as Python, JavaScript, etc.; and (4) infrastructure as code (IaC) blueprints, which are textual descriptions of cloud resources and their dependencies. 
>
> The AWS Console is mostly used to open an AWS account, to do one-off configurations, and to browse the overall state of resources used by an account.  Periodic or frequent interactions with AWS services are better managed with the other three options. SDKs (libraries) are mostly used to develop cloud-based applications for end users.  The `aws` CLI and blueprints are used to manage resources under an admin role. The `aws` CLI is the fastest way to get started because of familiarity: shell scripts have been used for decades in resource management. IaC blueprints are used with systems such as Terraform or AWS Cloud Formation. Basically, you write a blueprint of your infrastructure (service architecture) as code in a declarative language. On "running" your blueprint, the services making up your infrastructure will be created, configured and launched. If later you update your blueprint (say, delete or add more services), your infrastructure will be updated accordingly when you run your blueprint again. As blueprints are simple text files, your can use version control with Git and roll-back to a previous version of your system, etc. The main issue with using IaC blueprints is the steep learning curve: the language, the target resources, etc. IaC blueprints are justified for large systems that change often because of continuous improvements.
{: .callout}

This lesson will guide you to create and configure your AWS account and to configure your Linux machine with the `aws` CLI.

The content of the lesson is organised around AWS **personal accounts**. Personal accounts are created and configured by the end users of the account. In constrast, **institutional accounts** are created and configured by the IT department of an institution, and only then passed to the end users who can further configure their account but only to some extent. Institutional accounts may be configured to only use AWS services in a single region (in USA, Europe, etc.), or to access AWS services using specific security applications, among other restrictions. 

> ## Are you using an institutional AWS account?
> If so, you are very likely to be using specific security applications to access your account. For instance:
> - to access the AWS Console with our institutional (yet for personal use) AWS account, we use the applications `Shibboleth` and `Duo Mobile`. `Shibboleth` runs in the browser to ask for our username, password, and a pushed notification from `Duo Mobile` in our mobile phone. 
> - to access AWS services through the `aws` CLI, invoked either from a script or from a terminal in our Linux machine, we need to previously run the application `saml2aws` to generate a token that is valid for 1 hour, and run it again as needed.
>
> The course does not cover the configuration and use of those or similar security applications which may be used in your institution. Your IT department will be able to help you. 
{: .callout}

If you already have an AWS account, either personal or institutional, you can use that account and skip the first episode, *1. Create Your AWS Account*. However, you should check the second and third episodes, *2. Configure Your AWS Account* and *3. Configure Your Linux Machine*, as the configuration of your AWS account and the configuration of the `aws` CLI in your machine must "match". Please note that, to access AWS services through the `aws` CLI, the configurations shown in episodes 2 and 3 do work with our institutional (personal) AWS accounts. 

We developed, mantain and run the Scripts in a Linux machine. However, there is a remote option that can be used with both personal and institutional AWS accounts.  The **AWS CloudShell** is "a browser-based \[Linux Bash\] shell that gives you command-line access to your AWS resources".  CloudShell comes with the `aws` CLI installed and ready to run using the credentials that you use to login to the AWS Console. You must be logged in to the AWS Console to be able to run CloudShell.  

We have run the Scripts within CloudShell. No changes to the Scripts were required. 

How to use the CloudShell to run the Scripts is shown in the last episode.
