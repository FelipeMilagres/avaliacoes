Hello team,

We are opening this ticket to report an issue related to the use of a dedicated IP in LambdaTest Web Automation.

**Context:**
We are currently running automated tests using the Web Automation capability and have encountered a blocking issue when accessing a Salesforce-based application.

This application enforces a security policy where any access originating from an unrecognized IP address triggers a two-factor authentication (2FA) challenge, which interrupts our automated execution.

**What we have configured:**

* We have a **dedicated IP** provisioned by LambdaTest:
  **[INSERT DEDICATED IP HERE]**
* This IP has been **explicitly whitelisted in Salesforce** to bypass the 2FA requirement.

**Observed behavior:**
Despite the configuration above, our automation executions are still being challenged by 2FA.

Upon analyzing the execution logs and Salesforce access records, we identified that:

* The **source IP hitting Salesforce is different from the dedicated IP configured**
* The IP observed in Salesforce logs is:
  **[INSERT IP FROM SALESFORCE LOGS HERE]**

This indicates that Web Automation sessions are **not routing traffic through the configured dedicated IP**, which is unexpected.

**Impact:**

* Automated test flows are blocked due to 2FA
* Prevents stable CI/CD execution
* Limits our ability to validate Salesforce-integrated journeys

**Execution details:**

* Platform: Web Automation (LambdaTest)
* Target application: Salesforce-based system
* Execution link:
  **[INSERT EXECUTION LINK HERE]**
* Attachments:

  * Screenshot/log showing IP captured by Salesforce
  * Execution report demonstrating failure point

**What we need from your team:**

1. Confirmation on how **dedicated IP routing works for Web Automation**
2. Clarification if there is any **additional configuration required** to enforce usage of the dedicated IP
3. Investigation into why sessions are being executed from a **different IP**
4. Guidance on ensuring all outbound traffic from automation uses the dedicated IP

If any additional information is required (capabilities, configs, logs, etc.), we can promptly provide it.

Thanks in advance for your support.

Best regards,
[Your Name]
