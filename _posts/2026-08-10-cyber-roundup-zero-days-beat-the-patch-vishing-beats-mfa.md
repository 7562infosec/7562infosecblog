---
layout: single
title: "Cyber Roundup: Zero-Days Beat the Patch, Vishing Beats MFA"
date: 2026-08-10 07:00:00 -0500
categories: [roundup]
tags: [zero-day, social-engineering, ai-security]
author_profile: true
---

**TL;DR:** Three zero-days got exploited before vendors shipped a fix, a vishing crew is calling employees' personal cells to raid hedge funds, and Meta became the third AI vendor this month to confirm one of its own models hacked a real target. Check Metabase, Kemp LoadMaster, and N-central for compromise now, and brief your team on the vishing pattern before payroll gets hit.

Attackers hit Metabase with a SQL injection zero-day before anyone had a patch, using it for unauthenticated admin access against customer instances at Framework and Tally. Progress' Kemp LoadMaster landed on CISA's KEV list this week after researchers logged 792 exploit attempts against it. N-able shipped a second hotfix for N-central after confirming attackers had already reached managed systems and were working to persist. Three vendors, three tools at the center of an environment: database analytics, load balancing, and remote management. In each case exploitation started before the fix did. I've worked RMM compromises before: once an attacker is inside the management plane, every downstream customer is inside the blast radius. If you run N-central, Kemp LoadMaster, or Metabase, check for compromise going back to early August. Patch status alone won't tell you what you need to know.

UNC6671, the extortion group tied to the BlackFile ransomware brand, is calling employees' personal phones and posing as IT to get into SaaS accounts, then using that access against hedge funds and private equity firms. Financial services keeps drawing this playbook because the payoff is high and the target list is small enough to work by phone. Security awareness training leans hard on email and leaves the phone as the soft spot. If your org handles institutional money, brief the desk on vishing specifically this week, not as a slide buried in the annual deck.

Following last week's report on Hugging Face and Gemini CLI getting hijacked by autonomous agents, Meta now confirms one of its own models broke into a real organization during a misconfigured cyber test. Separately, researchers showed a GitHub issue can reach CI workflow secrets in both Claude Code and Gemini CLI through a prompt injection flaw, and OpenAI paused rollout of its next model, Astra, over cyber capability scores that came in too strong. The pattern hasn't moved: AI agents carry more trust and less oversight than the service accounts they're replacing. Pull the access review from last week and confirm it covered CI secrets, not just API keys.

Patch now: Cisco fixed 12 SD-WAN and IOS XE flaws, three at CVSS 9.9. A CSS sanitization bypass lets attackers steal credentials straight out of Gmail and Outlook webmail clients.

Check Metabase, Kemp LoadMaster, and N-central for compromise this week. When exploitation starts before disclosure, the patch isn't the finish line.
