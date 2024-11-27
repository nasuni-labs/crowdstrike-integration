# crowdstrike-integration
Templates to collect Nasuni syslog events, including Advanced Ransomware Protection, and forward into CrowdStrike XDR events using Falcon NG-SIEM.

## About
CrowdStrike NG-SIEM extends real-time detection to external third parties by joining the CrowdStrike LogScale (formerly Humio) service into Falcon XDR and working with third party logs. This allows Nasuni syslog messages to be ingested and processed, then be made ready for search, reporting, dashboards and alert actions. Logs are collected using a premise-based collection agent, and into the storage repository for parsing and processing.

## Integration with Nasuni
The Falcon LogScale Collector is the native log shipper for NG-SIEM that runs on prem. It can forward Nasuni syslog events, to the correct LogScale repository. When collecting Advanced Ransomware incidents, event correlation with other Falcon sensor, other LogScale integrations, or combination thereof can be visualized or acted upon.

## Integration with CrowdStrike Falcon XDR
The Falcon NG-SIEM Collector forwards Nasuni syslog events into the correct NG-SIEM repository. When collecting Advanced Ransomware incidents, log correlation, incident creation and Fusion SOAR workflows can be executed.

## Integration Requirements
* Nasuni syslog service must target a deployed collector.
* Operating System to Host a Falcon Logscale Collector (Linux or Windows).
* NEA Syslog Configuration
* NEA Audit Events (optional)
* CrowdStrike Falcon XDR and NG-SIEM Subscription

## Integration Templates
* nasuni-syslog-collector-config.yaml
  * Provides an example configuration file to enable the LogScale collector to listen for syslog traffic and forward to the account.
* nasuni-edge-events.yaml
  * Log format parser that will create fields based on the current Nasuni Ransomware event message text, and also convert the JSON audit syslog events into fields.
* Nasuni_Alerts.yaml
  * Dashboard templates to display Ransomware events of the last hour, and correlated audit events of the last 5 minutes.
* Nasuni_Email_1.yaml
  * Automation action with email recipient information.
