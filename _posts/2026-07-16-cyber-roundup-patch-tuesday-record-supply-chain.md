---
layout: single
title: "Cyber Roundup: A Patch Tuesday Record and a Supply Chain That Won't Quit"
date: 2026-07-16 07:00:00 -0500
categories: [roundup]
tags: [patch-tuesday, supply-chain, identity]
author_profile: true
---

Microsoft shipped 622 CVEs this Patch Tuesday, the largest release in the company's history and more than triple June's count. Attackers were already exploiting two of those bugs before the fixes landed. If your patch cadence still runs on a monthly cycle with a two-week rollout window, this is the month that breaks it. Triage the two zero-days first, then work through the rest in risk order, not alphabetical order.

SonicWall and CISA gave you more reasons to move fast. SonicWall confirmed active exploitation of two SMA 1000 zero-days, one an SSRF flaw scoring a perfect 10.0 that lets an unauthenticated attacker reach admin commands. CISA separately added actively exploited SharePoint flaws to its Known Exploited Vulnerabilities catalog, and Progress confirmed the zero-day behind last week's ShareFile Storage Zone shutdown. Three vendors, three confirmed zero-days, in the same week. I've seen teams treat vendor advisories as background noise until an auditor asks about them. This week that habit gets someone popped.

**Supply chain, again**

Four compromised packages in the @asyncapi npm namespace delivered a multi-stage botnet loader, and a poisoned release of jscrambler dropped a native infostealer through a preinstall hook — one binary each for Windows, macOS, and Linux. Socket caught the jscrambler package six minutes after publish. Six minutes is fast detection and still not fast enough if your build pipeline pulls packages automatically on release. Pin your dependencies. Review preinstall and postinstall scripts before they run in CI, not after.

**The identity angle**

Microsoft mapped a year of ShinyHunters activity against Salesforce environments, and none of it required exploiting Salesforce itself. The way in was OAuth trust: connected apps and third-party integrations nobody revisited after the initial approval. Separately, researchers flagged OAuth client ID spoofing being used to validate stolen Entra ID credentials without generating a sign-in event — which means alerting on failed logins misses it entirely.

Patch what's exploited, audit what's connected, and stop treating OAuth grants as a set-and-forget control. Pull your list of connected apps this week and revoke what nobody remembers approving.
