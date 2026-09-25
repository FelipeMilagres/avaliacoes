# Readme


Hello LambdaTest Support Team,

I hope you are doing well.

I would like to ask for your support regarding a behavior we recently observed during our automated test executions.

Currently, we have an App Automation plan with 30 parallel executions. During a recent test, when running a local automation (via pipeline), we noticed that only one device was actively in use. However, despite having available capacity, the execution was placed in a queue instead of starting immediately.

Based on our initial analysis, we believe this may be related to the specific device configured for the execution not being available at that moment, even though other devices were free in the pool (as we are using the public device farm).

With that in mind, we would appreciate your guidance on the following:

* Is there a way to check real-time device availability before triggering a test execution?
* Are there recommended practices to avoid executions being queued when capacity is available but not for a specific device?
* Is there any fallback strategy or configuration to automatically select alternative compatible devices?
* What are the best practices to optimize executions in a public device farm environment, especially within CI/CD pipelines?

Our goal is to avoid execution delays, particularly in pipeline scenarios where timing is critical.

Thank you in advance for your support. We look forward to your guidance.

Best regards,
Felipe Milagres
