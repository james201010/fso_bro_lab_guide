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


<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Navigate go to the **Vulnerabilities** tab as shown below to find out if the vulnerability (log4j CVE-2021-44228) is present in your TeaStore application.

1. Click on the **Vulnerabilities** tab that shows number of Open vulnerabilities, their severity levels and lifespans
2. In this column you see the specific types of vulnerabilities that have been detected
3. Look at the **Kenna Score** that provides an estimate of exploitation likelihood for each vulnerability. See [Vulnerability Scoring in Kenna](https://help.kennasecurity.com/hc/en-us/articles/360026160592-Vulnerability-Scoring-in-Kenna) for more details about the scoring mechanism.
4. Note if there is an exclamation point in the **Reached** column indicating that the vulnerable code has been reached
5. In the **Application** column, you can see the application that is vulnerable (in our case, it is only our TeaStore application, since you have limited the scope). The columns next to it indicate the exact application tier and library associated with the vulnerability, which makes it easier for application maintainers to proceed with remediation.
6. The **Status** column tells us if a particular vulnerability has been Detected, Confirmed, Fixed, Ignored, or Not Vulnerable

![image](/images/20_hands_on/attack_detect_01_B.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Next, look at the specific vulnerability you are interested in and focus on Detecting it and then Preventing attackers from exploiting it.

1. Select **ID** from the filter box drop-down
   - Type in the string **44228**
   - Select **CVE-2021-44228** from the drop-down
2. This confirms a **Critical vulnerability (CVE-2021-44228) is present** in your application
3. You can observe the affected services or Tiers in the application that are vulnerable
4. The **CVSS Score of 10.0** indicates that this vulnerability has a critical severity level
5. The **Kenna Score of 100** means Ali needs to do something urgently as it is highly probable that this vulnerability will be exploited soon
      - In general, you should focus more on the Kenna score than the CVSS score, because a low severity vulnerability (CVSS) may bring a high exploitation risk (Kenna) to your environment, while a high severity vulnerability may have little impact on the security of your application
5. Click on the **CVE-2021-44228** link under **ID** column, taking you to the vulnerability detail page

![image](/images/20_hands_on/attack_detect_02_B.png)



<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Now we can see more detail about the vulnerability and possible remediation steps for it.

1. The **Kenna Score** widget provides some real-time details about whether this vulnerability is part of an active internet breach, whether it is easily exploitable, whether it is a popular target, and so on.
   - It describes how attackers exploit this vulnerability and further detail on suggested remediation steps
2. The **Overview** box gives an overview of this vulnerability. Scroll down the overview box to learn more.
   - It describes how attackers exploit this vulnerability and further detail on suggested remediation steps
3. The **Details** section provides some details about the vulnerabilities, such as when the vulnerability was first published, when it first appeared in your application, as well as some suggestions for fixing the vulnerability by updating the affected library.
4. You can click on the external link next to **CVE-2021-44228** in the **ID** area
   - This will take you to the NIST website where you can learn more about this vulnerability (as seen in the next image)

_
![image](/images/20_hands_on/attack_detect_03_B.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Example of the NIST website for **CVE-2021-44228**

![image](/images/20_hands_on/attack_detect_04_B.png)

<br>


## Attacks Dashboard 

Now that you know that there is a vulnerability in your environment and how severe it is, you should make sure that the application is protected against this vulnerability. A **Policy within CSA** to block the **CVE-2021-44228** vulnerability was created previously.

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; The following steps will reveal how the policy was created.

1. Click on the cogwheel button in the upper right corner of the Secure Application screen
2. Select **Policies** from the drop-down    

![image](/images/20_hands_on/attack_detect_08.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Look for your application's policy and check its settings.

1. In the search bar, select **Application** as the search parameter and enter the name of your application, which you will find in the upper right corner
2. A single **Network or socket access** policy should appear, with a custom rule that blocks the attack if the application stack trace contains a malicious call to the Jndi lookup method in the log4j library

![image](/images/20_hands_on/attack_detect_09.png)

Next, make sure this policy is doing it's job and blocking the attacks.

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps below to look at the details of the blocked **CVE-2021-44228** vulnerability.

1. Click on the **Attacks** tab at the top of the Secure Application screen 
2. Select **Outcome** from the filter box drop-down 
   - Then select **Blocked** from the box drop-down
   - The screen will be populated with all the Attacks that have been **Blocked**
3. Click on the first attack in the list 

![image](/images/20_hands_on/attack_detect_05_B.png)



<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Now we are looking at the **Attack Details** screen.

1. Observe the **Timestamp** and the **Affected Node**
2. Look at the vulnerability details such as:
      - the attack **Entry Point**, which is the webserver URL accessed by the client in the transaction that triggered the event
      - **Blocked Reason** is the reason why the blocked event was triggered
      - **Socket Out** is the destination IP address. If there is a warning icon next to it, it means that a known malicious IP was detected.
      Currently, the Talos malicious IP list is supported.
3. Now click on **Show More** link next to the Stack Trace

![image](/images/20_hands_on/attack_detect_06_B.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Inspect the **Stack Trace** from the attack that was blocked.

As highlighted below, it confirms a line with 'org.apache.logging.log4j.core.net.JndiManager.lookup'. This information can be used to guide developers to the lines of code that was used to achieve the result of the event.

![image](/images/20_hands_on/attack_detect_07_B.png)


<br>

## Next <span style="color: #143c76;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp;

We'll take a look at how we can use **Cisco Secure Application** for **Risk Profiling and Prioritization**.

<br>



