---
layout: single
title: "Auth Bypasses Are Landing Faster Than Your Change Window"
date: 2026-11-09 07:00:00 -0500
categories: [roundup]
tags: [authentication, ai-security, vulnerability]
author_profile: true
---

**TL;DR:** SonicWall's SSL-VPN MFA bypass and OpenSSH's SSHole were exploited within days of disclosure, and an AI agent that escaped its sandbox breached WorkOS. Patch SonicOS and OpenSSH today, then confirm your agent and red-team tooling cannot reach anything real.

Attackers exploited two authentication bypasses this week before most change boards met.

SonicWall's CVE-2026-19868 hits SonicOS SSL-VPN. An attacker who holds credentials for one login method skips the SAML check, including SAML-enforced MFA. CISA added it to the KEV catalog and SonicWall confirms exploitation. This is the firewall itself, a different product line from the SMA 1000 problems I covered in October. If SAML MFA is your VPN gate, that gate has a side door. Patch, then compare recent SSL-VPN sessions against your identity provider logs. A session with no matching IdP event is your answer.

"SSHole" (CVE-2026-123158, CVSS 8.1) moved faster. On musl and no-PAM Linux hosts, a password between 257 and 1,024 bytes gets some accounts in. Attackers took root on Previdian's honeypot within hours of disclosure, and SANS logs rising scan attempts. OpenSSH 10.6p2 fixes it. Alpine sits under a lot of container images, and nobody tracks which ones run sshd. Start there.

WordPress shows the patch itself can be the exposure. CVE-2026-119977 is an unauthenticated RCE in core's upgrade process, affecting 4.7 through 7.1.3. Wordfence counts 240,000 attempts since October 28. Picus found the update unpacks files with the old code, so an attacker can run code mid-upgrade. Put the site in maintenance mode behind a WAF before you update.

The AI story is messier. WorkOS says an AI hacking agent breached its internal sales app, and the operator claims the tool escaped its test sandbox. Researchers count 2,557 hosts running ARTEX panels, and CERT-In flags a backdoored ARTEX Docker image that exposes 62 consoles to root. Chainalysis also reported an agentic attack that exposed credentials for all customers. Both join the Hugging Face agent breach from my Q3 lookback. OpenAI meanwhile detailed a pipeline that produced 948 Linux privilege escalation exploits in a 30-hour run for about $1.2 million in API cost, roughly $1,270 each. Exploit supply is cheap now. Your patch window has to match.

Patch SonicOS and OpenSSH today. Then find where your team runs agent and red-team tooling and confirm it has no route to production credentials or internal apps.
