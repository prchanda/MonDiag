# MonDiag
MonDiag is a simple self-help utility which will help you to troubleshoot most of the Azure Monitor issues. It comes with automatic root cause analysis engine to diagnose various scenarios like:

1.	Activity Log Alert didn't fire, although I see an entry for the corresponding activity in the activity logs.

2.	Classic Alert notification not received although alert criteria seems to have satisfied.

3.	Metric evaluation condition seems to have satisfied, however metric alert notification is not received.


Apart from providing the RCA, the tool provides OneStop information about alert definition, action group details, autoscale settings, etc.


### Topology
------------

MonDiag arena is divided into four parts:

1.	**Action Panel** - Place which gives you an option to choose your intended action. Ex- Run RCA, Get Alert definition, etc.

2.	**Control Panel** - Place where you can choose the scope of troubleshooting. Ex- Choose resource, Set TimeSpan of troubleshooting, etc.

3.	**Dashboard** - Place you get your queried information / results.

4.	**Utility** - Place which gives you an option to login, send feedback, etc.

![Dashboard](https://github.com/prchanda/MonDiag/blob/Images/Dashboard.PNG)


### Workflow
-----------------

1.	Login to your Azure subscription. If you are already authenticated, then you don't need to re-enter your credentials. You can login with a different azure account as well using change account button on the top-right corner of the tool.

2.	Choose your troubleshooting scope from the Control Panel. For example if you want to fetch the definition of all the activity log alerts across a resource group, select the corresponding resource group from the **Resource Group** dropdown list or if you want to get information about a particular activity log alert, please choose the correct resource from the **Resource** dropdown list.

3.	Select the intended action you want to perform from the action panel. For example if you want to retrieve the action group definition, click on "Action Group Definition" option.

4.	Click on the Apply button.


## Some of the Troubleshooting Scenarios
---------------------------------------------

- ### Running RCA on failed Activity Log Alert

##### Symptom
An activity log alert setup to track deletion of virtual network didn't get trigger, although we can see activity log generated for the corresponding activity.

##### Workflow

1.	Choose the **Root Cause Analysis** option from the *Action Panel*.

2.	Choose the category of the problem or issue from the Dashboard. In this case we will choose the first option - 

    "*One of my Activity Log Alert didn't fire, although I see an entry for the corresponding activity in the activity logs.*"

3.	Select the activity log alert in concern from the *Resource* dropdown list.

4.	Set the Start and End time during which you want the RCA.

5.	Click on the Apply button.

##### Assessment

This section will tell you which of the RCA evaluation step(s) failed. For example in the below screenshot alert criteria or condition didn't get satisfied as depicted by the cross mark.

![Assessment](https://github.com/prchanda/MonDiag/blob/Images/Assessment.PNG)

##### Recommendation

Based on the assessment, recommendation section will guide you what are the steps you need perform to resolve or fix the issue. For example as per the below recommendation, you need to fix the alert criteria because the expected alert condition for status is set to 'Started', whereas in reality the actual activity was 'Succeeded', hence the alert didn't get trigger as expected.

![Recommendation](https://github.com/prchanda/MonDiag/blob/Images/Recommendation.PNG)


- ### Retreive Action Group Details
---------------------------------

1.	Choose the **Action Group Definition** option from the *Action Panel*.

2.	Select the Action Group for which you want to fetch the details from the *Resource* dropdown list, or you can also retreive Action Group details across a resource group or whole subscription by selecting appropriate scope.

3.	Click on the Apply button.

4.	You should see the details in the Dashboard.
