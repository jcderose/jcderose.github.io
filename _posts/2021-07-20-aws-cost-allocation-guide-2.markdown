---
layout: blog-post
title:  "AWS Cost Allocation Guide: Aggregating and Assigning Cloud Costs"
date:   2021-07-20 15:44:57 -0700
categories: cloud cost-allocation finops aws cloud-cost
permalink: /aws-cost-allocation-guide-2
blurb: Understanding AWS spend is a big pain point for companies, but cloud cost allocation can help. In the second part of this series, we're focusing on what to do with your cloud cost data once it's generated.
---
NOTE: This content originally posted on the [Duckbill Group Blog](https://www.duckbillgroup.com/blog/aws-cost-allocation-guide-aggregating-and-assigning-cloud-costs/). 

Understanding AWS spend is a big pain point for companies, but cloud cost allocation can make the process easier.

Cloud cost allocation helps you identify, aggregate, and assign cloud costs along team, product, and business lines.

Once you’ve built (and socialized!) your process for identifying cloud costs, AWS will start churning out spend data along the parameters you chose — but that’s not immediately obvious. It won’t be reflected in your total monthly spend, and it won’t show up in your PDF bill. To leverage that data, we’ll look at the last two steps of cloud cost allocation: aggregating and assigning your cloud costs.

This article is part two of our AWS Cost Allocation Guide series. We’re giving you the tips to create your very own cloud cost allocation process and keep it relevant as your organization changes. Check out the first article in the series for help [identifying your cloud costs]({% post_url 2021-04-27-aws-cost-allocation-guide-1 %}), a critical first step in the process.

## Aggregating cloud costs with 1st-, 2nd- and 3rd-party solutions

AWS is building these magnificently complex reports for you with tons of data. Now what? It’s time to aggregate that data in a way that makes it insightful and actionable.

You’ve got multiple options for aggregating cloud costs depending on where you are in your cloud cost maturity journey.

* **Excel.** Let’s not kid ourselves here — your best bet may be [a handful of spreadsheets and formulas](https://github.com/aws-samples/aws-cost-explorer-report) if you’re just starting out in your journey or if you don’t have AWS console access.

* **Cost Explorer.** We can’t rule out this classic option. Cost Explorer has a number of [default reports](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/ce-default-reports.html) that can be easily tweaked to group spend by linked account or cost allocation tag. However, Finance (and Leadership) might not have access to Cost Explorer, so [that data needs to be exported](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/ce-saving.html) to be shared in internal reports.

* **[AWS Cost Categories](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-cost-categories.html).** These let you group spend based on accounts, tags, resources, or charge types. While it’s an easy way to group these expenses at a very high level, resource tagging still provides a more granular view and metrics from dynamic architectures.

* **The [AWS Cost and Usage Report](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html).** Because you’ve already [enabled your Cost and Usage Report](https://docs.aws.amazon.com/cur/latest/userguide/cur-create.html) with hourly billing and resource IDs, right? This can provide extremely granular spend and usage insights when combined with a business intelligence tool such as Athena, Quicksight, Tableau, Looker, etc.

* **A third-party tool.** Look for one that automatically groups spend for you, like Cloudability’s Business Mappings feature. While super handy, this method also requires the AWS Cost and Usage Report and a hefty price tag of 1% to 3% of your total AWS spend.

* **Your own custom, in-house tool.** Sometimes the feature set you need simply doesn’t exist in commercial solutions. We’ve seen a number of organizations with $12 million-plus annual AWS spend unable to find existing products that support their cost management strategy, leading them to build their own custom solutions. This can definitely make sense for some organizations, though I wouldn’t reach for this right off the bat.

If you’re just getting started, something simple like Cost Explorer or Excel may be all you need. But consider upgrading to the Cost and Usage Report as your organization grows. The Duckbill Group leverages the Cost and Usage Report for most of our engagements, so we highly recommend this option coupled with your BI/visualization tool of choice to get granular, resource-level breakdowns of cloud costs. AWS even provides a [CloudFormation stack](https://docs.aws.amazon.com/cur/latest/userguide/use-athena-cf.html) to get you started querying the data in Athena.

## Assigning cloud costs with the showback model
Once you’ve accurately identified and aggregated all or your cloud costs, it’s time to act on that data. Assign those cloud costs back to products, teams, and business lines to keep them accountable for their workloads. Even better, empower teams to guide their own cloud cost management journeys by sharing tailored cloud cost reports.

The easiest way to do this is with a showback model, which shows each team how much money its application(s) cost the company. If your developers consider the cloud a black box for deployments, this model provides additional information that allows them to make data-driven decisions about the cost of current features and future projects.

Once you’re allocating cloud costs, start a conversation between the Engineering and Finance teams about per-product budgets and forecasted spend. This helps both teams identify and gather the AWS spend data Finance needs to manage your organization’s money more accurately.

This is also where your holistic strategy for identifying cloud costs comes into play — you’ve already decided how to break up your costs along business lines, and now you get to see the output of that work. All of the cost aggregation solutions we mentioned in the previous section let you group costs to see how much each team, product, or business unit is spending on AWS. Finally! You’ve got some data!

This is a great feedback loop moment. Is the spend data broken up the way you need it? Are you able to make data-driven decisions with this information? If not, no sweat! Your cloud cost management strategy can be flexible — and the earlier you make these changes, the sooner you will be able to make data-driven decisions with accurate costs per team, product, or business unit.

The showback model can keep teams accountable to their cloud costs with per-product spend and forecasting — but not every team is incentivized to prioritize cost management work. As organizations grow to Enterprise levels, the AWS budget owner may not have direct influence over teams using AWS. And if the budget owner can’t influence teams to focus on spend data and optimization recommendations, those teams are less likely to adopt the organization’s cloud cost management strategy.

## Aligning cloud costs with business goals
In September 2009, author [Simon Sinek gave a TED talk](https://www.ted.com/talks/simon_sinek_how_great_leaders_inspire_action) on the difference between _what_ you do and _why_ you do it. Your cloud cost allocation work is the “what” in this scenario — the implementation method. But it’s the implementation method for a bigger purpose — the “why.”


### Why is cloud cost allocation so important?

Cloud cost allocation isn’t about optimizing or saving money — that’s a side effect. Ultimately, cloud cost allocation lets your organization accurately predict future spend as your organization grows, which leads to better forecasting and the ability to increase profits.

Once you’ve built your own cloud cost allocation model to identify, aggregate, and assign your AWS spend along business lines, there’s a critical concept your organization should explore to clearly align cloud costs with business goals: unit economics.

For those who aren’t familiar with the term, unit economics describes a business’ product in terms of revenues and costs related to a key performance indicator (KPI) that tracks closely with customer demand. That KPI can be any basic, quantifiable metric or item that creates value for the product. For example, in the airline industry, the unit economic KPI is usually a seat on an airplane. If you’re running a SaaS product, the unit economic KPI could be a single API request or a customer on the platform, depending on product architecture. Your KPI and how you break out costs to support your customers is unique to your overall business.

Once you’ve identified your product’s unit economic KPI, think about the infrastructure costs associated with it. These infrastructure costs include AWS and any other services you leverage to run the product, like Datadog, PagerDuty, Twilio, and Splunk. One simple approach to calculate your unit economic cost is to take the sum of all the infrastructure costs (including applicable third-party services) and divide that by your product’s specific unit metric.

That process works great for an organization with a single product and a single set of associated cloud costs. But let’s be real: You’re likely running multiple products across dozens or hundreds of AWS accounts. This is where your robust tagging strategy can help you accurately account for each product’s total infrastructure spend when all the cloud usage is shared.

Identifying and building your organization’s unit economic model takes work. But the [benefits of creating your unit economic model](https://aws.amazon.com/blogs/aws-cost-management/unit-metrics-help-create-alignment-between-business-functions/) are enormous. Once you know what your unit KPI costs, predicting your AWS spend is only a matter of estimating growth. That in turn allows Finance to more accurately predict Engineering spend further than just a quarter or two out.

### How cost allocation and unit economics can drive profits

There’s another less obvious benefit to setting up your unit economics model: Once you know the cost of your unit KPI and the drivers that lead to it, you can begin tweaking things to improve your margins. Imagine winning deals with competitive but profitable discounting because you know exactly what it will cost to service a new customer. That’s how you can leverage unit economics to grow your business in an increasingly competitive economic environment. Not only will you make your CFO happy with your ability to forecast the complex cloud spend, your Head of Sales will become your new best friend because you’ve given them a powerful tool to price deals more quickly and easily.


## Putting your cloud cost process into action

As you start identifying, aggregating, and assigning cloud costs to teams, you’ll need to set and clearly communicate your cloud cost management initiative as a priority. A team working on too many high-priority goals ultimately doesn’t accomplish any of those goals well, so your Engineering teams need to know that cloud cost allocation should be its number one focus.

Next, focus on changing employee behavior to ensure lasting accountability. [The Duckbill Group](https://www.duckbillgroup.com/) has seen lots of short-lived cost optimization initiatives because organizations do not invest in guided behavior change. To ensure long-term cloud cost accountability, your Engineering teams need to make cloud cost a valuable part of their conversations. This might include adding “cost” as a talking point when discussing any new architecture or feature, pulling in one or two optimization recommendations during each quarterly planning session, or spending at least one sprint per quarter [reviewing cost optimization opportunities](https://www.lastweekinaws.com/podcast/aws-morning-brief/balancing-cost-optimizations-and-feature-work/).

You can also reinforce ideal behavior by redesigning systems to promote that ideal behavior. Your technical systems (e.g., CI/CD pipelines, change management, etc.) must make doing “the right thing” the easiest path forward. For example, some teams may consider thinking about cost a major disruption to existing workflows. Use this opportunity to highlight how easily teams can gain insights from your cloud cost aggregation solution. Easy, convenient user experience in technical systems will lower the barrier to entry for most cost conversations.

Similarly, leadership can reinforce and socialize exemplary behavior. Research shows that [employees are far more likely to engage in an activity](https://www.sciencedirect.com/science/article/pii/S0065260108603305) if they know other people in the team or department are participating too. For example, one organization we worked with had surprisingly great coverage of their cost allocation tag “product code,” which led to extremely accurate AWS spend reports for each product. These reports empowered product owners, finance teams, and leadership to make data-driven decisions with highly accurate per-product information. This also prompted a healthy level of peer pressure on product teams who weren’t tagging their resources accurately, proving that higher tagging compliance led to better and more useful data for them.

All of this work is only viable so long as you maintain it. Think of it like a plant: You have to water, trim, and maintain it over time to make sure it can grow and thrive. In the next part of our AWS Cost Allocation Guide, we’ll discuss how to keep your cost allocation plan in tip-top shape as your organization grows and how to train teams to stay compliant.