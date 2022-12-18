---
title: 'Vibo'
date: 2018-11-18T12:33:46+10:00
draft: false
weight: 2
heroHeading: 'Vibo'
heroSubHeading: 'Social network for DJs'
heroBackground: 'https://unsplash.com/photos/OuLVg5ZKphI/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8M3x8ZGp8ZW58MHwwfHx8MTY3MTI4ODYzNg&force=true&w=1920'
thumbnail: 'https://unsplash.com/photos/OuLVg5ZKphI/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8M3x8ZGp8ZW58MHwwfHx8MTY3MTI4ODYzNg&force=true&w=640'
images: []
---

[ViboDJ](https://vibodj.com/) is a music & event planning application, centered around social functions.

The project's infrastructure was handed over to us from client's previous agency. Our first action was to conduct a thorough analysis, which revealed quite unoptimized architecture - overprovisioned EC2 instances, old instance types, classic ELB, Postgres and ElasticSearch set up on EC2.

From here, we decided to move onto low-hanging fruits: containerize Java application into Docker and move to ECS with Autoscaling Group, removing almost 60% of instances, which were held on standby, and migrate from t2 to t3a instances. ELB was migrated to Application Load Balancer as well, due to ELB Classic getting deprecated.

Next steps were a bit harder: Migration of data storages.
We started with and ElastiSearch, writing a pipeline on Logstash to move from EC2 to Elastic Cloud. After a little bit more than 24 hours, migration was completed, and we were able to redeploy API instances with access to new Elastic instances. Migration was done with zero downtime and data loss.

The final touch was moving Postgres from EC2 to RDS. Despite our fears, AWS Database Migration Service was capable of moving all data within 42 hours. We did not have any custom plugins on self-hosted PostgreSQL, so after DMS has reported finished migration, we switched connection string and tested all user-cases. With that, optimization of the infrastructure was done.
