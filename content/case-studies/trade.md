---
title: 'Trade+'
date: 2018-11-18T12:33:46+10:00
draft: false
weight: 3
heroHeading: 'Trade+'
heroSubHeading: 'Fintech project, centered around crypto and stocks trading'
heroBackground: 'https://unsplash.com/photos/Uo40KRVStJo/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8MTF8fHRyYWRpbmd8ZW58MHwwfHx8MTY3MTMxNjkxMQ&force=true&w=1920'
thumbnail: 'https://unsplash.com/photos/Uo40KRVStJo/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8MTF8fHRyYWRpbmd8ZW58MHwwfHx8MTY3MTMxNjkxMQ&force=true&w=640'
images: []
---

[Trade+](https://www.tplus.io/) is a FinTech company, offering a wide variety of sevices: trading, banking, payments, financial insights and more.

Our partnership with them had started two years ago, assisting them in development of the core proposition: mobile app for stock and crypto trading.
DevOps team has joined right at the start of the project, setting up infrastructure, CI/CD and release strategy from Day 1.

The project from technical part is a system of .NET microservices, leveraging PostgreSQL, Redis and Kafka for storage and brokerage.
On the Infrastructure side, after careful consideration, we chose to go with Kubernetes for orchestration and AWS for cloud.

In a span of a couple months we set up the whole infrastructure: from networking, to storages on RDS, ElastiCache and Managed Kafka, to EKS for API.
Using GitOps approach and ArgoCD as a tool, we were able to streamline a development process to the point of no having any manual intrusion from developers' side. All deploys happen automatically on merging code to master branch, with tests and monitoring in place, and within 10 minutes after commit a select range of customers can already see new feature.
Together with our amazing development team, we were able to lower current Time-to-Market into 1 day - from introducing hypothesis to testing it on customers.