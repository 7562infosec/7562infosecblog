---
layout: single
title: "Cyber Roundup: AI Coding Agents Are the New Attack Surface"
date: 2026-07-09 07:00:00 -0500
categories: [roundup]
tags: [ai-security, vulnerability, social-engineering]
author_profile: true
---

Three research teams published attacks against AI coding agents this week, and each one lands on the same weakness: these agents assume good faith and get hit anyway.

Wiz found symlink flaws in six coding assistants, including Claude Code, Cursor, Augment, and Windsurf. An agent asks permission to edit one harmless file. The write lands on a sensitive one instead, and a booby-trapped repo takes control of the developer's machine. The AI Now Institute published a separate proof-of-concept called "Friendly Fire," where a security-scanning agent runs the exploit it was asked to catch, because it operates in autonomous mode and approves its own actions. A third team detailed "HalluSquatting": AI assistants hallucinate package names in predictable patterns, so an attacker registers those names first and waits for an agent to fetch the trap and install botnet malware.

I've watched teams grant these agents broad file and shell access because the workflow is faster that way. These three findings break the same trust boundary in three different ways. The agent believes what it fetches and executes what it's told, with no way to tell a real dependency from a planted one. Sophos added a fourth data point: AI coding agents are tripping endpoint detection rules built for human intruders, because credential decryption and system enumeration look the same whether a person or an agent does it. The detection layer hasn't caught up to this class of actor.

If your org runs AI coding agents with write access to production repos or systems holding credentials, sandbox them the way you'd sandbox an unvetted contractor. Least privilege applies to agents too.

Second theme: two max-severity vulnerabilities, both under active exploitation. Ubiquiti patched a set of UniFi flaws across Connect, Talk, Access, Protect, and OS, including CVE-2026-50746, an improper access control bug that scores a full 10.0 and allows privilege escalation and arbitrary command execution. Adobe's ColdFusion CVE-2026-48282 is already being exploited according to KEVIntel. If you run either product, patch this week.

Third: attackers are still getting in through people. A phishing campaign impersonating more than 30 brands in fake job interviews is harvesting Google credentials from marketing staff. Separately, a group is calling employees on Microsoft Teams, posing as IT support, and talking them through installing EtherRAT malware during the call. Both attacks borrow trust from a process employees already follow. MFA doesn't stop someone who hands over access willingly because the voice on the phone sounded like IT.

Patch the two CVEs above before Friday. Sandbox your AI coding agents like you would a new contractor. And tell your help desk to remind users, again, that IT never asks you to install something mid-call.
