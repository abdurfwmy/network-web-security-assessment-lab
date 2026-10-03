# Network & Web Application Security Assessment Lab

A hands-on cybersecurity project involving the assessment of an intentionally vulnerable virtual laboratory environment.

The project demonstrates a practical security assessment workflow covering **network reconnaissance, service enumeration, vulnerability identification, controlled exploitation, web application security testing, evidence collection, and remediation**.

> **Lab environment:** Kali Linux → Metasploitable 2 / DVWA
> **Purpose:** Educational and defensive cybersecurity testing

---

## 🧪 Lab Environment

| Component               | Details              |
| ----------------------- | -------------------- |
| Security Testing System | Kali Linux           |
| Target System           | Metasploitable 2     |
| Web Application         | DVWA                 |
| Virtualization          | VMware Workstation   |
| Network                 | Isolated Virtual Lab |

---

## 🛠️ Tools Used

* **Nmap** — Network reconnaissance and service enumeration
* **Metasploit Framework** — Controlled vulnerability exploitation
* **SearchSploit** — Vulnerability research
* **cURL** — HTTP testing
* **Firefox Developer Tools** — HTTP request analysis
* **DVWA** — Web application security testing
* **Metasploitable 2** — Intentionally vulnerable target
* **VMware Workstation** — Virtual lab environment

---

## 🔎 Assessment Methodology

The assessment followed a simplified security testing workflow:

```text
Lab Setup
   ↓
Network Discovery
   ↓
Port & Service Enumeration
   ↓
Vulnerability Identification
   ↓
Controlled Exploitation
   ↓
Web Application Testing
   ↓
Evidence Collection
   ↓
Impact Analysis
   ↓
Remediation
```

---

# 1. Network Security Assessment

## Network Discovery

The Metasploitable 2 target was identified at:

`192.168.204.129`

Connectivity was verified before beginning the security assessment.

## Service Enumeration

Nmap service/version detection identified multiple exposed services, including:

* FTP — vsftpd 2.3.4
* SSH — OpenSSH
* Telnet
* HTTP — Apache
* SMB — Samba
* MySQL
* PostgreSQL
* VNC
* Apache Tomcat

The service enumeration output is included in the project evidence.

---

## vsftpd 2.3.4 Vulnerability

The FTP service was identified as running **vsftpd 2.3.4**.

SearchSploit was used to research the service version, followed by a controlled Metasploit test against the intentionally vulnerable Metasploitable 2 system.

The test successfully established a command shell.

Privilege verification returned:

```text
root
```

The `id` command confirmed:

```text
uid=0(root) gid=0(root)
```

### Impact

Successful exploitation demonstrated how a vulnerable exposed service could result in unauthorized command execution with root-level privileges.

### Remediation

* Upgrade vulnerable software to a supported version.
* Disable unnecessary services.
* Restrict administrative services using firewall rules.
* Apply least-privilege principles.
* Monitor exposed services.
* Perform regular vulnerability assessments.

---

# 2. Web Application Security Assessment

## DVWA

**Damn Vulnerable Web Application (DVWA)** was used as the intentionally vulnerable web application.

DVWA was configured to **Low** security level for controlled testing.

---

## SQL Injection

The DVWA SQL Injection functionality was tested using controlled input.

Normal input returned an individual database record.

A crafted SQL injection payload caused multiple database records to be returned.

Firefox Developer Tools were also used to inspect the HTTP request containing the supplied input.

### Impact

SQL injection can allow manipulation of database queries and may result in unauthorized access to database information depending on the application's implementation and database privileges.

### Remediation

* Use parameterized queries and prepared statements.
* Avoid constructing SQL queries directly from user input.
* Validate user input appropriately.
* Apply least-privilege database permissions.
* Implement secure error handling.
* Perform regular application security testing.

---

## Reflected Cross-Site Scripting (XSS)

The DVWA Reflected XSS functionality was tested using controlled JavaScript input.

The supplied JavaScript executed in the browser and generated a JavaScript alert, demonstrating reflected XSS behavior.

### Impact

Reflected XSS can allow attacker-controlled JavaScript to execute within a victim's browser context when the victim interacts with a maliciously crafted request or link.

### Remediation

* Apply context-aware output encoding.
* Validate and appropriately handle user input.
* Avoid inserting untrusted input directly into HTML or JavaScript contexts.
* Consider an appropriate Content Security Policy.
* Follow secure application development practices.

---

# 3. Evidence

Evidence collected during the assessment includes:

* Network service enumeration
* Normal SQL injection behavior
* Successful SQL injection
* Captured SQL injection request
* Reflected XSS execution
* Successful vsftpd exploitation
* Root privilege verification

Screenshots and supporting evidence are available in the project repository.

---

# 4. Key Learning Outcomes

This project provided practical experience with:

* Network reconnaissance
* Nmap service enumeration
* Vulnerability research
* Metasploit Framework
* Linux command-line investigation
* Web application security testing
* SQL injection
* Reflected XSS
* HTTP request analysis
* Evidence collection
* Vulnerability impact analysis
* Security remediation

---

# 5. Project Structure

```text
network-web-security-assessment-lab/
│
├── README.md
├── security-assessment.md
│
└── cyber-lab SS/
    └── Screenshots and assessment evidence
```

---

# ⚠️ Disclaimer

This project was conducted exclusively within an isolated virtual laboratory using intentionally vulnerable systems for educational and defensive cybersecurity purposes.

No third-party systems were targeted.

---

## Author

**Abdurrahman Fawmy**

Cyber Security & Digital Forensics
Network Security • Cloud Security • Digital Forensics
