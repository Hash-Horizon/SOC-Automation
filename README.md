# Diagram-SOC-Automation
![SOC Automation Diagram](SOC-Automation.drawio.png)
Thank you for sharing the diagram! Let's go through it in detail, breaking down each term and unusual name to make it easier to understand.

This diagram illustrates the process of security monitoring and incident handling using several components. Here's an explanation of each step and component visible in the diagram:

1. **Windows 10 Client (Wazuh Agent)**:
   - **Windows 10 Client**: This is a regular computer running the Windows 10 operating system. It could be any user machine in an organization.
   - **Wazuh Agent**: This is a lightweight software installed on the Windows 10 client. It collects security-related data from the computer, such as log files, suspicious activities, or changes in the system, and sends it to the next component for analysis.

2. **Router**:
   - **Router**: A router is a networking device that forwards data between computer networks. In this diagram, the router receives events (data) from the Wazuh Agent and passes them to the next stage in the monitoring process.

3. **Internet**:
   - **Internet**: The global network that connects all devices together. Here, the Internet is used as a medium to transfer the events collected by the Wazuh Agent from the local network to a remote server or system for further analysis.

4. **Wazuh Manager**:
   - **Wazuh Manager**: This is the main component of the Wazuh platform. It receives data from multiple Wazuh Agents and processes that data to detect threats or unusual activity. It acts as the brain of the monitoring system.
   - **Receive Events**: The Wazuh Manager receives events (logs and security data) from the agents installed on various devices.
   - **Send Alerts**: If the Wazuh Manager detects anything suspicious or identifies potential threats, it sends alerts to another component called **Shuffle**.

5. **Shuffle**:
   - **Shuffle**: Shuffle is an automation platform. It helps automate the process of handling alerts and responding to threats. Instead of a human needing to manually review and respond to each alert, Shuffle can trigger actions automatically based on predefined rules.
   - **Enrich IOCS**: **IOCs** stands for **Indicators of Compromise**. These are pieces of evidence that indicate a potential security breach, like unusual file changes or network activity. Shuffle enriches these IOCs by adding context, such as whether the activity is associated with known malicious sources.
   - **Send Alerts**: Shuffle sends these enriched alerts to **TheHive** for further incident management.
   - **Send Email**: Shuffle also sends email notifications as part of the automated response to incidents. This keeps the security team informed about what’s happening.

6. **TheHive**:
   - **TheHive**: TheHive is an open-source incident response platform. It is used by cybersecurity teams to manage incidents and collaborate on investigating threats. It helps organize alerts into cases, allowing analysts to work through each case systematically.
   - TheHive receives enriched alerts from Shuffle and helps the team manage the investigation and response process effectively.

7. **SOC Analyst**:
   - **SOC Analyst**: **SOC** stands for **Security Operations Center**. A SOC Analyst is a person who works in the Security Operations Center. They are responsible for monitoring security alerts, analyzing threats, and responding to incidents.
   - **Send and Receive Email**: The SOC Analyst communicates using email to coordinate incident response. They receive alerts from the system and may also reach out to other teams or stakeholders for further investigation or action.

### Detailed Flow Explanation
The diagram shows a complete flow of security event detection and response, starting from the endpoint (Windows 10 Client) and going all the way to a human analyst (SOC Analyst). Here's the step-by-step flow in detail:

1. **Event Generation (Windows 10 Client)**:
   - The flow begins at the **Windows 10 Client** where the **Wazuh Agent** is installed. This agent continuously monitors the system, collecting log data and looking for suspicious activities. When an event is detected (e.g., an unauthorized attempt to access files), it generates an event.

2. **Event Forwarding (Router)**:
   - The **Wazuh Agent** sends these events to the **Router**. The router is responsible for ensuring that the data from the endpoint reaches its intended destination in a secure and efficient manner.

3. **Event Transfer (Internet)**:
   - The **Router** forwards the event data to the **Internet**, allowing the information to be transmitted securely to a central system. This is essential when the Wazuh Manager is hosted remotely.

4. **Event Reception and Analysis (Wazuh Manager)**:
   - The **Wazuh Manager** is the central unit where all events from various agents are gathered. Upon receiving the events, the Wazuh Manager processes and analyzes them. It checks if the incoming data matches any known threat patterns or indicators of compromise (IOCs).
   - If the Wazuh Manager identifies any suspicious behavior, it generates an alert to notify the security system.

5. **Alert Handling (Shuffle)**:
   - The generated alerts are then sent to **Shuffle**, which is responsible for automated alert handling. Shuffle can enhance the alert with more context by enriching the **Indicators of Compromise (IOCs)**. This step involves gathering more information to determine if the threat is serious and if any action needs to be taken.
   - After enrichment, **Shuffle** can also take automated actions such as notifying relevant personnel by email, initiating further investigations, or sending enriched alerts to another tool like **TheHive**.

6. **Incident Management (TheHive)**:
   - The enriched alerts are forwarded to **TheHive**. TheHive acts as a **case management system**, which helps organize the alerts into incidents that require further investigation. It provides a structured environment where security analysts can document their findings and collaborate on incident response.
   - TheHive essentially helps convert alerts into manageable cases that can be assigned, investigated, and tracked by analysts.

7. **Response by SOC Analyst**:
   - Once an alert has been turned into a case in **TheHive**, it is picked up by a **SOC Analyst**. The analyst reviews all the information provided, including the enriched data and any automated actions taken so far.
   - The SOC Analyst then decides on the appropriate response, which could involve mitigating the threat, notifying stakeholders, or even escalating the incident for more extensive action. The analyst uses **email** to communicate with other teams or external parties as part of the response process.

8. **Continuous Monitoring**:
   - Throughout this flow, the system continuously monitors for new events and threats. The automated and manual processes work together to ensure that threats are detected early, analyzed thoroughly, and handled efficiently to minimize any impact on the organization.

Overall, this detailed flow shows how different components interact in a layered approach to detect, analyze, and respond to security incidents—from initial data collection by the Wazuh Agent to in-depth incident response by a SOC Analyst. This combination of automation and human expertise helps ensure that security events are handled in a timely and effective manner.

If there's any specific part of the diagram you'd like to discuss further or if you need more clarification, feel free to let me know!
