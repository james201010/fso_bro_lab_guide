+++
title = "Risk Profiling Prioritization"
chapter = false
weight = 23
+++


## Introduction

In the lab 'Attack Detection and Prevention', you detected the vulnerability in your environment and then observed that the policy blocked the Attack that leverages a particular vulnerability. You made sure that the policy worked as expected. You did well as this step and bought some valuable time for your DevOps and SecOps Teams to plan and implement a permanent remediation method.

<br>

## Learning Objectives

In this lab you will:

1. Understand the Risk impact of the vulnerability on your business
2. Based on the Risks and the Impact, understand the prioritization plan of the AppSec Team so the vulnerability can be remediated permanently

<br>


## Libraries Dashboard

<!-- SEC LITE VS FULL START -->

<!-- FULL -->
<!--
<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the credentials used previously to <a href="https://www.fsolabs.net/20_lab_environment/23_finalize_setup.html#verify-appdynamics-agents" target="_blank">**login to the AppDynamics controller**</a> if you've been logged out.
-->
<!-- FULL -->


<!-- LITE -->

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the credentials used previously to <a href="https://lt.fsolabs.net/20_lab_environment_lt/21_lab_login_steps.html#login-to-appdynamics" target="_blank">**login to the AppDynamics controller**</a> if you've been logged out.

<!-- LITE -->

<!-- SEC LITE VS FULL END -->

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps you used previously to [**navigate to the Secure Application Dashboard**]({{< ref "/21_understanding_app_security_state.html#appdynamics-application-dashboard" >}} "**navigate to the Secure Application Dashboard**") if you've been logged out.

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Now, let's' explore the **Libraries** that have been detected using the steps below.

1. Click on the **Libraries** tab on the top menu
2. Click on the **Highest Kenna Score** column header until you see the most severe vulnerabilities at the top of the list
   - This column tells you how many vulnerabilities with their respective Severity Levels are present in a particular Library
   - Here your Application has several vulnerable Libraries with their respective Risk Scores of 100 and 10
3. Here we see the Application name and which Tier or Service is using a particular Library 
   - It also tells us how many Nodes are affected with vulnerable Libraries 
4. Secure Application also suggests the version of the library (Remediation Candidate) to remediate those vulnerabilities in the respective Libraries


![image](/images/20_hands_on/risk_profiling_01.png)

In the above example let's say your 'teastore-webui' service is the bread and butter of your business and you can't afford any downtime with this Tier. It also has a Risk score of 10.0 with two critical vulnerabilities. This must be considered while deciding and prioritizing your remediation efforts. 

<br>


<!--
![alt text for screen readers](/images/23/libraries.png)

**(#2)** The above screen shows all the libraries that are used by our application 'Log4Shell'. 
If you remember, we had limited our scope to show results for this application only (Top Right 
corner of the above screen **(#3)**). Additionally, it also tells us the Type of the Application 
(Java in this case) and which Tier or Service is using a particular Library. It also tells us how 
many Nodes are affected with vulnerable Libraries. In our example, you know your 'Tier1' is affected 
and there is one (1) Node in this Tier that needs to be worked on.

This screen is crucial while applying a Risk Based approach towards remediation. Let us explore this further.

**(#4)** More importantly, it tells you how many vulnerabilities with their respective Severity 
Levels are present in a particular Library. Here, your Application has three vulnerable Libraries 
with their respective Risk Scores: 33.1, 5.9 and 4.3.

**(#5)** Secure Application also suggests you the version of the library (Remediation Candidate) that can 
remediate those vulnerabilities in the respective Libraries.

In the above example, let us say your Tier1 service is the bread and butter of your business and you can't afford
any downtime with this Tier. It also has a Risk score of 33.1 with two critical vulnerabilities. This 
must be considered while deciding and prioritizing your remediation efforts. 

You can now pass on this information to the DevOps Team. Your DevOps Team will be delighted to get this type of information.

-->

## Summary

In this lab, you learned how much risk a particular Library carries. It would immensely help your DevOps Team in deciding where to start from. You quickly learned which library needs to be replaced first and how much benefit might come from it.

Well done again! It was a quick lab but you now have the information for your DevOps Team so they can prioritize their remediation efforts.

<br>

## Next <span style="color: #143c76;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp;

We'll take a look at how we can use **Cisco Secure Application** for **Vulnerability Assessment & Remediation**.

<br>
