
## Threat Model Diagram
[Threat Model Report](http://htmlpreview.github.com/?https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Threat_Modeling/Threat_Report_R1.htm)

## Threat Model Analysis
### Threat: Elevation Using Impersonation
### Mitigation:
Nextcloud offers three simple checks to prevent additional privileges by attacker or Auth bypass.
*	OCP\JSON::checkLoggedIn(): Checks if the logged in user is logged in
*	OCP\JSON::checkAdminUser(): Checks if the logged in user has admin privileges
*	OCP\JSON::checkSubAdminUser(): Checks if the logged in user has group admin privileges.
Using the App Framework, these checks are already automatically performed for each request and have to be explicitly turned off by using annotations.

### Threat:Spoofing of the Third-Party WebServer External Destination Entity
### Mitigation:Nextcloud can be run through a reverse proxy, which can cache static assets such as images, CSS or JS files, move the load of handling HTTPS to a different server or load balance between multiple servers.Next cloud emphasizes to define the trusted proxies parameter  as an array of IP address to define the servers Nextcloud should trust as proxies. Nextcloud uses the de-facto standard header ‘X-Forwarded-For’ by default, but this can be configured with the forwarded_for_headers parameter. This parameter is an array of PHP lookup strings, for example ‘X-Forwarded-For’ becomes ‘HTTP_X_FORWARDED_FOR’. If the parameter is set incorrectly there is a chance for clients to spoof their IP address as visible to Nextcloud, even when going through the trusted proxy.

### Threat:External Entity Third-Party WebServer Potentially Denies Receiving Data
### Mitigation:In Nextcloud server data storage can be encrypted using a default military grade AES-256 encryption with server-based or custom key management which prevents external entity writing data.

### Threat:Data Flow Checks User Access Rights Is Potentially Interrupted
### Mitigation:Data Transfer from Nextcloud employs industry-standard TLS to encrypt data in transfer. This prevents interruption of data flow across a trust boundary in either direction.

### Threat:
### Mitigation:

### Threat:
### Mitigation:

### Threat:
### Mitigation:

### Threat:
### Mitigation:

### Threat:
### Mitigation:

### Threat:
### Mitigation:


[Trello Project Board](https://trello.com/b/PG39aw1z/sa-project-task-4-threat-modeling)
