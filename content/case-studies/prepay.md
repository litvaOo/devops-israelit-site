---
title: 'PrePay'
date: 2018-11-18T12:33:46+10:00
draft: false
weight: 1
heroHeading: 'PrePay'
heroSubHeading: 'Digital wallet solution.'
heroBackground: 'https://unsplash.com/photos/pb_lF8VWaPU/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8MTF8fGRpZ2l0YWwlMjB3YWxsZXR8ZW58MHwwfHx8MTY3MTMxNzcyNg&force=true&w=1920'
thumbnail: 'https://unsplash.com/photos/pb_lF8VWaPU/download?ixid=MnwxMjA3fDB8MXxzZWFyY2h8MTF8fGRpZ2l0YWwlMjB3YWxsZXR8ZW58MHwwfHx8MTY3MTMxNzcyNg&force=true&w=640'
images: []
---

[PrePay](https://prepay.co.il) is a multi-tenant Digital Wallet platform.

For this project two things were of the heaviest priority - security and speed.
While the Terraform definitions were handed over from client's previous agency, the rest was on our shoulders: the Kubernetes definitions, Helm charts, and CI/CD. All of this had to be done in one-week term, because the client's demo for investors was long overdue, so our team had to be really fast. Thanks to our expertise, we were able to put up the working infrastructure fast enough, and demo went without a hitch. We took some time after it, refactored all parts, and now the process of starting new tenant is as simple as pushing a new branch. After that - end customers can add their DNS and start working with their own instance of application.

The big thing for this project was completing the certifications. We had to do both ISO 27001 and PCI DSS. Not only two of those simoultaneously, but in a short time as well - to ensure customers' payment information safety before the soft launch.
After initial analysis with QSA, we pinpointed two gaps: Web Security and code-level issues.

In order to resolve those, we started with an easier one - web security.
AWS WAF was enabled immediately, using OWASPs ModSecurity list of rules, AWS Guard was set up to protect us from DDoS attacks, and all security groups and routes were double-checked for allowing any redundant ports or having too broad allowed source.

The next part was securing code and supply chain.
Big chunk of it was already done by our existing GitHub settings: 2FA, encrypted secrets, etc. But a lot of things were done on the project-level as well:
1. Required test coverage of at least 90%.
2. Required linter pass.
3. Required [Trivy](https://github.com/aquasecurity/trivy) scanner for Docker security.
4. Required SonarQube for static analysis.
5. Required in-build package manager supply chain analytics: npm audit, composer, etc.
6. Required AWS scan on ECR.
7. Required proactive monitoring with ClamAV on Kubernetes level.

After setting up all of the mentioned above, we were able to find and eliminate 4 potential critical issues, as well as dozens of high and medium risks. With these elements in place, both certifications were passed in a span of a month.