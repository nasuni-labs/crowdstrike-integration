# crowdstrike-integration
Templates to trigger CrowdStrike XDR with Advanced Ransomware Protection Events using LogScale and Tines
CrowdStrike LogScale

## About
CrowdStrike LogScale (formerly Humio) is a log and event collection platform that includes search, reporting, dashboards and alert actions. The platform collects logs/events through an API integration, or otherwise a log collection agent, and into a storage repository for parsing and ingest.

## Integration with Nasuni
The Falcon LogScale Collector is the native log shipper for LogScale. It can collect and send Nasuni syslog events, then using secure ingest tokens route data to the correct LogScale repository. When collecting Advanced Ransomware incidents, event correlation with other Falcon sensor, other LogScale integrations, or combination thereof can be visualized or acted upon.

## Integration with CrowdStrike Falcon XDR
LogScale promotes a 3rd party integration with Tines, a workflow automation service builder. It allows for custom built workflows that can accept webhooks from LogScale, and from there an API request can be made to a Falcon instance to perform actions such as containing hosts. It 

The community edition limits are currently:
•	3 Builders
•	1 Team
•	Unlimited viewers
•	3 Stories
•	500 Story Runs Daily

## Integration Requirements
•	NEA Syslog Configuration
•	NEA Audit Events (optional)
•	CrowdStrike Falcon XDR and API
•	CrowdStrike Logscale Endpoint
•	Tines Environment

## Integration Templates
•	nasuni-syslog-collector-config.yaml
o	Provides an example configuration file to enable the LogScale collector to listen for syslog traffic and forward to the account.
•	nasuni-syslog-parser.yaml
o	Log format parser that will create fields based on the current Nasuni Ransomware event message text, and also convert the JSON audit syslog events into fields.
•	Nasuni_Alerts.yaml
o	Dashboard templates to display Ransomware events of the last hour, and correlated audit events of the last 5 minutes.
•	Nasuni_Tines_Webhook.yaml
o	Automation action to create a webhook to Tines.
•	Nasuni_Email_1.yaml
o	Automation action with email recipient information.
•	NasuniRansomwareDetectionEventon{field host}Template.yaml
o	Automation alert that will act on detection of a Ransomware event, and will execute two actions (email and webhook).
•	NasuniRansomwareMitigationhasOccuredon{field host}Template.yaml
o	Automation alert that will act on mitigation of a Ransomware event, and will execute two actions (email and webhook).
•	contain-a-registered-device-with-crowdstrike.json
o	Tines Story template for listening on a webhook, establishing a connection to Falcon XDR, which will learn the client based on the host IP address, then peform an isolation action.
