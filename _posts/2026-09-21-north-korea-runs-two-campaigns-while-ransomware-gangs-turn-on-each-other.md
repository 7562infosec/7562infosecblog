---
layout: single
title: "North Korea Ran Two Campaigns This Week, and Ransomware Gangs Started Robbing Each Other"
date: 2026-09-21 07:00:00 -0500
categories: [roundup]
tags: [north-korea, ransomware, ai-security]
author_profile: true
---

**TL;DR:** Microsoft patched a maximum-severity Azure AI Foundry flaw and CISA flagged three actively-exploited Linux kernel bugs, while North Korea's WaterPlum and Jade Sleet crews ran parallel campaigns and ShinyHunters turned on the Clop ransomware gang. Confirm your kernel patch level against the new CISA entries, and audit what has standing access to your AI platforms.

Microsoft's Azure AI Foundry picked up a CVSS 10.0 this week: CVE-2026-85889 let attackers escalate privileges with no authentication required. Microsoft patched it server-side, so there's nothing for customers to deploy, but that's exactly the problem. Teams have started treating AI platforms as somebody else's infrastructure to secure. I've watched this pattern before with cloud services generally: shared responsibility gets mistaken for no responsibility. AI Foundry runs your models and touches your data. Audit who has access to it the same way you'd audit access to a production database, because a vendor patch doesn't tell you whether that access was already abused before the fix shipped.

CISA added three actively-exploited Linux kernel flaws to its Known Exploited Vulnerabilities catalog this week, including CVE-2025-39682 at 9.8. If you're still running kernel versions from before this summer's patch cycle, that's not a compliance gap. That's an open door with a KEV entry now attached to it.

North Korea ran a full slate this week, on two separate fronts. WaterPlum operators infected roughly 30,000 devices across more than 100 countries by posing as recruiters, luring developers and crypto specialists into fake job interviews, and walked away with more than $10.7 million in stolen cryptocurrency. Separately, Jade Sleet compromised an India-based IT services provider using two new backdoors, FLATROOF and ROOFDECK, continuing the group's pattern of targeting developers to reach downstream networks. Two different DPRK-linked crews, two different playbooks, same result: developer machines are still the softest target in most environments. If your engineers are installing anything a "recruiter" sent them, that's a security incident, not a career opportunity.

ShinyHunters, the extortion crew we've flagged in past roundups, didn't attack a company this week. They attacked the Clop ransomware gang's own leak site, defaced it, and are now threatening to expose Clop's victim data and keys themselves. Ransomware-as-a-service has a reputation problem when the criminals start extorting each other. It doesn't change your threat model directly, but it's worth watching: when leak-site infrastructure gets this unstable, stolen data can surface through channels you're not monitoring.

Action item: pull your kernel version against the new CISA KEV entries today, and don't let "the vendor already fixed it" talk you out of checking who has standing access to your AI platforms this week.
