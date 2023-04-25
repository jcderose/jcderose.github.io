---
layout: blog-post
title:  "AWS Cost Allocation Guide: Tagging Best Practices"
date:   2021-02-23 15:44:57 -0700
categories: cloud cost-allocation finops aws cloud-cost
permalink: /aws-cost-allocation-tagging
blurb: Looking for AWS tags you can implement immediately? We’ve got you covered.
---
NOTE: This content originally posted on the [Duckbill Group Blog](https://www.duckbillgroup.com/blog/aws-cost-allocation-guide-tagging-best-practices/). 

“Are your resources tagged?”

Every engineer has heard this at some point. They may have even said it. Love it or hate it, resource tagging is a topic every engineer has a stance on, from “we’re not big enough for that yet” to “of course! we automatically tag non-compliant resources, too” — and everything in between.

But why? Why is resource tagging important?

It’s not just about tag coverage, though that’s important, too. Resource tagging is part of a bigger business goal: mapping cloud costs directly to your applications and projects, otherwise known as cloud cost allocation. When it’s used effectively, cloud cost allocation can have lasting positive impacts on how your business manages cloud costs.

Not sure where to start with your tagging strategy? [Duckbill Group](https://www.duckbillgroup.com) has seen three successful methods for identifying cloud costs: user-defined cost allocation tags, hierarchical account separation, and third-party tooling. Keep reading to learn which makes the most sense for your business.

### User-Defined Cost Allocation Tags

AWS provides two kinds of cost allocation tags for cost allocation purposes: AWS-generated tags and user-defined tags.

As the name implies, AWS-generated tags are added automatically when resources are created within certain AWS services (e.g., resources created by a CloudFormation stack automatically receive “aws:cloudformation:*” tags). However, these tags’ keys differ from service to service, so they aren’t a great way of measuring spend across an entire account.

User-defined cost allocation tags, on the other hand, are created by you (i.e., the user) and can be applied uniformly across most AWS resources in any given account. This makes user-defined cost allocation tags one of the best strategies for measuring cloud spend accurately across your business’s teams, products, business units, etc.

Now the important question: What should your cost allocation tags be?

Do you want to identify and measure spend per team? Per product? Per application environment? There are lots of different ways to slice and dice your cloud costs, but it ultimately depends on what’s going to be most helpful for you and your organization.

Note we say organization here—not just Engineering. Finance, Product, and even Security or Leadership may have a say in which tags will help them make data-driven decisions.

As a starting point, Duckbill Group recommends the following tags:

* **Name** : This tag is often built-in for many AWS resources, but it’s oddly lacking for others. Enabling this as a cost allocation tag will allow you to report costs on individual, named resources.

* **Service** : This refers to the service a resource belongs to. Along with Name, this tag can have a multitude of potential values; attempting to maintain tight control on all possible values will lead to frustration. Instead, we recommend paying more attention to the consistency of this tag application (e.g., “all resources attributed to service Foo have the tag Service:Foo”) rather than trying to enumerate every possible value from the outset (e.g., “all resources must be deployed with one of the following Service values: Foo, Bar, Baz”).

* **Environment** : This tag outlines which application environment a resource belongs to. Possible values might include production, staging, qa, and development.

* **Owner** : This tag tracks the email address of the person who created the resource. For teams using Infrastructure as Code tools like Terraform or CloudFormation, this often winds up being a shared user; we recommend ensuring that each user spinning up resources is doing so with their own account so this tag remains accurate.

* **Product** : This tag’s potential values should include your product or brand lines, plus an additional value for organization-wide resources like CI/CD, logging and monitoring infrastructure, and SIEM infrastructure.

* **Accounting** : This allows Finance to accurately report on accounting lines. Duckbill recommends three possible values: Cost of Goods Sold (“COGS”), Research and Development (“R&D”), and General and Accounting (“G&A”). G&A is usually the default value for this tag, as it includes anything that isn’t directly involved in providing service to a user (COGS) or development of new features for a user (R&D).

* **DataClassification/Compliance** : This key denotes whether the resource contains any Personally Identifiable Information (PII) as defined by regulations like [GDPR](https://gdpr-info.eu/issues/personal-data/), [HIPAA](https://www.virtru.com/blog/phi-vs-pii/) or internal [SOC2](https://www.imperva.com/learn/data-security/soc-2-compliance/) compliance. Security will thank you later for knowing which resources contain PII and configuring restricted access on them. Possible values might include sensitive (e.g. resources containing PII) and standard (e.g., resources not containing PII).

* **bucket-name** : This key is only used for S3 resources, as it denotes each S3 bucket name. We recommend this key separately from the Name key above to make S3 cost visibility easier.

There are two major caveats worth highlighting for this method.

First, cost allocation tags will need to be applied to resources and [activated in the AWS console](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/activating-tags.html) before they can be leveraged for reporting purposes. AWS doesn’t backfill historical tag data, so the sooner tags are added to your resources and activated in the console, the sooner you’ll be able to accurately slice and dice your cloud costs.

Second, most (but not all!) AWS usage types are taggable because—in typical AWS fashion—[not everything follows the same model](https://www.lastweekinaws.com/blog/the-various-billing-philosophies-of-aws/). This means that even when you tag everything in AWS, you’re still going to end up with “untagged spend” in your cost allocation model. You’re not going crazy; that’s expected.

With that said, we’ve seen highly mature organizations tag roughly 85% to 90% of their AWS usage, meaning only 10% to 15% of AWS usage is untagged. This provides enough accuracy in the cost allocation data for teams to make informed decisions.

### Hierarchical Account Separation

Now, we know what you’re thinking: “We’re talking about tagging—not accounts.”

As your engineers can attest, tagging doesn’t always provide the level of granular cost visibility desired. However, separating your AWS resources into accounts along business lines provides additional accuracy for your cloud costs.

By taking this approach, all spend related to a given business unit lives in a single AWS account and can be easily attributed back to that business unit, whether the resources in that account are tagged or untagged. Win-win.

Duckbill Group recommends a set of core AWS accounts to start, plus supplementary accounts as necessary for your organization’s brands and products.

#### Core Accounts

The core of a scalable, secure account infrastructure is four accounts:

1. The root payer account ("the management account"),
2. A security account,
3. A shared tools account, and
4. An identity account.

| **Account Alias** | **Purpose** |
| ----------------- | ----------- |
| acmegroup-root | Contains the [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) configuration linked to all subaccounts, thereby functioning as the root payer account. All organization-wide Service Control Policies are controlled here. Reservations like Savings Plans and Reserved Instances should be purchased in this account to allow them to apply organization-wide to subaccounts. |
| acmegroup-security | Contains all security and logging tools (SIEM), vulnerability and audit scanners, and CloudTrail logs. Access should be restricted to security personnel only. |
| acmegroup-tools | Contains organization-wide shared tooling, such as CI/CD systems, self-hosted version control systems or configuration management systems, container or AMI repositories, centralized logging, etc. These are often systems that don’t fit neatly in a brand-specific account or an environment-specific account; segmenting these tools off improves security posture. |
| acmegroup-identity | The termination point for all access control. If your organization leverages an SSO solution, it should be integrated with this account via IAM policies controlling access to all linked accounts. [AWS SSO](https://aws.amazon.com/single-sign-on/) is recommended for this. This configuration will allow your organization to track access across all accounts and establish complete audit trails. |  

<br/>

### Brand Accounts

Beyond the core account structure, we recommend establishing a consistent pattern for accounts for each brand.

The most common and effective pattern we have seen adopted is one account per environment per brand. That might look like this:

| **Account Alias** | **Purpose** |
| ----------------- | ----------- |
| brandA-prod | Brand: Brand A Environment: Prod |
| brandA-dev | Brand: Brand A Environment: Dev |
| brandB-prod | Brand: Brand B Environment: Prod |
| brandB-dev | Brand: Brand B Environment: Dev |  

<br/>
Should a given brand desire more environments (e.g., staging, QA, etc.) or further security boundaries for special cases, additional accounts should be created within the same pattern.

Access to production and entire brands can easily be controlled with this arrangement. (Remember: Account boundaries are the only hard security limits within AWS!) We recommend having some staff with full access to all accounts so organization-wide changes are quick and easy but still secure and auditable.

### Third-Party Tools

While Duckbill generally recommends the above two methods for cost allocation, third-party tools can provide additional value-add—but at a price.

SaaS platforms like Cloudability and CloudHealth have some really neat cost allocation features, like attributing non-taggable spend to a given team, product, or business unit, or attributing spend from misspelled tag values to their correct tag value.

But if you don’t have a strong tagging policy in place to begin with, you’re going to have a much harder time leveraging these tools to accurately identify cloud costs for each team, product, or business unit.

And chances are you’re not utilizing your third-party tooling to their full potential. That’s not a knock against you. It’s just a common occurrence we see with powerful software that has so many bells and whistles. That hefty price tag provides you with all these amazing features, but unless your organization is full of power users for these tools, you’re likely not getting the best bang for your buck.

### How can you audit compliance?

Tagging compliance is hard. Socializing the benefits of tagging may incentivize some engineers to champion your tagging policies, but all the socializing in the world may not help your teams implement and use those tags. For the best results, you may need to take a more targeted effort towards tag adoption.

There are two main strategies to enforce tagging within your organization.

The first is to enable the continuous monitoring of your AWS resources and notify the appropriate teams and users when their tag usage falls out of compliance.

The second strategy, more commonly found in cloud-mature organizations, takes a hard-nose approach towards tag enforcement by stopping or terminating resources that do not meet the predefined requirements. This one requires significant buy-in from the organization because pulling the rug out from your engineers may not win you many friends at the lunch table.

There is a case to be made that companies should adopt both of these strategies over time. If you’re just starting your cost allocation journey, you may want to start with monitoring and communication to get everyone on the same page before implementing tooling that stops or terminates resources.

Here are some tools Duckbill has seen over the years that can help with either strategy:

* [Cloud Custodian](https://cloudcustodian.io/) : Cloud Custodian is an open-source solution that allows users to [scan a given AWS account](https://cloudcustodian.io/docs/aws/examples/tagcompliance.html) for any taggable AWS resources that don’t have a given tag key/value pair and take actions accordingly. The output is clunky and needs massaging before being presented to stakeholders, but it’s the best tool we’ve seen for catching taggable, untagged resources. Plus as your cost allocation practices mature, you can leverage other Cloud Custodian’s other [heavy-lifting capabilities](https://cloudcustodian.io/docs/aws/examples/index.html)—like automatically stopping or terminating resources deployed without the appropriate tags. Want to leverage all these features without running the software yourself? Check out [Stacklet](https://stacklet.io/), a commercial effort by the creators of Cloud Custodian.

* [AWS Config](https://aws.amazon.com/config/) : AWS Config lets you set compliance rules (e.g., “all EC2 instances need the Application tag”) and tells you when resources are noncompliant. The trouble is that the only built-in rule (i.e., “required-tags”) focuses on EC2 instances. If you want to check for other tags, you’ll need to create a custom Config rule. Plus, the UI is a bit clunky.

* [AWS Organizations Management Tag Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_tag-policies.html) : Similar to Cloud Custodian, AWS Organizations Management Policies will proactively prevent resources from being deployed with incorrect or noncompliant tags. Note that this solution requires AWS Organizations, and should only be implemented as an advanced practice after you’ve standardized and socialized your tagging policy. As the documents linked above suggest, “It's especially important to understand a tag policy's effects before you _enforce_ compliance with any tag policy.”

* [AWS Resource Groups](https://docs.aws.amazon.com/ARG/latest/userguide/welcome.html) : This groups resources by user-defined parameters. These groups can be created by Infrastructure as Code tools, but the application of a given tag to resources within a group requires console access—which can break scalable automation and introduce human error.

### Which strategy is right for you?

No matter which strategy you choose to take with tagging your resources, know that the only way to ensure ongoing success is to have a plan for monitoring and compliance—and stick to it.

Creating a process or even—_gasp_—[automating your tagging remediation](https://aws.amazon.com/blogs/mt/monitor-tag-changes-on-aws-resources-with-serverless-workflows-and-amazon-cloudwatch-events/) will help make sure you are never falling behind on tag coverage.

Every organization is different, so tagging strategies that work for one organization might not work for another. The goal is to get accurate data to decision makers so they can make informed decisions. Still not sure where to start? No worries, we’re happy to help. [Schedule a time to chat today.](https://www.duckbillgroup.com/services/cloud-finance-analysis/)