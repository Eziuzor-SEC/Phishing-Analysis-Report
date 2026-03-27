# Phishing Analysis Report — atendimento-fluxo-online.shop

**Report ID:** PHI-001  
**Submission ID:** PhishTank #9377269  
**Severity:** High  
**Category:** Phishing — Credential Harvesting  
**Analyst:** Michael Eziuzor  
**Date:** March 27, 2026  
**Source:** PhishTank  

---

## 1. Overview

This report documents the analysis of a live phishing site submitted to 
PhishTank on March 27, 2026. The site targets Portuguese-speaking users, 
specifically impersonating a Brazilian government or official service portal. 
The investigation covers URL analysis, threat intelligence lookups, 
infrastructure analysis, and detection findings.

---

## 2. Phishing Site Details

- **Phishing URL:** hxxps://atendimento-fluxo-online[.]shop/
- **Status:** Live (HTTP 200) at time of analysis
- **Page Title:** Efetuar Análise (Portuguese: "Perform Analysis")
- **Target:** Brazilian users — impersonates official government/service portal
- **Submitted to PhishTank:** March 27, 2026 at 15:27 UTC
- **Server:** Apache
- **Content Type:** text/html

---

## 3. Threat Intelligence

**VirusTotal — atendimento-fluxo-online.shop**
- 1/95 security vendors flagged as malicious
- Vendor detection: ESET — Phishing
- First submitted: March 27, 2026
- Body SHA-256: 368c5c189352af9f0c18f69d0a0a69c65a0876749d9014c180020b2ce6805104

**AbuseIPDB — 88.80.17.168**
- No prior abuse reports — newly deployed infrastructure
- ISP: PRQ Dynamic VPN network
- Usage Type: Data Center / Web Hosting / Transit
- Country: Sweden, Stockholm
- Hostname: portal-oficial-bombeiros-edital.shop

---

## 4. Infrastructure Analysis

The phishing site is hosted on IP 88.80.17.168, operated by PRQ, a Swedish 
hosting provider historically associated with bulletproof hosting services 
that tolerate abuse complaints. The hostname on the same IP — 
portal-oficial-bombeiros-edital.shop — impersonates the Brazilian fire 
department (Bombeiros), suggesting a coordinated campaign targeting 
Brazilian government service impersonation across multiple domains.

The .shop TLD and freshly registered domain are consistent with 
disposable phishing infrastructure designed to evade blocklists before 
being abandoned.

---

## 5. URL Analysis

- **Domain:** atendimento-fluxo-online.shop
- **TLD:** .shop — commonly abused for phishing
- **Translation:** "atendimento" = attendance/service, "fluxo" = flow, 
  "online" = online — mimics a legitimate Brazilian customer service portal
- **Redirection:** HTTP redirects to HTTPS version of same domain
- **Last Modified:** March 26, 2026 — created one day before submission

---

## 6. Attack Classification

- **Type:** Credential Harvesting / Social Engineering
- **Target Region:** Brazil — Portuguese-speaking users
- **Impersonation:** Brazilian government or official service portal
- **Infrastructure:** Bulletproof hosting (PRQ, Sweden)
- **Detection Rate:** Low (1/95) — actively evading most security vendors
- **Status:** Live at time of analysis

---

## 7. Conclusion

This is a confirmed phishing site targeting Brazilian users by impersonating 
an official government or customer service portal. The site was live at the 
time of analysis with a low detection rate of 1/95 vendors, indicating 
it was recently deployed and actively evading security tooling. The hosting 
infrastructure on PRQ — a provider associated with bulletproof hosting — 
and the related hostname impersonating the Brazilian fire department suggest 
this is part of a broader coordinated phishing campaign targeting Brazilian 
government service impersonation.

---

## 8. Recommendations

- Block domain atendimento-fluxo-online.shop at DNS and web proxy level
- Block IP 88.80.17.168 at firewall level
- Report domain to ESET and other vendors for expanded detection
- Submit to Google Safe Browsing and Microsoft SmartScreen for blocklisting
- Monitor for related domains hosted on the same IP infrastructure
- Alert users to verify URLs before entering personal information on 
  any government service portal

---

**Verdict:** Confirmed Phishing Site  
**Threat Level:** High  
**Escalation Required:** No — site blocked at gateway level  
**Analyst:** Michael Eziuzor | github.com/Eziuzor-SEC
