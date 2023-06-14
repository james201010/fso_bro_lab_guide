+++
title = "Attack Detection Prevention"
chapter = false
weight = 22
+++


## Introduction

In the previous lab 'Understanding Security State of an Application' you obtained some actionable information and learned how the Dashboard made it easy to understand the state of an application. We will explore this further in the following lab ('Business Risk Profiling and Prioritization'). But now that we know we have some open vulnerabilities that carry critical and high severity levels, our immediate priority should be to make sure adversaries are not able to exploit these vulnerabilities or do any further damage.

<br>

## Learning Objectives

In this lab you will:

1. Detect if the vulnerability (log4j CVE-2021-44228) is actually present in the application
2. If it is, block the attacks without even updating the code or restarting the app
3. Confirm that the attacks are being blocked

<br>


## Vulnerabilities Dashboard

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

<!--
<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps you used previously to <a href="https://security.fsolabs.net/20_hands_on_observability/21_understanding_app_security_state.html#appdynamics-application-dashboard" target="_blank">**navigate to the Secure Application Dashboard**</a> if you've been logged out.

-->

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Let's go to the **Vulnerabilities** tab as shown below to find out if the vulnerability (log4j CVE-2021-44228) is present in your TeaStore application.

1. Click on the **Vulnerabilities** tab that shows number of Open vulnerabilities, their severity levels and lifespans
2. In this column you see the specific types of vulnerabilities that have been detected
3. Look at the **Kenna Score** that provides an estimate of exploitation likelihood for each vulnerability
4. Notice the application that is vulnerable (in our case it is only our TeaStore app as we have restricted the scope)
5. The **Status** column tells us if a particular vulnerability has been Detected, Confirmed, Fixed, Ignored, or Not Vunerable

![image](/images/20_hands_on/attack_detect_01.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Let's look at the specific vulnerability we are interested in and focus on Detecting it and then Preventing the adversaries from exploiting it.

1. Select **ID** from the filter box drop-down
   - Type in the string **44228**
   - Select **CVE-2021-44228** from the drop-down
2. This confirms a **Critical vulnerability (CVE-2021-44228) is present** in our application
3. **Tier (Nodes)** column tells us the affected services or Tiers in the application that are vulnerable
4. The **Kenna Score of 100** means Ali needs to do something urgently as it carries a Critical vulnerability
5. Click on the **CVE-2021-44228** link under **ID** column, taking you to the vulnerability detail page

![image](/images/20_hands_on/attack_detect_02.png)



<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Now we can see more detail about the vulnerability and possible remediation steps for it.

1. The **Overview** box gives an overview of this vulnerability. Scroll down the overview box to learn more.
   - It describes how attackers exploit this vulnerability and further detail on suggested remediation steps
2. Look at the **First/Last Seen** details
3. The **Remediation** area lists the suggested framework versions that would not have the vulnerability
4. You can click on the external link next to **CVE-2021-44228** in the **ID** area
   - This will take you to the NIST website where you can learn more about this vulnerability (as seen in the next image)


![image](/images/20_hands_on/attack_detect_03.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Example of the NIST website for **CVE-2021-44228**

![image](/images/20_hands_on/attack_detect_04.png)

<br>

<!--
![alt text for screen readers](/images/22/all-vulnerabilities.png)

	Everything we see on this page is related to 'Log4Shell' application ONLY. It is because 
	we restricted our scope to this application (top right corner) during last lab.

The **Vulnerabilities** Tab (above screenshot) shows the vulnerabilities in detail. We had a glimpse 
of this top pane during our previous lab 'Understanding Security State of an Application'. We talked 
about this in detail there but, just to summarize, the top pane shows number of Open and Fixed vulnerabilities,
their severity levels and Lifespans.

Let us pay close attention to the bottom pane of the above screenshot. We see all the vulnerabilities
associated with our application Log4Shell, their severity levels (critical, high, medium, low),
the application that is vulnerable (in our case it is only Log4Shell as we have restricted the scope). 
The **Status** column in the right hand side tells us if a particular vulnerability has been
Discovered, Blocked or Fixed yet.

We'll revisit this page again in our next lab to learn about the vulnerability in much more detail 
but for now let us focus on Detecting it and then Preventing the adversaries from exploiting it.

![alt text for screen readers](/images/22/vulnerability-search.png)

As shown above, in the filter box, make sure **Vulnerability** is selected from the drop-down menu 
and start typing the string 44228. It'd display the search result where you can select **CVE-2021-44228** 
and see the result similar to the one shown below.

![alt text for screen readers](/images/22/vulnerability-explaination.png)

This confirms a Critical vulnerability (CVE-2021-44228) present in our application Log4Shell. 
Clicking on the Red triangular icon next to the severity level confirms the exploit. **Tier (Nodes)** column
tells us the affected services or Tiers in the application that is vulnerable.

**Discovered** status (under **Status** column) means this vulnerability has just been discovered and 
Ali need to do something urgently as it carries a Critical vulnerability. This is where 'Prevention' comes handy
where we can protect the application from being exploited.

Click on the **CVE-2021-44228** link under **Vulnerability** column as shown below.

![alt text for screen readers](/images/22/vulnerability-link.png)

This'd bring you to the vulnerability detail page:

![alt text for screen readers](/images/22/vulnerability-detail.png)

The above screen tells you when this vulnerability was **First/Last seen** in your environment 
and suggests the remediation steps. In **Description** box, it gives an overview of this vulnerability. 
**Scroll down** the Description box to learn more about this vulnerability, how attackers exploit this 
vulnerability and further detail on suggested remediation steps.

If you are interested, you may click on the external link next to 'Title: CVE-2021-44228' towards 
top of the above screen. This will take you to the NIST website where you can learn some more 
details about this vulnerability (shown below).


![alt text for screen readers](/images/22/nist-nvd.png)

<br>

<span style="color: #fb0606;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp; **TBD**


-->

## Attacks Dashboard 

Now that we know we have a vulnerability present in our environment and how bad it is, let's make sure our application is protected against this vulnerability.  A **Policy within CSA** to block the **CVE-2021-44228** vulnerability was created previously. Now, let's make sure this policy is doing it's job and blocking the attacks.

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps below to look at the details of the blocked **CVE-2021-44228** vulnerability.

1. Click on the **Attacks** tab at the top of the Secure Application screen 
2. Select **Outcome** from the filter box drop-down 
   - Then select **Blocked** from the box drop-down
   - The screen will be populated with all the Attacks that have been **Blocked**
3. Click on the first attack in the list 

![image](/images/20_hands_on/attack_detect_05.png)


<!--

![alt text for screen readers](/images/22/attacks.png)

Now, click on one of the attacks as shown above **(#3)**. This'd take you to the below screen with more 
details about that particular attack.

Below, it shows you the Timestamp and the affected Node **(1)**. It tells you the Entry Point and Client IP 
where the attack originated from. This is vital information **(2)**.

-->

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Now we are looking at the **Attack Details** screen.

1. Observe the **Timestamp** and the **Affected Node**
2. Look at the **Entry Point** and **Client IP** where the attack originated from
   - This is vital information
3. Now click on **Show More** link next to the Stack Trace

![image](/images/20_hands_on/attack_detect_06.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Inspect the **Stack Trace** from the attack that was blocked.

As highlighted below, it confirms a line with 'org.apache.logging.log4j.core.net.JndiManager.lookup'. This information can be used to guide developers to the lines of code that was used to achieve the result of the event.

![image](/images/20_hands_on/attack_detect_07.png)


<!--

![alt text for screen readers](/images/22/attack-detail.png)

Now, click on **Show More** above next to Stack Trace as shown in #3 above.

![alt text for screen readers](/images/22/stack-trace.png)

It shows the Stack Trace from the attack we collected. As highlighted above, it confirms a line with 
'org.apache.logging.log4j.core.net.JndiManager.lookup'. This information can be used to guide developers 
to the lines of code that was used to achieve the result of the event.



## Summary

In this Lab, you confirmed the vulnerability log4j CVE-2021-44228 was present in your environment and how severe it was, you then created a policy with a rule to block the attacks that exploit this vulnerability. You went ahead and confirmed that the rule you created was actually effective in blocking those attacks.

-->

<br>

## Next <span style="color: #143c76;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp;

We'll take a look at how we can use **Cisco Secure Application** for **Risk Profiling and Prioritization**.

<br>



