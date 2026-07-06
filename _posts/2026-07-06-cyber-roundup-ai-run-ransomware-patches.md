---
layout: single
title: "Cyber Roundup: AI-Run Ransomware and the Patches Nobody Applied"
date: 2026-07-06 07:00:00 -0500
categories: [roundup]
tags: [ai-security, ransomware, supply-chain]
author_profile: true
---

Cybersecurity researchers just documented the first ransomware attack run entirely by an AI agent, not a human, from initial access to encryption. That's the headline this week, and it should change how you think about your detection stack.

Sysdig's threat research team calls the operator JadePuffer. It exploited a remote code execution flaw in Langflow, then handled reconnaissance, lateral movement, and deployment against a target database without a human touching the keyboard. I've spent years watching SOC teams tune detections around human behavior: dwell time, off-hours logins, command sequencing that looks deliberate but imperfect. An agent doesn't get tired, doesn't second-guess a pivot, and doesn't leave the fingerprints a rushed human attacker does. If your detection logic assumes human pacing, it's already behind.

Meanwhile, two vendors confirmed active exploitation of flaws they patched months ago. CISA flagged a Microsoft SharePoint RCE bug, patched in May, now under attack in the wild. Cisco confirmed the same story for a Unified Communications Manager flaw patched in June. Patch Tuesday doesn't end the risk. Attackers work off the public disclosure calendar, and they know most organizations take 60-90 days to close out "already patched" tickets in their asset inventory. That gap is the attack surface.

The FortiBleed credential campaign is following the same playbook. Researchers linked the stolen Fortinet credentials to the INC and Lynx ransomware operations, months after the initial harvesting. Attackers sat on stolen access, waited, then monetized it. Now there's a Nextcloud zero-day layered into the same campaign. Credential theft isn't a one-time event on your incident timeline. It's inventory an attacker draws down over months.

North Korean actors tied to the Contagious Interview campaign published 108 malicious packages across npm, Packagist, Go, and Chrome extensions in a run they're calling PolinRider. This isn't a one-off typosquat. It's a sustained developer-targeting operation, and if your engineering org pulls open-source dependencies without a vetting gate, you're exposed to a nation-state actor, not a script kiddie.

Last one worth your attention: a Linux kernel flaw called Bad Epoll (CVE-2026-46242) lets an unprivileged user gain root. It hits desktops, servers, and Android. Get this patched before you triage anything lower on your list this week.

Takeaway: pull your last 90 days of "resolved" CVE tickets for SharePoint, FortiOS, and Unified CM. Confirm every instance actually got the patch, not just the ticket closed. Attackers are re-checking that list. You should too.
