# Workflow Engine

* Integrate with Kaleo workflow engine
* A Kaleo workflow, called a “process definition”, is defined in an XML document.

# Nodes

* condition
* state
  * Set "initial=true" for start state.
* task
* join
* join-xor
* fork

# Script language

* Beanscript
* Groovy
* Python, Ruby

# Notification

* execution-type
  * onAssignment
  * onEntry
  * onExist
* notification-type
  * email
* Role-type
  * site
  * organization
  * portal = regular

# Timer

* task-timer
* timer-action

# Sample workflows on github

* Single approver <https://github.com/liferay/liferay-portal/blob/6.2/modules/apps/forms-and-workflow/portal-workflow/portal-workflow-kaleo-runtime-impl/src/main/resources/META-INF/definitions/single-approver-definition.xml>
* <https://github.com/liferay/liferay-portal/blob/master/portal-web/test/functional/com/liferay/portalweb/dependencies/advanced-governors-review.xml>
* <https://github.com/liferay/liferay-portal/blob/master/portal-web/test/functional/com/liferay/portalweb/dependencies/workflow_definition_task_timers.xml>
* <https://github.com/liferay/liferay-docs/blob/master/discover/deployment/code/legal-workflow-script.xml>

# Change mail sender/subject

TODO I didn't try this, but the following ticket claim that it works:

<https://issues.liferay.com/browse/LPS-36149>

```
workflowContext.put("notificationSenderAddress", "no-reply@test.com");
workflowContext.put("notificationSenderName", "My Custom Name");
```

# References

* User manual <https://dev.liferay.com/documents/10184/510059/indexed-using-liferay-portal-62.pdf>
* Developer tutorial <https://dev.liferay.com/develop/tutorials/-/knowledge_base/6-2/workflow>
* Liferay Kaleo workflow <https://web.liferay.com/marketplace/-/mp/application/15194706>
* XML schema <https://github.com/liferay/liferay-portal/blob/master/definitions/liferay-workflow-definition_6_2_0.xsd>
* Liferay IDE <https://dev.liferay.com/develop/tutorials/-/knowledge_base/6-2/developing-apps-with-liferay-ide>
