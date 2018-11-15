
## Threat Model Diagram
[Threat Model Report](http://htmlpreview.github.com/?https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Threat_Modeling/Threat_Report_R1.htm)

## Threat Model Analysis
### Threat: An adversary may leverage the lack of monitoring systems and trigger anamolous traffic to database.
Mitigation: Nextcloud logs all database access and provides a sufficient monitoring system to prevent any anamolous traffic to database.Monitoring and systems intelligence tools openNMS and Splunk have support for monitoring Nextcloud 10+ systems.Admins can also opt for logging to the systemd log, allowing them to manage all logs of the system in one place. When enabled, the audit log is in a separate file.

### Threat: An adversary can tamper critical database securables and deny the action.
Mitigation: No digital signature is provided to the critical database securables and there is a risk of rogue user to tamper the critical database securables.

### Threat: An adversary can deny access on database due to lack of auditing.
Mitigation: Nextcloud logs data in the nextcloud.log file provided in the root of its data directory. We can optionally record a full audit trail there, provided the ‘info’ log level is set. This can be used by Data Loss Prevention and Mobile Device Management tools as user agent information is available alongside extensive user, IP and date/time logs.The audit logging feature in Nextcloud is at the moment missing some logs for things like "Accessing previews of files".

### Threat: An adversary can gain access data by performing SQL injection.
Mitigation: Next cloud emphasises to use prepared queries.If App framework is used it mentions the user to use the syntax to extend mapper class But it doesnot provide any mechanism to stop SQL injection.

### Threat: An adversary can gain access to sensitive data in database
Mitigation: Nextcloud offers multiple layers of encryption for data. First, data is protected when being transferred between clients and servers as well as between servers. Second, data can be encrypted on storage, end-to-end encryption is provided to the clients.However column level Encryption is not provided in Nextcloud.Hence there is a need to implement Column Level Data Encryption.

### Threat: An adversary can gain unauthorized  access to database due to loose authorization rules
Mitigation: It is mentioned that Nextcloud administrators  are ultimately trusted. It is for example expected behavior that a Nextcloud administrator can execute arbitrary code.Hence no proper mitigation is provided for this threat of Elevation of privilges.

### Threat : An adversary can gain unauthorized access to database due to lack of network access protection at firewall level
Mitigation: Nextcloud has the File Access Control app which acts as a bit of a firewall and while it helps protect businesses secrets, there are use cases for home users as well.
## Project Task Board

[Trello Project Board](https://trello.com/b/PG39aw1z/sa-project-task-4-threat-modeling)
