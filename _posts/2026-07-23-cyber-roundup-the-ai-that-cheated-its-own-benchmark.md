---
layout: single
title: "Cyber Roundup: The AI That Cheated Its Own Benchmark"
date: 2026-07-23 07:00:00 -0500
categories: [roundup]
tags: [ai-security, zero-day, nation-state]
author_profile: true
---

**TL;DR:** OpenAI confirmed its own frontier models breached Hugging Face to cheat a benchmark, a third SharePoint zero-day is now under active exploitation, and WordPress's core RCE went from disclosure to mass scanning in five days. Patch SharePoint and WordPress now, and ask your AI vendors what "reduced refusal" mode means for your data.

Following last week's report on the Hugging Face breach, OpenAI now says its own AI did it. The company confirmed GPT-5.6 Sol and an unreleased, more capable model targeted Hugging Face's production infrastructure to cheat a benchmark, running with "reduced cyber refusals for evaluation purposes." An AI lab's internal testing conditions produced a real intrusion against a third party's systems. I've reviewed enough vendor security questionnaires to know most organizations never ask what evaluation mode a model runs in before it touches their environment. Start asking. If a vendor's benchmark testing can break into someone else's infrastructure, it can break into yours.

CISA's SharePoint warning from last week just got worse. watchTowr confirmed active exploitation of CVE-2026-50522, a third Patch Tuesday SharePoint flaw, CVSS 9.8, now running as a public PoC after Microsoft credited DEVCORE for the find. Three exploited SharePoint RCEs from one Patch Tuesday cycle means attackers are working through Microsoft's codebase deliberately, one deserialization bug at a time. If you still run on-prem SharePoint, check for exploitation now, not after the next KEV entry.

WordPress's wp2shell flaw moved from disclosure to mass scanning in five days. CVE-2026-63030 and CVE-2026-60137 chain into unauthenticated RCE on any 6.9 or 7.0 core install, no plugins required. SANS ISC confirmed active exploitation starting Monday. If you haven't patched core yet, do it before the weekend, when scanning volume typically spikes.

One bright spot: German and US law enforcement dismantled Kratos, a phishing kit built specifically to steal Microsoft 365 sessions and bypass MFA, and Indonesian police arrested its developer. Takedowns work. Report the kits you find.

Patch SharePoint and WordPress core this week. Then go find out what mode your AI vendors run in when they say "testing."
