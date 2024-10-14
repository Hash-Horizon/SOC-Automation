# Diagram-SOC-Automation
# Network Security Flow

Thank you for sharing the diagram! Let's go through it in detail.

This diagram illustrates the process of security monitoring and incident handling using several components. Here's an explanation of each step and component visible in the diagram:

## 1. Windows 10 Client (Wazuh Agent)
- The client computer running Windows 10 is equipped with a Wazuh Agent.
- The agent is responsible for collecting events from the client system and sending them to the **Router** as the initial events.

## 2. Router
- The router receives events from the Wazuh Agent and forwards these events to the **Internet**.

## 3. Internet
- From the Internet, events are received by the **Wazuh Manager**.
- The Wazuh Manager is the central monitoring unit responsible for analyzing the incoming events from the agent.

## 4. Wazuh Manager
- **Receive Events**: The Wazuh Manager receives events sent by the Wazuh Agent.
- **Send Alerts**: After analyzing the events, the Wazuh Manager sends alerts to **Shuffle** if any suspicious activity or anomaly is detected.

## 5. Shuffle
- **Enrich IOCS**: Shuffle enriches Indicators of Compromise (IOCs) with additional information to provide better context about the threat.
- **Send Alerts**: Shuffle sends alerts to **TheHive** for incident management.
- **Send Email**: Shuffle also sends emails as part of the automated response to incidents.

## 6. TheHive
- TheHive is used for incident management and creating alerts within a case management system. With information from Shuffle, TheHive facilitates analysts in taking further action.

## 7. SOC Analyst
- **Send and Receive Email**: The SOC (Security Operations Center) Analyst is responsible for receiving alerts, analyzing them, and responding to the reported threats. They communicate through emails received from the monitoring system.

---

Overall, this diagram demonstrates the flow of information between various components for security monitoring, analysis, and incident response. The process starts from the client (Windows 10 with Wazuh Agent), proceeds through the Router and Internet, and is then processed by Wazuh Manager, Shuffle, and TheHive before finally reaching the SOC Analyst, who takes the final actions.

If there's any specific part of the diagram you'd like to discuss further or if you need more clarification, feel free to let me know!
