# crowdstrike-integration
Templates to collect Nasuni syslog events, including Advanced Ransomware Protection, and forward into CrowdStrike XDR events using Falcon NG-SIEM. The latest parser (Named nasuni-edge) should always be available to NG-SIEM customers when adding the Nasuni Edge Events Data Connector with the NG-SIEM console.

## About
CrowdStrike NG-SIEM extends real-time detection to external third parties by joining the CrowdStrike LogScale (formerly Humio) service into Falcon XDR and working with third party logs. This allows Nasuni syslog messages to be ingested and processed, then be made ready for search, reporting, dashboards and alert actions. Logs are collected using a premise-based collection agent, and into the storage repository for parsing and processing.

## Integration with Nasuni
The Falcon LogScale Collector is the native log shipper for NG-SIEM that runs on prem. It can forward Nasuni syslog events, to the correct LogScale repository. When collecting Advanced Ransomware incidents, event correlation with other Falcon sensor, other LogScale integrations, or combination thereof can be visualized or acted upon.

## Integration with CrowdStrike Falcon XDR
The Falcon NG-SIEM Collector forwards Nasuni syslog events into the correct NG-SIEM repository. When collecting Advanced Ransomware incidents, log correlation, incident creation and Fusion SOAR workflows can be executed.

## Support of the Integration
Nasuni Support is responsible for ensuring that the core Nasuni services, such as Nasuni’s syslog service, on which the integration is built are functioning properly. Nasuni is responsible for updating the parser template to meet product enhancements that may affect the operation of the parser. 

CrowdStrike supports the operation and troubleshooting of the log shipper (agent), NG-SIEM, XDR and other CrowdStrike components involved.


## Integration Requirements
* Nasuni syslog service must target a deployed collector.
* Operating System to Host a Falcon Logscale Collector (Linux or Windows).
* NEA Syslog Configuration
* NEA Audit Events (optional)
* CrowdStrike Falcon XDR and NG-SIEM Subscription
* The most up to date CrowdStrike/Nasuni integration guide can be found at https://falcon.us-2.crowdstrike.com/documentation/page/l30d7037/nasuni

## Integration Templates
* nasuni-syslog-collector-config.yaml
  * Provides an example configuration file to enable the LogScale collector to listen for syslog traffic and forward to the account.
* nasuni-edge-events.yaml
  * Log format parser that will create fields based on the current Nasuni Ransomware event message text, and also convert the JSON audit syslog events into fields.
* Nasuni_Alerts.yaml
  * Dashboard templates to display Ransomware events of the last hour, and correlated audit events of the last 5 minutes.
* Nasuni_Email_1.yaml
  * Automation action with email recipient information.
* Nasuni_RWP_Incident.yaml
  * A NG-SIEM rule template that will create an incident when NG-SIEM ingests a Nasuni syslog event of a ransomware detection and/or mitigation.
* Nasuni Edge Alert Device Containment.yaml
  * A SOAR workflow that when triggered by a Nasuni NG-SIEM alert with a client IP address, will lookup the host's agent ID where available and contain it. 

