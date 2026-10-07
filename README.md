# SWYNEX-Web-Security-Review

## Overview

This repository contains a defensive web security review performed against an intentionally vulnerable Metasploitable2/DVWA training environment.

The assessment focused on identifying exposed web services, legacy software, exposed applications, and a reflected Cross-Site Scripting (XSS) vulnerability.

## Target

- IP Address: `192.168.126.128`
- Environment: Metasploitable2 / DVWA
- Assessment Type: Authorized local security lab

## Tools Used

- Nmap
- Web Browser
- DVWA
- Metasploitable2

## Key Findings

### 1. Legacy Apache HTTP Server 2.2.8
**Severity: High**

Nmap identified Apache HTTP Server 2.2.8 running on the target.

**Recommendation:** Upgrade to a supported version and apply current security updates.

### 2. Legacy Apache Tomcat 5.5
**Severity: High**

Apache Tomcat 5.5 was identified on TCP port 8180. The Tomcat default page and management interfaces were accessible.

**Recommendation:** Upgrade Tomcat, restrict management interfaces, and remove unnecessary default applications.

### 3. Reflected Cross-Site Scripting (XSS)
**Severity: High**

A harmless JavaScript alert payload was submitted to the DVWA Reflected XSS functionality. The payload executed successfully in the browser.

**Recommendation:** Use context-aware output encoding, secure input handling, safe DOM APIs, and a restrictive Content Security Policy.

### 4. Multiple Web Applications Exposed
**Severity: Medium**

The target exposed multiple web applications, including DVWA, Mutillidae, phpMyAdmin, TWiki, and WebDAV.

**Recommendation:** Remove or disable applications that are not required and restrict administrative interfaces to authorized users.

## Evidence

Screenshots documenting the assessment are available in the `screenshots` directory.

The complete assessment report is available here:

`SWYNEX-Web-Security-Review.pdf`

## Remediation Summary

- Upgrade legacy Apache and Tomcat versions.
- Restrict administrative interfaces.
- Remove unnecessary web applications.
- Apply secure output encoding to prevent XSS.
- Implement appropriate security headers and Content Security Policy.
- Perform follow-up security testing after remediation.

## Scope

All testing was performed only against the authorized local training environment. No third-party systems were targeted.
