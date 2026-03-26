# Red Team Report – DC-3

## Initial Access
The target was vulnerable to SQL Injection in Joomla 3.7.0. Using sqlmap, I was able to extract the database contents.

## Credential Access
From the database dump, password hashes were obtained and cracked using John the Ripper.

## Privilege Escalation (Web)
With valid credentials, I logged into the Joomla admin panel and modified a template file to achieve remote command execution.

## Reverse Shell
A reverse shell was established using netcat, providing access to the target system.

## Privilege Escalation (System)
After gaining a shell, I exploited a local kernel vulnerability to escalate privileges and obtain root access.

## Result
Full system compromise (root access).
