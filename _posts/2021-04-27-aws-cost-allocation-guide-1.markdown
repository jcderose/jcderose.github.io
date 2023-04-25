---
layout: blog-post
title:  "AWS Cost Allocation Guide: Identifying Your Costs"
date:   2021-04-27 15:44:57 -0700
categories: cloud cost-allocation finops aws cloud-cost
permalink: /aws-cost-allocation-guide-1
blurb: Understanding AWS spend is a big pain point for companies, but cloud cost allocation can help. In the first part of this series, we're focusing on what cloud cost allocation is, and how to gain visibility into your cloud spend.
---
NOTE: This content originally posted on the [Duckbill Group Blog](https://www.duckbillgroup.com/blog/aws-cost-allocation-guide-identifying-your-costs/). 

At The Duckbill Group, our clients repeatedly tell us the same thing: **We need to know why our AWS bill went up**. In fact, gaining better visibility into your cloud spend is one of the biggest pain points you will encounter with AWS.

For organizations moving from the data center world, [AWS is a completely different cost model](https://www.10thmagnitude.com/opex-vs-capex-the-real-cloud-computing-cost-advantage/) and requires retraining how you think about costs. Even for cloud-native organizations, [different AWS services bill usage in different ways](https://www.lastweekinaws.com/blog/the-various-billing-philosophies-of-aws/), often unexpectedly so.

The best way to solve this problem—to create that visibility—is by improving your cloud cost allocation practices.

## What is cloud cost allocation?

Cloud cost allocation is the process of identifying, aggregating, and assigning cloud spend to your organization’s teams, business units, products, etc. When it’s done effectively, cloud cost allocation can have lasting positive impacts on how your business manages cloud costs.

In the next few blog posts, we’ll walk through each step of the process with you to help you understand not just what to do but why doing it is so important.

Better visibility into your cloud spend starts with identifying your cloud spend—especially as it pertains to your teams, business units, products, etc. Until you know which teams’ resources live where, you won’t be able to accurately allocate costs to those teams.

Duckbill has seen three successful methods for identifying cloud costs: user-defined cost allocation tags, hierarchical account separation, and third-party tooling.

## User-defined cost allocation tags

Whether you only have a single AWS account or hundreds of accounts spanning multiple subsidiaries and business units, [user-defined cost allocation tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/custom-tags.html) are the best place to start identifying your cloud costs.

AWS won’t show your tags in Cost Explorer (or the Cost and Usage Report) until you [enable them in your account](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/activating-tags.html), so make sure those tags are enabled in the AWS Billing console as soon as you start tagging resources. Additionally, Cost Explorer doesn’t backfill spend data for tagged resources once they’re tagged, so the sooner you add tags to your resources, the sooner you’ll have more accurate cost allocation visibility.

There’s lots of existing documentation that talks about which tags you should use. But we ultimately want to highlight the importance of the tagging strategy itself.

### Tagging doesn’t have to be the worst

It seems like every blog post that talks about “how to save money” tells you to tag your resources. But that advice feels much the same as when your doctor tells you to eat healthier.

Of course, we all know we should eat more veggies. But the doctor’s advice doesn’t teach us anything new about veggies. What we need to learn is how to make vegetables taste more delicious so that we’ll choose to eat more of them.

In other words, our veggie consumption (er, lack of) isn’t because we don’t know that we should eat more. It’s because we’re never looking forward to a heaping plate of unseasoned lima beans.

Likewise, tagging your resources just for the sake of tagging won’t help your organization because you’re missing the crucial component: strategy.

### Teamwork makes the (tagging) dream work

Tags are for more than just billing or finding out “who spun up this x1e.32xlarge host?” (Trick question! The answer is always **you**.)

For the best results, start your tagging efforts as a series of holistic conversations with different teams. Bring together Finance, Product, and Engineering/Operations to talk about how each team leverages tagging to benefit their work.

For example, Security might use tags for audits and patch compliance while Finance uses them to identify cloud spend allocated to development work for tax credits. Both are completely valid use cases for different reasons and both generate different requirements for your organization’s tagging policy.

Collaborate to create a purposeful tagging strategy—one that will incentivize Engineering teams to commit to tagging because it will actually enable them to do their job more easily and more effectively. Socializing each team’s tagging requirements provides business context for why including each tag is so important and is a great way for your engineers to create shared purpose and belonging within the organization.

What starts as two teams collaborating can turn into a grassroots effort to improve tagging across the organization, and lead to a community of practice for tagging best practices. Once you have a tagging strategy that everyone agrees on, you need to shout it from the rooftops.

Track your tagging success (or lack thereof) at a similar granularity across teams or products. Celebrate teams that tag all their resources, thus improving the accuracy of your cost allocation, and socialize their workflows with other teams who may be struggling to tag or get value from their tags.

For more information, check out AWS’s “thrilling” 24-page [Tagging Best Practices Whitepaper](https://d1.awsstatic.com/whitepapers/aws-tagging-best-practices.pdf). Don’t let the length or the undoubtedly “edge of your seat” storyline sway you from giving it a quick perusal. It includes a slew of helpful use cases for various tagging strategies to fit nearly every business need. [We’ve also written our own guide to tagging.](https://www.duckbillgroup.com/blog/aws-cost-allocation-guide-tagging-best-practices/)

## Hierarchical account separation

Most (but not all!) AWS usage types are taggable. This means even when you tag everything in AWS, you’re still going to end up with “untagged spend” in your cost allocation model.

It’s annoying, right?

How do you allocate that untaggable spend without hours of spreadsheets and resource-specific utilization metrics? By moving resources into separate AWS accounts for each team, product, or business unit.

First, create separate AWS accounts for each of your core cloud-related administrative functions—like security, logging/monitoring, identity, and shared tools (CI/CD). AWS accounts are free, so there are no extra charges here.

Next, create accounts in a standardized manner based on your organization’s brands and products. The most common and effective pattern we have seen adopted is one account per environment per product.

If your organization has multiple brands each with multiple products, you may want to create one account per environment per product **per brand**. Should a given brand desire more environments (staging, QA, etc.) or further security boundaries for special cases, additional accounts should be created within the same pattern.

While it’s still not perfect, AWS’s [native](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html) tooling has made massive improvements in the last few years to make multi-account creation and management a breeze.

Access to production or entire brands can easily be controlled with this arrangement. (Remember, account boundaries are the only hard security limits within AWS!) We recommend having some staff with full access to all accounts so organization-wide changes are quick and easy, but still secure and auditable.

## Third-party tools

Third-party tools **can** accomplish the same goals as the above two methods. But the cost allocation features you’ll want are usually bundled into a larger suite of cost management tools that will cost you 1% to 3% of your total AWS spend.

For example, in addition to helping you allocate your costs, SaaS platforms like Cloudability and CloudHealth provide customizable dashboards, insights, and forecasting capabilities that may or may not be what you need right now in your cost allocation journey.

And chances are you’re not utilizing your third-party tooling to its full potential. That’s not a knock against you—it’s just a common occurrence we see with powerful software that has so many bells and whistles. That hefty price tag provides you with solid features. But unless your organization is full of power users for these tools, you’re likely not getting the best bang for your buck.

Plus, if you don’t have a strong cost allocation policy in place before utilizing these tools, you’re going to have a much harder time accurately identifying cloud costs within these tools.

In our experience, clients have generally found the price tag to not be worth the results.

## Building blocks for success

Whew, that’s a lot to digest!

I know tagging and account migrations doesn’t sound glamorous or exciting. But remember, you have to crawl before you can walk. In other words, you have to identify cloud costs before you can get visibility into your cloud costs.

And this process takes time.

It’s not just about how you break up your costs, but **why** you break up your costs—what are you ultimately trying to accomplish by breaking up your costs?

Talk with your engineers. Talk with Finance. Heck, talk with Product and Security and Leadership. All stakeholders should buy-in to your process for identifying cloud costs before you implement it, because all of them will depend on the results.

[In the next part of our guide]({% post_url 2021-07-20-aws-cost-allocation-guide-2 %}), we will discuss implementing your cost allocation process by aggregating and assigning cloud costs. This is the place where your organization becomes empowered to make data-driven decisions on optimizing cloud spend. It’s where the true magic happens.