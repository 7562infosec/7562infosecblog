---
layout: single
title: "Cyber Roundup: When the AI Agent Is the Attacker"
date: 2026-07-20 07:00:00 -0500
categories: [roundup]
tags: [ai-security, ransomware, nation-state]
author_profile: true
---

**TL;DR:** AI tools are being weaponized as attack platforms, SonicWall's June compromise is still burning under Inc ransomware, and Russian state actors upgraded their email evasion. Audit your AI services and pull SMA 1000 logs back to June.

An autonomous AI agent broke into Hugging Face last week, and the platform that hosts the world's AI models had to admit its own attacker used the same technology it sells. Hugging Face confirmed unauthorized access to internal datasets and credentials, sourced from an agent operating without a human at the keyboard. Pair that with Google's Gemini CLI getting hijacked by a threat actor calling itself "bandcampro" to run a small botnet, and a new Go-based botnet called NadMesh scanning specifically for exposed ComfyUI, Ollama, n8n, and Langflow instances to harvest AWS keys and Kubernetes tokens. Three stories, one pattern: the AI stack you stood up fast is now both a weapon in the attacker's hand and a target on your network. I've watched teams treat AI tooling like a sandbox exempt from the access reviews everything else gets. Inventory every AI service exposed to the internet this week. If you can't name what's running and who can reach it, NadMesh already found it.

Following last week's report on SonicWall's SMA 1000 zero-days, the picture got worse on two fronts. Volexity now attributes pre-disclosure exploitation to a threat actor it tracks as UTA0533, meaning attackers were inside these appliances since June 22, three weeks before SonicWall's public advisory. The Inc ransomware operation is now chaining both flaws together for root-level access on compromised appliances. A patch released two weeks ago doesn't help if the actor already had a foothold before you knew there was a bug. If you run SMA 1000 gear, check for signs of compromise going back to June, not just apply the patch and move on.

Russian state actors are back in Ukraine's inboxes. CERT-UA attributes a new campaign to UAC-0145, a Sandworm sub-cluster tied to GRU military intelligence, using ClickFix CAPTCHA lures to get Ukrainian targets to paste malicious commands into their own Run box and install data-stealing malware. Separately, researchers found over a million phishing emails using hidden "salted" text to slip past AI-based email filters entirely. Both stories point the same direction: attackers are optimizing around the controls we just built. ClickFix defeats user judgment. Text salting defeats the AI layer meant to catch what judgment misses. Neither problem gets solved by stacking another filter on top.

Patch now: Zoom fixed a critical Windows account takeover flaw, CVE-2026-53412, CVSS 9.8, in its desktop and VDI clients. F5 shipped a fix for a critical nginx worker-crash bug, CVE-2026-42533, that can lead to remote code execution. Three malicious RubyGems packages impersonating git-credential-manager show the dependency-poisoning problem isn't slowing down, in any language.

Run your AI service inventory this week. Find what an internet scanner would find first, and close it before NadMesh's operator does.
