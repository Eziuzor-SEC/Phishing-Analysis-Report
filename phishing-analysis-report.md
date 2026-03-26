# Phishing Email Analysis Report

**Report ID:** PHI-001  
**Severity:** High  
**Category:** Phishing  
**Analyst:** Michael Eziuzor  
**Date:** March 2026  
**Platform:** LetsDefend  

---

## 1. Overview

This report documents the analysis of a suspicious phishing email reported 
by an internal user. The investigation follows standard SOC phishing analysis 
methodology including email header inspection, URL reputation analysis, 
attachment analysis, and threat intelligence lookups.

---

## 2. Email Details

- **Sender (Display Name):** Microsoft Security Team
- **Sender (Actual Address):** security-alert@microsft-verify.com
- **Reply-To:** harvester@malicious-domain.ru
- **Subject:** Urgent: Your Microsoft Account Has Been Compromised
- **Date Received:** February 14, 2024, 09:23 AM
- **Recipient:** internal.user@company.com

---

## 3. Header Analysis

Email header inspection revealed the following anomalies:

- **SPF:** FAIL — sending server not authorised for domain
- **DKIM:** FAIL — signature invalid
- **DMARC:** FAIL — message did not pass DMARC policy
- **Originating IP:** 185.220.101.45
- **Mail Server:** smtp.malicious-domain.ru
- **Spoofed Domain:** microsft-verify.com (typosquat of microsoft.com)

All three email authentication checks failed, confirming the email 
did not originate from a legitimate Microsoft server.

---

## 4. Threat Intelligence

**VirusTotal — 185.220.101.45**
- Flagged as malicious by 18 vendors
- Associated with phishing and credential harvesting campaigns

**AbuseIPDB — 185.220.101.45**
- 12,847 abuse reports
- Categorised as phishing and spam infrastructure

**URLScan.io — microsft-verify.com**
- Domain registered 3 days prior to email delivery
- Page mimics Microsoft account login portal
- Designed to harvest credentials

---

## 5. URL and Link Analysis

The email contained a single call-to-action button linking to:

`hxxp://microsft-verify.com/account/verify?token=a8f3k2`

- Domain is a typosquat of microsoft.com
- Newly registered domain (3 days old at time of delivery)
- Page renders a fake Microsoft login portal
- Form submits credentials to attacker-controlled backend

---

## 6. Attachment Analysis

No attachment was present in this email. The attack vector was 
exclusively link-based credential harvesting.

---

## 7. Attack Classification

- **Type:** Credential Harvesting Phishing
- **Technique:** Domain spoofing via typosquatting
- **Target:** Microsoft account credentials
- **Authentication Failures:** SPF, DKIM, DMARC all failed
- **Impact:** Potential account compromise if user clicks link

---

## 8. Conclusion

This is a confirmed phishing email. The sender spoofed Microsoft branding 
using a typosquatted domain registered days before the campaign. All email 
authentication mechanisms failed. The embedded link directs victims to a 
credential harvesting page mimicking the Microsoft account login portal. 
The originating IP has thousands of prior abuse reports confirming its 
use in phishing infrastructure.

The email did not bypass technical controls but represents a social 
engineering risk if delivered to end users.

---

## 9. Recommendations

- Block sender domain microsft-verify.com at email gateway
- Block originating IP 185.220.101.45 at firewall level
- Submit domain to Microsoft for phishing takedown
- Alert end users via security awareness communication
- Review email gateway rules for typosquat domain detection
- Implement DMARC enforcement policy if not already active
- Conduct phishing simulation training for staff

---

**Verdict:** Phishing Confirmed  
**User Clicked Link:** No  
**Escalation Required:** No — Blocked at gateway
