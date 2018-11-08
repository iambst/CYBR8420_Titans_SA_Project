
## Threat Model Diagram

## Threat Model Analysis
Threat: An adversary can gain access to sensitive data in database
Mitigation: Nextcloud offers multiple layers of encryption for data. First, data is protected when being transferred between clients and servers as well as between servers. Second, data can be encrypted on storage; end-to-end encryption is provided to the clients.However column level Encryption is not provided in Nextcloud.Hence there is a need to implement Column Level Data Encryption.

Threat: An adversary can gain unauthorized  access to database due to loose authorization rules
Mitigation: It is mentioned that Nextcloud administrators  are ultimately trusted. It is for example expected behavior that a Nextcloud administrator can execute arbitrary code.Hence no proper mitigation is provided for this threat of Elevation of privilges.

Threat : An adversary can gain unauthorized access to database due to lack of network access protection at firewall level
Mitigation: Nextcloud has the File Access Control app which acts as a bit of a firewall and while it helps protect businesses secrets, there are use cases for home users as well.
## Project Task Board

[Trello Project Board](https://trello.com/b/PG39aw1z/sa-project-task-4-threat-modeling)
