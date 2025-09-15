---
layout: blog-post
title:  "Controlling Cloud Costs with Culture"
date:   2022-10-25 15:44:57 -0700
categories: cloud writing management leadership finops
permalink: /controlling-costs-with-culture
cross-post-dest: dev.to
cross-post-url: https://dev.to/jcderose/controlling-cloud-costs-with-culture-26jc
image: assets/images/blog/oo2t0jnp5tk0bsv4z8tp.webp
image-credit-url: https://www.pexels.com/@fauxels/
image-credit-text: Fauxels
blurb: 
---
As companies move more workloads into public cloud platforms like AWS, GCP, and Azure, managing those costs becomes more important and more complex. Even when armed with Cloud Financial Management (CFM) frameworks and best practices, a lot of companies still struggle to manage their cloud spend. To succeed long-term, companies also need to focus on the people involved, creating a cost-conscious culture that ensures employees are engaged and on board. 

In this article, we'll dive into why frameworks and best practices aren't enough and three key steps to create a cost-conscious culture that will lead your company into its CFM golden age.

## Why frameworks and best practices aren't enough
I've spent the last three years helping organizations succeed in their CFM journeys, and I noticed a trend. We'll take one client as an example.

The organization's CFM journey started when someone in senior leadership noticed cloud spend was "too high". Maybe it spiked astronomically from last month, or maybe it was growing slowly month over month, year over year. To solve this problem, the VP of Engineering decided to cut spend 20% over the next 6 months.

Extensive research supplied reactive, short-term suggestions like purchasing reservations or turning off unused resources. The VP dropped tickets into their teams' queues, those teams performed the work in upcoming sprints, and cloud spend dropped. Fantastic.

With the tickets completed, teams returned to their regularly scheduled backlog. And that's when it happened–the org's cloud spend slowly climbed up and up again, and the organization was back where it started. ([The Duckbill Group refers to this as the cloud cost cycle of pain](https://www.duckbillgroup.com/resources/unconventional-guide-to-aws-cost-management/).)

I saw this trend in organizations of all shapes and sizes: employees completed the CFM work that was asked of them and then went back to their day job. And that's no fault of their own–they were hired to build and maintain their company's rock-star product. They're incentivized to focus on shipping code. 

This is why CFM frameworks and business practices aren't enough–by themselves, they're not part of an organization's "business as usual". Employees won't necessarily embody these ideas on their own. To change that, you need technical solutions and people solutions. For a CFM practice to be successful, to ensure "business as usual" includes CFM work, you need a cost-conscious culture.

## Do I really have a culture problem?


![via GIPHY](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tbje5eydh31o5wjww5r5.gif)

I know, I know–you're probably thinking "I don't have a culture problem." 

Well. 

In the [2022 State of FinOps Survey](https://data.finops.org/), 30% of all respondents said making engineers take action was the biggest challenge they faced. 

<img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yrcspdv39z1c5eorxcdq.png" alt="via data.finops.org" width="600" height="500">

An additional 22% reported struggles with organizational adoption of FinOps. 

<img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5652qwlvj4ih0gk8f9jg.png" alt="via data.finops.org" width="600" height="500">

That's 52% of respondents who said their main challenge in implementing CFM practices was related to culture. **That's right, over half of respondents expressed culture change as a major hurdle for successful CFM practices.**

If you're struggling to keep your cloud spend under control, you may have a culture problem. And you're not alone–lots of companies are experiencing the same thing.

I get it–culture change is hard. Nobody wants to admit they have a culture problem and even if they do, finding a solution is challenging. But fear not! The organizations who built successful CFM practices shared three key business practices that you can use to create your own cost-conscious culture.

## Practice 1: Leadership Buy-In and Communication
Leadership must buy-in to the importance of CFM and communicate its importance to all key players in the company. There are two major questions to think about here:

### Why does the company need to care about CFM?
If you run your company's workloads in data centers, that spend is usually classified as capital expenditure (CapEx): upfront investments, depreciated over time. But when you run workloads in the public cloud, that spend is usually classified as operational expenditure (OpEx): variable spend accrued per minute that varies day-to-day and month-to-month. [Public cloud spend can cause major spikes in ways data center spend never could](https://blog.tomilkieway.com/72k-1/). Yikes.

CFM practices create visibility into workload spend on your public cloud platforms. Think about CFM work in terms of business value: how is your public cloud spend split amongst your products and services? Is spend split evenly across all your products? Is it heavily focused in one product? Do profits for that product outweigh its cloud spend? Your bill won't give you any of these insights unless you implement CFM practices like user-defined cost allocation tags and well-labeled linked accounts.

Similarly, how is cloud spend influenced by business KPIs? If you're a SaaS company, for example, you might care about business growth as a function of the number of customers on your platform. So how much money are you spending on the public cloud for every customer you have? What's the cost of keeping each customer on your platform? Is that more than you're charging them to use the platform? CFM will help you answer those questions, and your business leaders need to set goals accordingly to prioritize that work.

Note that I say leaders and not managers–the two aren't necessarily the same. Key influential leaders can come from any level of an organization. Think about the people who are passionate and vocal about their work–those are the people you want bought-in on CFM as early as possible because they can help you champion it to other parts of the organization.

### How does this goal fit in versus other priorities?

Also note that I say leaders broadly, not just Engineering leaders. Offering a technology-based product requires input from multiple stakeholders like Engineering, IT, Security, Product, and Design. 

Leadership needs to communicate the importance of CFM work to all of those stakeholders, and ensure everyone's priorities are aligned. If stakeholders don't agree where CFM fits versus other organizational priorities, they might send mixed signals to Engineering teams. And we've all been on a team where priorities change week to week or even day to day. Nothing gets done because you're constantly shifting focus, the work that does get finished is lower quality, and your chances for burn-out increase. Nobody wants that.

Similarly, these stakeholders may have vital business context that influences Engineering teams' ability to optimize costs. For example, I worked with one team who identified terabytes of infrequently-accessed customer data that could move into a cheaper storage tier. This particular storage tier was cheaper because data in this tier was retrieved in a number of hours rather than a number of seconds. However, when the team discussed this change during a meeting, a Customer Success team member reminded them of a service-level agreement that required all customer data be readily accessible within minutes. This meant the team couldn't move the data without violating the SLA, and thus couldn't optimize that spend without changing the SLA.

## Practice 2: Incentivize Employees to Care

When leadership communicates the importance of CFM work, they're telling employees where to focus their time. But [for teams to accept this new way of working, they need to buy into it](https://hbr.org/2005/10/the-hard-side-of-change-management). And to get buy-in from employees, you need to incentivize them to change.

How each individual's incentives align with business goals will vary. Every person has different incentives so ask them what they care about. [Make them feel heard](https://hbr.org/2018/12/the-secret-to-leading-organizational-change-is-empathy). If you're their manager, bring it up in your next one-on-one. [Some key topics to consider](https://www.prosci.com/methodology/adkar): 

- What's in it for the employee? Is this an opportunity or a threat? Is your organization's CFM program going to improve their quality of work life or be detrimental to it?
- What's your organization's track record with organizational change? If your organization has successfully implemented org-wide changes in the past, employees are more likely to believe your CFM program will also succeed, and subsequently buy in.
- [What other factors are impacting the employee outside of this change](https://neuroleadership.com/your-brain-at-work/scarf-model-motivate-your-employees)? Maybe this person is experiencing instability in their team or home life and fear the new habits you're asking them to embody will create additional instability.
- What are the employee's personal values and motivators? Most of us work for money but is that our primary, driving incentive? The Great Resignation and Quiet Quitting suggest other factors might incentivize employees to show up to work every day.

Once you know what your employees care about, you need to help them build new, proactive, cost-conscious habits that support your CFM goals. Charles Duhigg's <u>The Power of Habits</u> can provide additional guidance here.

## Practice 3: Make the Happy Path the Easy Path

"The Happy Path" is a concept commonly used in product development to describe the default scenario a user experiences to complete a task with no exceptional or error conditions. Think of it as what you expect to happen when you checkout on Amazon.com, or the default process your Engineering teams follow to deploy a new feature into production. 

To build a cost-conscious culture, you need to embed proactive cost habits into your happy path workflows, into the default ways your teams work. [You need to embed proactive cost habits into the design, strategy, and provisioning processes for your engineering teams](https://www.linkedin.com/posts/dvir-mizrahi_finops-reactive-proactive-activity-6952537803251445760-tzsU). If Engineering teams aren't thinking about cloud cost in their daily work, they're not incorporating it into their daily work, and you'll end up with reactive, short-term work all over again. 

For example, your engineering team already has a happy path for deploying microservices to the cloud, likely involving a CI/CD pipeline and a documented business process. An easy way to embed proactive cost habits into this workflow is to add cost allocation tags to resources as they move through this pipeline. You could even add the tags to your Infrastructure as Code files so every resource deployed through the pipeline automatically receives tags, and is clearly allocated to a specific team or department.

Your engineering team also already has a happy path for managing development cycles, via a number of structured meetings like standups, sprint groomings, and retros. Use these meetings to proactively look at historical cloud spend or review optimization opportunities. Teams could even discuss cost as part of the architecture design process–does your new microservice really need 16 vCPU and 64 GB RAM at all times? Or can you autoscale smaller compute resources as demand fluctuates? 

These changes require a little engineering effort upfront but ultimately allow you to gather the cloud cost data you need and teams to stay focused on what they do best. It's a win-win.

For teams to embrace proactive, cost-conscious habits, they need to be surrounded by tools and processes that incentivize those habits. That's the happy path idea. But not every tool and process in your organization is designed to incentivize those new habits. A lot of them might actually incentivize teams to revert to old habits that are counterproductive to your CFM goals. 

This leads to the easy path portion of our discussion. Have you ever tried to complete a task and found the default workflow convoluted, frustrating, or counterproductive? I've seen many teams reinvent the wheel simply because the default workflow wasn't easy or aligned with business goals. Empower teams to change tools and processes that don't foster cost-conscious habits. If employees don't shift away from old habits and behaviors, they won't embody cost-conscious habits and behaviors, and your CFM program won't be successful. 

## It's Dangerous to Go Alone

![via GIPHY](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/i8nqn6hjo3ckaubfag56.gif)

Two final thoughts: first, there will be disagreements along the way. That's okay. In fact, that's healthy. When you bring different perspectives together, they're not all going to agree. What is important is that everyone feels heard and moves forward together.

Second, culture change takes work. Yes, lots of hard work. This is not something you will implement overnight. It’s not even something you’ll see dividends in immediately. Define how you plan to measure success early, and measure often. For example, one team I worked with regularly polled employees to rate their agreement or disagreement with various statements about cost-conscious habits. Over many months of CFM work to create a cost-conscious culture, most employees reported increased alignment with, and embodiment of, cost-conscious habits.

And I get it–culture change is hard. Nobody wants to admit they have a culture problem and even if they do, finding a solution is challenging. Changing a group’s culture requires a lot of soft skill work, and that’s hard to define in terms of ROI and business KPIs so any culture change projects generally don’t happen at best or are doomed to fail with no clear path to outcomes at worst.

Focus on getting senior leadership buy-in, incentivizing your employees to care about cloud costs, and leveraging your existing tools and processes. 

Once you’ve got a cost-conscious culture, then you can introduce CFM frameworks and best practices. [Shout out to the FinOps Foundation which has done an amazing job centralizing and highlighting helpful resources](https://www.finops.org/introduction/what-is-finops/). 

And if you get stuck–no worries! Reach out to me. I’m happy to offer assistance. 
