---
title: 'PassItForward'
date: 2018-11-18T12:33:46+10:00
draft: false
weight: 1
heroHeading: 'PassItForward'
heroSubHeading: 'Charity and donations platform.'
heroBackground: 'https://passitforward.com/main-background.a350cee29a71cb06b7ce.png'
thumbnail: 'https://passitforward.com/assets/images/home/home-static-nonprofit/trusted-by-change.png'
images: []
---

[PassItForward](https://passitforward.com) is a platform for croudfunding of the charity projects.

Before joining our company, the infrastructure development was quick, but chaotic. At one point, the whole infrastructure was heavily overprovisioned.
While the general state of the cloud was satisfactory, the costs were over the roof for a simple app of one Node.js backend and two SSR front-ends.

We started with installing an APM and monitoring, in this case - New Relic. After a week of data collection, we were able to check two things.
1. Performance bottlenecks.
2. Which parts were overprovisioned.

This included a heavy cooperation with development team. Within a two-week sprint, most of the heavy bottlenecks were patched. Having these part, we proceeded to reducing instance count.
An obvious solution for this case was leverage of AutoScaling groups: we moved all EC2s under an ASG, using 1:2 ratio between in-demand and spot instances. This move already saved us 40% in bills.
Fortunately, PassItForward's team consists of strong believers in the project, so for our day-to-day capacity we were able to put reservations in place for 3 years, all upfront. After making a purchase, the total savings in the span of three years were cut by almost 80%, giving the team a much needed breathing room in terms of budget.
