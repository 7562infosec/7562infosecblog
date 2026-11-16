---
layout: single
title: "Cyber Roundup: The Tools You Trust Opened the Door"
date: 2026-11-16 07:00:00 -0500
categories: [roundup]
tags: [supply-chain, ai-security, north-korea]
author_profile: true
---

**TL;DR:** A leaked vendor key shipped a trojanized Claude Code extension, N-central fell on fully patched servers, and PHP2Shell is now wiping ESXi through Check Point gateways. Rotate every AI and RMM credential a third party holds for you, and pull Check Point logs back to October 30.

The tools you bought to manage risk carried most of the risk this week.

**Cursor pays for Fireworks' breach.** Following last week's report on the Fireworks AI compromise, Cursor confirmed the downstream damage. An access key Cursor issued to Fireworks leaked in that breach. The attacker used it to copy API credentials and archived source code, then pushed a trojanized Claude Code extension through Cursor's marketplace. Amazon's threat intel team adds the bigger picture. Its decoy servers caught AI agents scanning exposed LiteLLM and Dify instances for provider keys, then running models on the victims' bills. The FBI's new FLASH on ARTEX says some ARTEX-driven intrusions reached privileged access in under three hours. Your developers' API keys are a primary target now, and machines are doing the hunting.

**N-central falls on patched servers.** Last week the N-central PoC was a warning. Now it is an incident. Attackers exploited 4EverAble2Shell within hours of the public PoC, and 19 of the first 21 compromised servers ran the latest hotfix. N-able is restricting features while it remediates. Blackpoint also documented SCKit, a worm-like toolkit that rides ScreenConnect support sessions from customer endpoints back to MSP technicians. I've worked incidents where the RMM agent was the persistence mechanism, and nobody flagged it because it was supposed to be there. If your MSP runs N-central or ScreenConnect, ask them today what they've isolated.

**PHP2Shell reaches Check Point.** We called PHP2Shell our Log4j in October. The long tail now includes unpatched Check Point gateways. Attackers chained it with a Gaia OS privilege escalation (CVE-2026-123039) to get root, dropped the TSGA backdoor, and wiped VMware ESXi hosts. Activity began October 30 against Israeli organizations. CISA added the Gaia flaw to KEV on November 13 with a three-day deadline. That deadline is today.

**North Korea moves to deepfake video.** The FBI tied a North Korea-linked campaign it calls FaceStealer to more than $400 million in crypto theft over 18 months, run through deepfake video calls. Video verification became the control many finance teams adopted after voice cloning took off. That control is broken. A callback to a known number plus a second human approver still holds.

**SMS codes are readable inside the carrier.** Enea attributed SilentAir to a state-level group operating inside Asian mobile operators, intercepting calls and texts, mostly targeting Taiwan. If SMS codes still protect privileged access anywhere in your environment, that is a finding, not a control.

**Action item:** Inventory every API key and RMM credential a third party holds on your behalf and rotate them this week. Then pull Check Point gateway logs back to October 30 and hunt for TSGA. If a vendor can't tell you which of your keys they hold, you have your next audit finding. 


