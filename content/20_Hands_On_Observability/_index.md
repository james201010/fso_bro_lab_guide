+++
title = "Hands-On Observability"
chapter = false
weight = 20
+++

**Ali is the Lead SecOps Engineer who works for Savi at Bridge to Possibili-Tea. You will be working
with Ali during this exercise. &nbsp; Your job is to make sure Ali achieves his goals for which Bridge to Possibili-Tea bought Cisco Secure Application.**

![image](/images/20_hands_on/ali.png)


---

 Ali wants to secure his application against the log4j CVE-2021-44228 vulnerability that can result in remote code execution giving complete control over the application and underlying system.

To achieve the above, we will take Ali through the following steps:

1. Access Business Risk Profile
2. Detect if the vulnerability (log4j CVE-2021-44228) is actually present in the application
3. If it is, block the attacks without even updating the code or restarting the app
4. Making sure the attacks were being blocked
5. Further investigating the attacks and the related vulnerability across all tiers of the application
6. Suggesting ways for a permanent remediation for this vulnerability

<br>

## Next <span style="color: #143c76;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp;

We'll look at the **current security state** of the application.

<br>