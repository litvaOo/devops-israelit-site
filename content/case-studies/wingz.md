---
title: 'WingZ'
date: 2018-11-18T12:33:46+10:00
draft: false
weight: 1
heroHeading: 'WingZ'
heroSubHeading: 'E-Scooter sharing app.'
heroBackground: 'https://unsplash.com/photos/0cRfS_WyuqI/download?force=true&w=1920'
thumbnail: 'https://unsplash.com/photos/0cRfS_WyuqI/download?force=true&w=1920'
images: []
---

[WingZ](wingz.az) is an app for E-Scooters sharing, localized in Azerbaijan.

Our team were on the development staff from the very beginning of the MVP phase, so we had a chance to see it grow from zero to almost 130000+ users.
While the application itself was quite simple, consisting of one .NET and one Java app, with PostgreSQL for storage, there were two hardships to overcome:

1. High requirements for uptime and latency - we didn't want someone's scooter get locked on full-speed just because the server went down.
2. Tight budget - especially in the beginning, before validating the idea, we had no luxury of high redundancy.

So, with these two things in mind, we delved deeper into the AWS, settling on the following solution:
1. Postgres-compatible Aurora with read-replicas: with no to negligble difference in cost to usual Postgres, our benchmarks have shown higher performance and lower latency with Aurora. Complacent with Graviton-type instances, this was our best bet in terms of performance-to-cost ration.
2. ECS on EC2 for API: we didn't see any need for a complex orchestration for only two instances, so we used simple ECS for deploying and scaling our apps. EC2 was chosen as a capacity provider due to being cheaper than Fargate and providing better reservation options.
3. Reserved and Spot Instances for Autoscaling: we had used a 1:1:1 ratio in our Autoscaling groups, by reserving a third of instances for guaranteed performance and availability, and then leveraging on-demand and spot instances in halves to save cost, while scaling for increased loads.

This setup has given us a needed uptime of 99.95%, while keeping the overall cost of infrastructure less than a 1000 USD.