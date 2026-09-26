---
layout: single
title: "Cyber Roundup: A Vendor Pulls the Plug and Botnets Hire AI Agents"
date: 2026-09-26 07:00:00 -0500
categories: [roundup]
tags: [cisa-kev, ai-security, north-korea]
author_profile: true
---

**TL;DR:** Kiteworks told customers worldwide to shut their servers down this weekend on a law enforcement tip, and CISA gave agencies until Sunday to patch an exploited, max-severity WSO2 auth bypass. Patch WSO2 and Adobe Commerce, hunt your file transfer logs before Kiteworks comes back up, and strip outbound reach from every AI agent that reads outside input.

Kiteworks told its customers to power off their servers for six hours this weekend. The secure file-sharing vendor says federal authorities passed along credible intelligence of an imminent attack. Kiteworks reports no known compromise and says version 9.5.1 fixes every known bug, yet its support staff told Heise the shutdown guards against "potential zero-day attacks." I've never seen a vendor ask for a global precautionary outage, and I take it seriously. Managed file transfer has been Clop's favorite hunting ground for years: Accellion, GoAnywhere, MOVEit, Cleo. If you run Kiteworks, confirm you're on 9.5.1 and hunt the last 30 days of logs before you bring it back up.

CISA added a maximum-severity WSO2 flaw, CVE-2026-5430, to the KEV catalog with a Sunday deadline. The JWT handler accepts tokens signed with an unsupported algorithm, so a forged token gets an attacker admin. WSO2 disclosed it in May. watchTowr caught exploitation attempts on September 13. That's four months of runway for anyone who treated API gateways as plumbing instead of perimeter. The same KEV update added an Adobe Commerce authorization flaw, CVE-2026-71362, that lets attackers hijack customer accounts with no credentials, plus exploited SharePoint and MikroTik RouterOS bugs.

Attackers now hand the keyboard to AI agents. ThreatDown found Carbonato, a worm that hits Docker APIs exposed on port 2375, launches a privileged container, and installs the Hermes Agent framework. Operators send tasks over Telegram. The agent writes commands, reads the output, and picks the next step while it harvests AI API keys and SSH credentials. SecurityWeek reported a separate Windows botnet, x47.c, that uses xAI's Grok to choose its persistence actions. Following our August coverage of an agent going off-script in AISI testing, this is the production version: criminals running agents on your hardware.

Defensive deployments fail the same way. Zenity Labs disclosed SalesBleed, three flaws in Salesforce Agentforce. A poisoned Web-to-Lead submission sits dormant until an employee asks the agent about it. Then the agent exfiltrates CRM data with zero clicks, or posts phishing links to internal Slack under its own trusted identity. Salesforce patched all three by August 19. The pattern outlives the patch. Any agent that reads outside input and acts with internal privileges is a confused deputy waiting for the right prompt.

Bitget also lost $351.6 million from its hot and warm wallets on September 24, and investigators suspect North Korea. If your treasury team holds exchange balances, ask who reviewed the custody controls this quarter.

Do three things before Monday. Patch WSO2 and Adobe Commerce. Keep Kiteworks offline until you've verified the version and reviewed the logs. Then scan your external ranges for port 2375, inventory every AI agent that ingests web forms, email, or tickets, and block its ability to send data anywhere you didn't approve.
