# CYBR8420 Project Proposal

# Team Name 
```
Titans
```
# Team Members 

Charitha Karnam (ckarnam@unomaha.edu), Lakshmi Prasanna Kaspa(lkaspa@unomaha.edu), Sai Tarun Battula(sbattula@unomaha.edu)

# Project: 

Nextcloud Server 


Github Link: [Nextcloudserver](https://github.com/nextcloud/server)

# License Information

All contributions to NextCloud repository from June, 16 2016 on are considered to be licensed under the AGPLv3 or any later version.

# Contribution

Nextcloud doesn't require a CLA (Contributor License Agreement). To modify an existing file, the existing license header has to be placed as it is and a copyright notice needs to be added. A Developer Certificate of Origin (DCO) is used as an additional safeguard to sign the commits contributors make.

# Repository Activity
```
Total Commits: 45,558 commits
Branches: 115 branches
Total releases : 431 releases
Contributors: 551
```
# Programming Languages usage breakdown:

  - PHP : 57%
  - JavaScript : 40%
  - CSS : 1%
  - Others : 2%

# Motivation:

Nextcloud server, is a secure all in one place where one can store their data and also specify access levels to other users. As the project itself deals with providing best possible security based services to users, it has caught our interest to pick this project. Another consensus by which we selected the project was due to the common programming expertise that we share together as a team. Nextcloud is mostly built with PHP and JavaScript..

# Description:

Nextcloud is a suite of client-server software for creating and using file hosting services. It is functionally similar to Dropbox, although Nextcloud is free and open-source, allowing anyone to install and operate it on a private server. In contrast to proprietary services like Dropbox, the open architecture allows adding functionality to the server in the form of applications and enables users to have full control of their data.
  
# Features!


  - Nextcloud users can manage calendars, contacts, scheduled tasks and streaming media  from within the platform.
  - Content can be shared by defining granular read/write permissions between users and/or groups.
  - Nextcloud users can create public URLs when sharing files. Logging of file-related actions, as well as disallowing access based on file access rules is also available.
  - Users can interact with the browser-based text editor, bookmarking service, URL shortening suite, gallery, RSS feed reader and document viewer tools from within Nextcloud.

# Some essential security needs

  - Secure the storage of client files.
  - Restrict the access of user's data to other users or groups.
  - Provide encryption to the user data to provide confidentiality.
  - Have counter measures to contain the damage caused by any malicoius programs.
  - Ability to invalidate the session if device is stolen.
  - Secure the server from different types of attacks like Man-in-the-middle, DDOS etc.
  
 # Security Features

  - The system uses PGP key to ensure confidential submission and authentication.
  - Next cloud server uses bcrypt algorithm for security and performance thus avoiding Denial-of-service attacks.
  - Nextcloud uses a RFC 4086 compliant mixer to generate cryptographically secure pseudo-random numbers.
  - The project sites (website, repository, and download URLs) support HTTPS using TLS.
  - The security mechanisms within the software produced by the project implements perfect forward secrecy for key agreement protocols   so a session key derived from a set of long-term keys cannot be compromised if one of the long-term keys is compromised in the future.

# Security related history

 **A missing sanitization of search results for an autocomplete field could lead to a stored XSS requiring user-interaction**
        
      This missing sanitization only affected group names, hence malicious search results could only be crafted by privileged users like admins or group admins.

**Improper checks of dropped permissions**

    Nextcloud Server before 12.0.8 and 13.0.3 suffers from improper checks of dropped permissions for incoming shares allowing a user to still request previews for files it should not have access to.

**Improper authentication**

    Nextcloud Server before 12.0.8 and 13.0.3 suffer from improper authentication on the OAuth2 token endpoint. Missing checks potentially allowed handing out new tokens in case the OAuth2 client was partly compromised.

**Breach of Privacy**
    
    Nextcloud Server before 10.0.4 and 11.0.2 are vulnerable to disclosure of calendar and address book names to other logged-in users. Note that no actual content of the calendar and address book has been disclosed.
    
**XSS vulnerabilities**
    
    Nextcloud Server before 9.0.58 and 10.0.5 and 11.0.3 are vulnerable to an inadequate escaping of error messages leading to XSS vulnerabilities in multiple components.

# Project Links

Nextcloud Server - https://github.com/nextcloud/server
Trello Project Board - https://trello.com/b/gPTAEzv4/sa-nextcloud


