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

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps you used previously to [**navigate to the Secure Application Dashboard**]({{< ref "/21_understanding_app_security_state.html#appdynamics-application-dashboard" >}} "**navigate to the Secure Application Dashboard**") if you've been logged out.


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


## Attacks Dashboard 

Now that we know we have a vulnerability present in our environment and how bad it is, let's make sure our application is protected against this vulnerability.  A **Policy within CSA** to block the **CVE-2021-44228** vulnerability was created previously. Now, let's make sure this policy is doing it's job and blocking the attacks.

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps below to look at the details of the blocked **CVE-2021-44228** vulnerability.

1. Click on the **Attacks** tab at the top of the Secure Application screen 
2. Select **Outcome** from the filter box drop-down 
   - Then select **Blocked** from the box drop-down
   - The screen will be populated with all the Attacks that have been **Blocked**
3. Click on the first attack in the list 

![image](/images/20_hands_on/attack_detect_05.png)



<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Now we are looking at the **Attack Details** screen.

1. Observe the **Timestamp** and the **Affected Node**
2. Look at the **Entry Point** and **Client IP** where the attack originated from
   - This is vital information
3. Now click on **Show More** link next to the Stack Trace

![image](/images/20_hands_on/attack_detect_06.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Inspect the **Stack Trace** from the attack that was blocked.

As highlighted below, it confirms a line with 'org.apache.logging.log4j.core.net.JndiManager.lookup'. This information can be used to guide developers to the lines of code that was used to achieve the result of the event.

![image](/images/20_hands_on/attack_detect_07.png)


<br>

## Next <span style="color: #143c76;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp;

We'll take a look at how we can use **Cisco Secure Application** for **Risk Profiling and Prioritization**.

<br>



