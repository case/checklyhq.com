---
title: Pagerduty integration
weight: 4
---

Checkly integrates with [Pagerduty](https://pagerduty.com) and can deliver all failure and recovery events 
to Pagerduty account. After setting up the integration, Checkly will:

1. Trigger alerts in Pagerduty when a check fails.
2. Resolve alerts when a check recovers.

Integration is as simple as following the three step Pagerduty connect process.


1. Navigate to the global **alert channels** tab on the account screen and click the 'Alert with Pagerduty' button.
![](/docs/images/alerting/pagerduty_step1.png)

2. Clicking the **Alert with Pagerduty** button will take you to a Pagerduty login screen. Provide your credentials and click
**Authorize integration** to allow Checkly to integrate with Pagerduty.
![](/docs/images/alerting/pagerduty_step2.png)

3. On the next screen you can either hook up Checkly to an existing service, or create a brand new service.
Click **Finish integration** to save your settings and redirect you back to Checkly. 
![](/docs/images/alerting/pagerduty_step3.png)

4. Back in Checkly, you should see your Pagerduty **integration credentials** reflected in the alert settings. 
![](/docs/images/alerting/pagerduty_step4.png)

5. Checkly will trigger an incident in Pagerduty when checks fail and also mark them as resolved when the checks are passing again.
![](/docs/images/alerting/pagerduty_step5.png)



If you want to change your Pagerduty integration, first remove it and then go through the setup steps again
