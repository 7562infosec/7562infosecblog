---
layout: single
title: "FortiBleed Is Still Open, and Atlassian Took Two Hours"
date: 2026-10-08 07:00:00 -0500
categories: [roundup]
tags: [credential-theft, vulnerability, identity]
author_profile: true
---

**TL;DR:** The FBI says FortiBleed attackers are still creating their own FortiGate admin accounts and locking real admins out, and attackers hit Atlassian's CVE-2026-21589 two hours after a public PoC dropped. Kill every active FortiGate VPN session, diff your admin accounts, and patch Atlassian Data Center today.

The FBI and Secret Service warned Tuesday that FortiBleed is still active, and a password reset won't close it. The campaign surfaced in June with a leak of plaintext credentials for nearly 74,000 FortiGate devices. SOCRadar now counts 86,644 compromised. Attackers log in with harvested or sprayed credentials, pull more hashes off the box, and crack them offline on a GPU cluster. Then they create their own admin accounts and delete yours. INC, Lynx, and Payload ransomware affiliates buy the access, and the operator ranks targets by revenue.

I've walked into incidents where the team rotated the VPN password and called it contained. That fails here. The attacker already holds an admin account you never created. The FBI's list is the right one: terminate all active VPN sessions, audit every admin account, enforce MFA, restrict management access, and move admin password storage to PBKDF2. Legacy SHA-256 hashes are what got cracked.

Atlassian disclosed CVE-2026-21589 on Monday, an unauthenticated file-read bug across eight Data Center products including Jira, Confluence, and Bitbucket. watchTowr published a PoC showing how to read crowd.properties and turn those credentials into a Jira admin account in Crowd-integrated deployments. Previdian's honeypots logged exploitation attempts two hours later, and a Nuclei template followed. Your 30-day patch window for self-hosted collaboration tools is now competing with a two-hour one. Atlassian says it can't tell you whether your instance is already compromised, so check Crowd for any admin account created since Monday.

Google disclosed that attackers compromised third-party operators of the .gh, .sl, and .as country-code registries, rewrote authoritative DNS, and obtained valid HTTPS certificates for Google domains and other major brands. Google blocked the certs in Chrome through CRLSets. Firefox, Safari, and your API clients don't get that protection. A valid certificate proves someone controlled the domain at issuance. It says nothing about whether that someone was you.

Two smaller items. SonicWall shipped hotfixes for a new CVSS 10.0 pre-auth SSRF in SMA1000 gateways. And the Shai-Hulud worm turned up in a compromised Tensorlake npm package. Following Monday's Q3 lookback on supply chain trust, nothing about that lesson has changed: pin versions and know which secrets your build can reach.

Every story this week runs through access someone already trusted: a VPN login, an SSO config file, a DNS record, a package.

Today, terminate every active FortiGate VPN session and diff your admin account list against what you provisioned. Patch Atlassian Data Center or apply the WAF traversal rules. Then turn on Certificate Transparency monitoring and restrictive CAA records for every domain you own, parked ones included.
