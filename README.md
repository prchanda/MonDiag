# MonDiag
MonDiag is a simple self-help utility which will help you to troubleshoot most of the Azure Monitor issues. It comes with an automatic root-cause analysis engine to diagnose various scenarios like:

1.	Activity Log Alert didn't fire, although I see an entry for the corresponding activity in the Activity Logs.

2.	Classic Alert notification not received although alert criteria seems to have been satisfied.

3.	Metric evaluation condition seems to have been satisfied, however metric alert notification is not received.


Apart from providing the root-cause analysis, the tool provides centralized information about alert definitions, action group details, autoscale settings, etc.


### Topology
------------

The MonDiag interface is divided into four areas:

1.	**Action Panel (top left)** - The area that provides options to choose your intended action. For example - Run Root-Cause Analysis, Show Alert Definitions, etc.

2.	**Control Panel (bottom left)** - The area where you can select the scope for troubleshooting. For example - Subscription, Resource Groups, Resources, Timespan, etc.

3.	**Dashboard (main window)** - The area where the results will be displayed.

4.	**Utility (right vertical)** - The area that provides the option to login to your Azure account, send feedback, etc.

![Dashboard](https://github.com/prchanda/MonDiag/blob/Images/Dashboard.PNG)


### Workflow
-----------------

1.	Login to your Azure subscription. If you are already authenticated, then you don't need to re-enter your credentials. You can login with a different Azure account by clicking the account button in the top-right corner of the tool.

2.	Choose your troubleshooting scope from the Control Panel area (bottom left). For example if you want to fetch the definition of all the Activity Log Alerts across a Resource Group, select the corresponding Resource Group from the **Resource Group** dropdown list or, if you want to get information about a particular Activity Log Alert, choose the specific Resource from the **Resource** dropdown list.

3.	Select the intended action you want to perform from the Action Panel (top left). For example if you want to retrieve the Action Group Definition, click the "Action Group Definition" option.

4.	Click on the Apply button.


### Example Troubleshooting Scenarios
---------------------------------------------

#### Scenario 1 : Running Root-Cause Analysis on failed Activity Log Alerts

##### Symptom
An Activity Log Alert to track the deletion of Virtual Networks was not trigger, although we can see the Activity Log generated for the corresponding activity.

##### Workflow

1.	Choose the **Root-Cause Analysis** option from the *Action Panel*.

2.	Choose the category of the problem or issue from the Dashboard. In this case we will choose the first option - "*One of my Activity Log Alerts didn't fire, although I see an entry for the corresponding activity in the Activity Logs.*"

3.	Select the Activity Log Alert in reference from the *Resource* dropdown list.

4.	Set the Start and End time during the time window in which you want the Root-Cause Analysis.

5.	Click on the Apply button.

##### Assessment

This section will tell you which of the Root-Cause Analysis evaluation step(s) failed. For example in the screenshot below, the Alert criteria or condition was not satisfied, as is depicted by the red X mark.

![Assessment](https://github.com/prchanda/MonDiag/blob/Images/Assessment.PNG)

##### Recommendation

Based on the assessment, the Recommendation section will guide you with what are the steps you need to perform to resolve or fix the issue. For example, in the example below, you need to fix the Alert criteria because the expected alert condition for status is set to 'Started', whereas in reality the actual activity was 'Succeeded', hence the alert wasn't trigger as expected.

![Recommendation](https://github.com/prchanda/MonDiag/blob/Images/Recommendation.PNG)


- #### Scenario 2 : Retreive Action Group Details

1.	Choose the **Action Group Definition** option from the *Action Panel*.

2.	Select the Action Group that you want to retrieve the details for from the *Resource* dropdown list, or you can also retreive Action Group details across a Resource Group or whole Subscription by selecting the appropriate scope.

3.	Click on the Apply button.

4.	You should see the details in the Dashboard.
