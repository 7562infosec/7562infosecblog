---
layout: single
title: "PHP2Shell Lands While Storm-0940 Runs AI Agents Through ConnectWise"
date: 2026-10-22 07:00:00 -0500
categories: [roundup]
tags: [zero-day, ai-security, china]
author_profile: true
---

**TL;DR:** PHP2Shell exploits were live before the patch existed, and Storm-0940 used AI agents to turn ConnectWise credentials into access to customer Microsoft 365 tenants. Patch PHP to 8.5.12, 8.4.27, 8.3.36, or 8.2.35 today, then rotate every ConnectWise credential and review sign-ins from its application identities.

PHP2Shell is the emergency of the week. Two unauthenticated RCE flaws, CVE-2026-109618 and CVE-2026-109619, sit in the PHP runtime itself at CVSS 9.2 and reach back to builds since 5.4. Details leaked before the fix. Cloudflare, SecurityWeek's sensors, and SANS all logged exploit attempts while admins had nothing to install. Cloudflare pushed emergency WAF rules. Talos published Snort coverage. SANS raised InfoCON to yellow. PHP shipped 8.5.12, 8.4.27, 8.3.36, and 8.2.35 on October 21, and Krebs expects outages as operators scramble to update.

No vendor workaround existed before the patch, and the interim setting most people suggested did not close the hole on its own. I've watched this pattern in financial services: the exploit window closes before the change window opens. Rapid7's Q3 data puts average time to exploit for high-severity flaws at about three days. A monthly patch cycle loses that race by default. Inventory every PHP host today, including the forgotten WordPress box and the vendor appliance. Keep the WAF rules on until each host runs a fixed build.

Storm-0940 is the other story, and it sharpens what I wrote on August 20 about nation-states putting AI on offense. Microsoft ties the China-aligned group to the ConnectWise Cloud Backup compromise and says it ran an agentic pentesting tool called ARTEX. ConnectWise disabled seven application identities after attackers used them to log into customer Microsoft 365 tenants. It has since reset credentials and replaced application secrets, and Cloud Backup is still offline. ConnectWise says customer impact is unconfirmed. I would not wait for confirmation.

This is MSP risk in its plainest form. One vendor compromise hands an attacker a key to every tenant that vendor touches. Your backup provider's service account sits inside your Microsoft 365 tenant with real permissions, and nobody on your team reviews it like a user account.

Do two things today. Patch every PHP host to a fixed build. Then, if ConnectWise touches your environment, rotate its credentials, list every application identity it holds in Entra ID, and pull sign-in logs for those identities back to October 1.
