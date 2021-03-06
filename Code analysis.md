
# Code Analysis-Nextcloud server
## Code Review Strategy:
Our Code Review Strategy is based on checklist based code review strategy to analyze the nextcloud code for any defects that may lead to critical security issues. While reviewing the code, we considered the areas where security plays a major role. Our main focus is on the below entities.
Oauth
Encryption
Files_external
Files_sharing
Twofactor-backupcodes
#### Oauth: 
OAuth (Open Authorization) is an open standard for token-based authentication and authorization on the Internet. It allows an end user's account information to be used by third-party services, such as Facebook, without exposing the user's password.
#### Encryption:
The data is encrypted both on storage and on data transfer.
#### Files_external:
External Files are accessed by Nextcloud server
#### Files_sharing :
Files from third party entities are shared by Nextcloud server.
#### Twofactor-backupcodes:
Nextcloud provides two factor authentication and an in built bruteforce mechanism.<br/>
We also analyzed code based on our Threat model and misuse cases identified.

## Manual Code Review:
In Filesharing functionality we observed that the data is directly written to screen without any validation or sanitization. It was not clear if the variable is controlled by the user which may lead to potential XSS attack.
```javascript
public function isFieldInResponse($field, $contentExpected){
		if (count($data->element) > 0){
			foreach($data as $element) {
				if ($contentExpected == "A_TOKEN"){
					return (strlen((string)$element->$field) == 15);
				}
				elseif ($contentExpected == "A_NUMBER"){
					return is_numeric((string)$element->$field);
				}
				elseif($contentExpected == "AN_URL"){
					return $this->isExpectedUrl((string)$element->$field, "index.php/s/");
				}
				elseif ((string)$element->$field == $contentExpected){
					return True;
				}
				else{
					print($element->$field);
				}
			}

```
In the Encryption module we found that a code of line uses a pseudo-random number generation that is not cryptographically secure.
```javascript
private function randomString() {
		return sha1(uniqid(mt_rand(), true));
	}
```
The below code is vulnerable to code injection as it fails to account for dangerous PCRE modification flags in the input string because of usage of preg_replace function.It is harmful when used with user controlled parameters and may facilitate direct attacks against the web server.A function named preg_quote() can be used which will quote any nasty characters in the input string and prevent code injection.
```javascript
/**
* @When the CSRF token is extracted from the previous response
*/
public function theCsrfTokenIsExtractedFromThePreviousResponse() {
$this->requestToken = substr(preg_replace('/(.*)data-requesttoken="(.*)">(.*)/sm', '\2', $this->response->getBody()->getContents()), 0, 89);
		}
```



## Automated Code Analysis Review:

The Static Code Analysis is performed using Visual Code Grepper, Parse Security Scanner and Codacy. 

#### Visual Code Grepper: 

This tool is an automated code security review tool and it looked for issues related to bad/insecure code. One primary issue reported by this tool is a File Inclusion Vulnerability where a user-supplied file was included without proper validation. It reported many false positives on potential XSS. 

[Link to report](http://htmlpreview.github.com/?https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/visualCodeGrepper.html)

#### Parse Security Scanner:

The Parse scanner is a static scanning tool to review PHP code for potential security-related issues. One primary issue reported is that one function output contents directly and this might lead to a potential injection.Most issues reported by this scanner are Style Checking and Type Checking type of errors and were not very useful. 

[Link to report](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/ParseCodeReviewResults.txt)


## Summary of Findings:
* By viewing the code issues pointed out by Visual Code Grepper we could majorly categorize the errors into three categories:
  - Nextcloud server appears to allow the use of an unvalidated variable when executing a command.
  - Potential XSS attacks.
  - Bugs related to MD5 algorithm being used in the application with regard to Encryption.

  The tool reported a File Inclusion Vulnerability which has high risk associated with it. The other issues were related to stylechecks   and improper declaration and usage of variables and some unfinished code which could cause low-level issues.

* We also analyzed code with codacy which reported errors related to Cross-site Request Request Forgery, SQL Injections, XSS attacks       which have a medium risk level.

* The errors reported by Parser Scanner were mostly related to Logical Operators, Hardcoded Sensitive Values, TypeSafe In Array.These     are of type Style Checking and are trivial. 

* In the manual code analysis we could identify a potential XSS attack, an issue with Encryption, we also could find out various           instances where the variable is directly outputted leading to possible injections.

To summarize, nextcloud has some code quality issues with the way logical operators are handled and input is validated. These are commonly reported by all tools though they are not critical for the application. Our key findings from the manual and automated code analysis are mapped to the following Common Weaknesses Enumeration. 

* [CWE-79](https://cwe.mitre.org/data/definitions/79.html) : Improper Neutralization of Input During Web Page Generation

* [CWE-338](https://cwe.mitre.org/data/definitions/338.html) : Use of Cryptographically Weak Pseudo-Random Number Generator

* [CWE-98](https://cwe.mitre.org/data/definitions/98.html) : Improper Control of Filename for Include/Require Statement in PHP Program 

From the above CWE we identified the attack pattern [CAPEC-73](https://capec.mitre.org/data/definitions/73.html): User-Controlled Filename

## Contribution Plan

We are planning to place a pull request regarding the data being outputted directly without any validation in the File sharing functionality which could lead to XSS attack.

## Project Board

[Project Board](https://trello.com/b/bKN8AWRw/sa-project-task-5-code-analysis)


