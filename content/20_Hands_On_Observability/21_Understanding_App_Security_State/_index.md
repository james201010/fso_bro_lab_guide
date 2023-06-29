+++
title = "Understanding Security State"
chapter = false
weight = 21
+++

## Introduction

Ali wants to have actionable information. In this lab, you will make sure Ali has a quick way to find how his Applications are doing from security point of view. Ali wants to be comfortable while navigating the Dashboard so he knows what kind of information is readily available to him.


<br>


## AppDynamics Application Dashboard

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps below to **navigate to your TeaStore application**.

1. Click on the **Applications** tab on the top menu
2. Find your **TeaStore application** with **your lab number in the name** and **click on its name** to open it

![image](/images/20_hands_on/security_state_01_B.png)


<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; The **Application Dashboard** displays showing the components that comprise the TeaStore application. 

1. The **Security Health** widget displays the Business Risk Score in real time, the number of vulnerabilities divided by criticality, and the number of attacks that either compromised the security of your application, were blocked by the CSA attack policy, or the malicious activity was detected but not exploited.
2. Click on the **Security Health** link to launch the **Secure Application** dashboard

![image](/images/20_hands_on/security_state_02_B_1.png)

<br>


## CSA Home Dashboard

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; The **Home** page provides a high-level overview of **Attacks and Vulnerabilities** of the monitored application.

1. Navigate to the Home page by clicking the **Home** tab on the top menu

2. The **Business Transactions** pane shows the number of business transactions based on their risk status detected, alongside the daily **Busines Risk Score**, and **Top Recommended Actions**.
  - There are 3 business risk statuses based on the score:
      - **Normal**: 0-330 &nbsp; **Warning**: 340-660 &nbsp; **Critical**: 670-1000

3. The **Vulnerabilities** pane shows the number of both **Open** and **Fixed** vulnerabilities. 

  - The chart in the left represents the total number of vulnerabilities based on their risk score.
  - The color of the chart displays the number of vulnerabilities for different severity levels:
     - **Critical** = Red &nbsp; **High** = Orange &nbsp; **Medium** = Yellow &nbsp; **Low** = Purple
  - **Severity Trend** shows the number of security vulnerabilities by severity in a given period.
  - **Days Since First Detected** shows the number of days since the vulnerability has been open and its severity level.


![image](/images/20_hands_on/security_state_03_B.png)


<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Scroll down the screen to see the **Attacks** and **Applications** pane.

1. The **Attacks** pane displays the number of Attacks by Outcome, Top Applications and Top Attack Types.

  - The chart on the left shows the total number of **Open** attacks and their states:
     - **Exploited** = Red &nbsp; **Blocked** = Purple &nbsp; **Attempted** = Yellow
  - **Top Attack Types** displays the top 10 attack events in different states (exploited, blocked or attempted)
  
2. The **Applications** pane displays the nodes of the application in question and the trend

  - **Total Active Nodes** Total number of APM nodes that are registered and active in the AppDynamics controller.
  - **Supported Nodes** Number of Active nodes that are running a Secure Application supported version of the agent.
  - **Ready Nodes** Number of Supported nodes that are sending heartbeats to the Secure Application service.
  - **Enabled Nodes** Number of Ready nodes that have a Security Setting value of Enable.
  - **Secured Nodes** Number of Enabled nodes that are sending security insights to the Secure Application service.

![image](/images/20_hands_on/security_state_04_B.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Next, you'll learn an alternative way to get into security monitoring while keeping an eye on the application performance dashboard.

1. If you are in the CSA dashboard, scroll up and click the icon next to the name of your application
    - Alternatively, you can return to the AppDynamics APM Controller and open your application's dashboard as you did in the first step.

![image](/images/20_hands_on/security_state_05.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; The application dashboard is the main source of information about application performance, but it also serves as a starting point when you want to look at other aspects of application observability, in your case application security. Previously, you used the **Security Health** widget to get into the CSA dashboard. Now you'll see that you can examine the performance and business risk of the application's business transactions in a single view, and then dive deeper into security as needed.

1. Click on **Business Transactions** menu button.

![image](/images/20_hands_on/security_state_06.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Business transactions are key objects when it comes to monitoring application performance. But they also involve business risk associated with each of those transactions. AppSec teams can use this to decide if there is a security risk associated with any of the important business transactions.

1. Click the **Business Risk** column heading to sort transactions by business risk in descending order.
2. Double click on the business transaction with the highest business risk

![image](/images/20_hands_on/security_state_07.png)

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; The following view focuses only on the selected business transaction.

1. Click on the **Business Risk** link within the **Security Health** widget.

![image](/images/20_hands_on/security_state_08.png)


<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; From monitoring the performance of business transactions of the application, you quickly moved to business risk observability, where you can see the details about the security risk of business transactions, the associated vulnerabilities, attacks and options to address the risk. 

You will learn more about **Business Risk Observability** and its features in later exercises.

![image](/images/20_hands_on/security_state_09.png)
<br>


## Summary

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Just by looking at the **Home** page of his Secure Application Dashboard, Ali has not only learned about his application and it's security state but he also has actionable information.

- Number of Open Vulnerabilities, their severity levels and the lifespan of those open vulnerabilities
- The business impact of vulnerabilities based on the Business Risk Score
- Open attacks that needs to be fixed and their states 
- Top Applications with open attacks and event types
- Nodes of the application(s) that needs to be enabled and secured

<br>

## Next <span style="color: #143c76;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp;

You'll look at how **Cisco Secure Application** easily enables **Attack Detection and Prevention** for your business crititcal applications.

<br>

