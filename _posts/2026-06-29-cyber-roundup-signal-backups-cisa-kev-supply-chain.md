---
layout: single
title: "Cyber Roundup: Russia Targets Signal Backup Keys, CISA Drops Urgent Deadlines, Supply Chain Week"
date: 2026-06-29 07:00:00 -0500
categories: [roundup]
tags: [russia, apt, supply-chain]
author_profile: true
---

This is 7562 InfoSec. A few times a week I'll post on whatever's actually moving in the threat landscape — current incidents, notable vulnerabilities, and occasionally a look back at attacks that shaped how we defend today. No vendor marketing, no hype cycles. Just what matters to practitioners.

This week: Russia is going after Signal backup keys, CISA issued hard deadlines on two actively exploited flaws, and developer tooling had a rough few days.

---

Russia upgraded its phishing campaign this week, and the new target is your Signal backup recovery key.

The FBI and CISA updated their March advisory on Russian intelligence operations against Signal users. The original campaign stole session credentials through phishing. The updated version goes further: attackers now pressure targets into surrendering their Signal Backup Recovery Keys. Hand that over and an adversary can restore your full message history on any device they control, independent of Signal's end-to-end encryption. The encryption layer held. The recovery mechanism is the weak point. If your organization treats Signal as a secure channel for anything sensitive, backup key hygiene belongs in your next tabletop.

Google TAG added context to the broader Russian picture. Turla, the FSB-linked APT, deployed a new .NET backdoor called STOCKSTAY against Ukrainian government and military targets. Two Russian APTs, two fresh toolkits, same week. The operational tempo out of Russia is not easing.

## CISA Added to the KEV and Gave Agencies a Hard Deadline

CISA added two critical vulnerabilities to the Known Exploited Vulnerabilities catalog this week, both actively exploited.

The first: a flaw in Cisco Unified Communications Manager. UCM is the kind of infrastructure that enterprise IT treats as untouchable. "Too critical to patch" is a posture I've seen kill organizations. The second: a remote code execution vulnerability in PTC Windchill PDMLink and FlexPLM. Windchill sits inside manufacturing and defense supply chains where patching requires change control boards and maintenance windows measured in quarters. Neither argument holds when CISA has confirmed active exploitation.

A public proof-of-concept also dropped for CVE-2026-55200, a critical memory corruption flaw in libssh2 that lets a malicious SSH server execute code on a connecting client. Cloud workloads and CI/CD runners are the main exposure.

## Developer Tooling Is Under Sustained Attack

Three separate supply chain attacks hit developer infrastructure this week. Hijacked npm and Go packages deployed a Python infostealer through VS Code Tasks. Miasma malware targeted npm packages and GitHub Actions workflows. A separate technique showed how a clean-looking GitHub repository can trick an AI coding agent into running a malicious payload that evades scanners because it looks like normal project setup code.

I've watched this pattern build in financial services environments. Developers extend implicit trust to their tooling. Lock down your package manager configs. Audit GitHub Actions permissions and pin to commit hashes, not tags. Before letting an AI agent clone and set up an unfamiliar repo, know what you're authorizing it to run.

Patch Cisco UCM. Check your Windchill version. Treat your Signal backup key like a root credential.
