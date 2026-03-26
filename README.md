
# DC-3 Red Team & Blue Team Lab

This project documents a full attack simulation on the DC-3 machine, followed by log analysis from a defensive perspective.

---

## 🔴 Red Team

The attack chain included:

- SQL Injection (Joomla 3.7.0)
- Database extraction using sqlmap
- Password hash cracking (John the Ripper)
- Admin panel access
- Remote Command Execution via template modification
- Reverse shell
- Shell upgrade (PTY)
- Privilege escalation → root access

Detailed steps and commands:
- red-team/report.md
- red-team/commands.md

---

## 🔵 Blue Team

After exploitation, logs were analyzed to identify traces of the attack:

- SQL Injection patterns in HTTP requests
- Automated tool detection (sqlmap user-agent)
- Suspicious parameters (`cmd=`)
- Reverse shell indicators
- HTTP 500 error correlation

Analysis and commands:
- blue-team/report.md
- blue-team/commands.md

---

##  Screenshots

The repository includes screenshots demonstrating:

- Initial access (SQL Injection)
- Reverse shell
- Root access
- Log analysis

---

##  Purpose

This project demonstrates both offensive techniques and how they can be detected from a defensive perspective.

---

Part of my cybersecurity learning journey.
