+++
title = "Understanding Security State"
chapter = false
weight = 21
+++

## Introduction

Ali wants to have actionable information. In this lab, you will make sure Ali has a quick way to find how his Applications are doing from security point of view. Ali wants to be comfortable while navigating the Dashboard so he knows what kind of information is readily available to him.

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

<br>


## AppDynamics Application Dashboard

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Use the steps below to **navigate to your TeaStore application**.

1. Click on the **Applications** tab on the top menu
2. Find your **TeaStore application** with **your lab number in the name** and **click on its name** to open it

![image](/images/20_hands_on/security_state_01.png)


<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; The **Application Dashboard** displays showing the components that comprise the TeaStore application. 

1. The **Security Health** widget shows us if we have any Critical or Warning events
2. Click on the **Security Health** link to launch the **Secure Application** dashboard

![image](/images/20_hands_on/security_state_02.png)

<br>


## CSA Home Dashboard

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; The **Home** page provides a high-level overview of **Attacks and Vulnerabilities** of the monitored application.

1. Navigate to the Home page by clicking the **Home** tab on the top menu

2. The **Business Transactions** pane shows the number of business transactions based on their risk score detected along with the **Top Recommended Actions**

3. The **Vulnerabilities** pane shows the number of both **Open** and **Fixed** vulnerabilities. 

  - The chart in the left represents the total number of vulnerabilities based on their risk score.
  - The color of the chart displays the number of vulnerabilities for different severity levels:
     - **Critical** = Red &nbsp; **High** = Orange &nbsp; **Medium** = Yellow &nbsp; **Low** = Purple
  - **Days Since First Detected** shows the number of days the vulnerability has been open for and it's severity
  - **Severity Trend** shows the trend of fixing the open vulnerabilities


![image](/images/20_hands_on/security_state_03.png)


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

![image](/images/20_hands_on/security_state_04.png)

<br>

<!--
Let's start the fun. For now, Ali is only interested in his application - Log4Shell.

First, Log on to your assigned AppD Controller. Under **Applications** Tab, Click **Log4Shell**
Application as highlighted below. It'd take you to the application (Log4Shell) detail screen.

![alt text for screen readers](/images/21/1-application.png "Pic 1 - Select Application")

Now, at the top right of your screen, select **last 1 week** (shown below) as Duration so we 
can see some events. In the Right hand side, 'Security Events' widget tells us Ali has 3 Security Events
that are 'Critical' and 5 'Warning' for his Application (Log4Shell) during last 1 week.

![alt text for screen readers](/images/21/2-security-events.png "Pic 2 - Select Security Events")



Select **Security Events** as highlighted in the above picture. This'd launch the SecureApp 
Dashboard (shown below) that gives a high-level overview of what is seen in your application 
environment from security point of view.

![alt text for screen readers](/images/21/3-dashboard.png "Pic 3 - SecureApp Dashboard")

**[NB : Make sure you still have Log4Shell selected as the scope for the Dashboard in the top Right 
corner. If not, you can use the 'Filter' icon (Top Right corner) and select 'Log4Shell' as 
Application and 'All Tiers' then 'Apply Changes' to see the information only related to Log4Shell.]**

You'd have a very similar screen as shown above. It is the Dashboard for Secure Application.
It is a graphical representation of all the analyzed data. The data is updated on the dashboard 
when the service within the Controller sends the analyzed data to the dashboard.


1. The **Home** page is the landing page of the Dashboard and it provides a high-level overview 
of Attacks and Vulnerabilities of the monitored Application (Log4Shell in this case).

2. The **Vulnerabilities** pane shows the number of both **open** and **fixed** vulnerabilities. The 
Pie chart in the left represents the total number of open vulnerabilities. The color of the 
Pie chart displays the number of vulnerabilities for different severity levels - 

	Critical = Red; High = Orange; Medium = Yellow; Low = Purple

	Hover the mouse on each of the severity to view the number of related open vulnerabilities. E.g. In
	the above screenshot, there are 2 open critical vulnerabilities out of a total of 10.

	**LIFESPAN** shows the number of days the vulnerability has been open for and it's severity.

	**TREND** shows the trend of fixing the open vulnerabilities.


3. The **Attacks** pane displays the number of open attacks, Top Applications and Top Attack Types.

	The Pie chart shows the total number of **open** attacks and their states. In the above example, 
	there are 25 open attacks that have been blocked.

	[Observed = Blue; Exploited = Red; Blocked = Yellow]

	You may hover your mouse on the required state to view the number of open attacks in that state.

	The **Top Applications** chart displays the top 10 applications based on open attacks for every application. 
	we have only one application here as per the filter we applied earlier.

	The **Top Attack Types** displays the top 10 attack events that are in different states (exploited, 
	blocked or observed) against the total number of open attacks.


4. The **Observations** pane shows top 10 Applications and Event Types that are observed with 
	malicious activities..

5. The **Applications** pane displays the nodes of the application in question (Log4Shell in this case)
	and the trend.
	
	**TOTAL ACTIVE NODES**	- number of nodes that are actively communicating with the Controller.
		
	**SUPPORTED NODES**	- number of nodes registered/unregistered with Cisco Secure Application.
	
	**ENABLED NODES** - number of nodes that have security enabled/disabled for the applications.
	
	**SECURED NODES** - number of secured/unsecured nodes.
	
	**TREND** displays the number of enabled, supported, active, and secured nodes against the day of the month.

-->


## Summary

<span style="color: #143c76;"><i class='fas fa-circle fa-sm'></i></span>&nbsp; Just by looking at the **Home** page of his Secure Application Dashboard, Ali has not only learned about his application and it's security state but he also has actionable information.

- Number of Open Vulnerabilities, their severity levels and the lifespan of those open vulnerabilities
- Open attacks that needs to be fixed and their states 
- Top Applications with open attacks and event types
- Nodes of the application(s) that needs to be enabled and secured

<br>

## Next <span style="color: #143c76;"><i class='fas fa-cog fa-spin fa-sm'></i></span>&nbsp;

We'll look at how **Cisco Secure Application** easily enables **Attack Detection and Prevention** for your business crititcal applications.

<br>

