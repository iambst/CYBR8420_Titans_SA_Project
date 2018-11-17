
## Threat Model Diagram
[Threat Model Report](http://htmlpreview.github.com/?https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Threat_Modeling/Threat_Report_R1.htm)

## Threat Model Analysis
### Threat: Elevation Using Impersonation
### Mitigation:
Nextcloud offers three simple checks to prevent additional privileges by attacker or Auth bypass.
•	OCP\JSON::checkLoggedIn(): Checks if the logged in user is logged in
•	OCP\JSON::checkAdminUser(): Checks if the logged in user has admin privileges
•	OCP\JSON::checkSubAdminUser(): Checks if the logged in user has group admin privileges
Using the App Framework, these checks are already automatically performed for each request and have to be explicitly turned off by using annotations.




[Trello Project Board](https://trello.com/b/PG39aw1z/sa-project-task-4-threat-modeling)
