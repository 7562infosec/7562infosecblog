---
layout: single
title: "Cyber Roundup: Your Vendors Are Holding Your Keys"
date: 2026-11-12 07:00:00 -0500
categories: [roundup]
tags: [supply-chain, cloud-security, vulnerability]
author_profile: true
---

**TL;DR:** Railway, Fireworks AI and Qubole lost customer secrets this week, Apache shipped a fix for a 9.8 pre-auth HTTP/2 bug, and Outlook has a zero-day under attack. Rotate every credential your vendors hold, get httpd to 2.4.71 or turn off h2, and push the Outlook fix before the weekend.

Three platform vendors leaked their customers' secrets in the same 96 hours. If a vendor stores your API keys, those keys are only as safe as that vendor's worst day.

**Railway, Fireworks AI, Qubole**

Railway confirmed attackers reached the systems that store customer environment variables. They burned about $740,000 in fraudulent AI usage on stolen keys. Railway puts the potential exposure at up to 100,000 workspaces and is telling every customer to rotate.

Fireworks AI disclosed that attackers reached its development machines after breaching a third-party cloud provider. Notion felt it downstream: chat transcripts from under 1% of its workspaces leaked through Fireworks. Notion says its own systems were never touched. The customers whose transcripts left the building don't care.

A threat actor also used IAM credentials from Qubole's AWS account to exfiltrate data from several customers' AWS environments. Those customers granted Qubole cross-account trust so the product would work. The attacker inherited that trust.

I've worked this incident from the customer side. The first question is always "what did we give them?" and nobody has the answer written down. The vendor questionnaire asked about encryption at rest. It never asked which of our secrets they hold or how fast we can revoke them.

**Apache HTTP/2 bug**

Apache released httpd 2.4.71 on November 11 to fix CVE-2026-119618, a race condition in mod_http2. An unauthenticated attacker can trigger it on any 2.4.55 through 2.4.70 server with HTTP/2 enabled. Red Hat scores it 9.8. Nobody has confirmed exploitation yet, but two research teams found it independently. When two teams find the same bug, assume a third team found it and isn't reporting it. Standalone mod_h2 builds have no fixed release, so those servers need h2 and h2c pulled from the Protocols directive today.

**Outlook zero-day leads Patch Tuesday**

Microsoft fixed more than a thousand flaws. Attackers are already using CVE-2026-124194 in Outlook, which leaks NTLMv2 hashes. Stolen hashes feed relay attacks and offline cracking, so treat this as a credential exposure.

**Management planes keep falling**

Attackers are exploiting an authentication bypass in Xen Orchestra to take admin control of XCP-ng hosts. Barracuda confirmed exploitation of two Email Security Gateway flaws that hand out root. N-able is warning about attacks on N-central RMM servers after proof-of-concept code went public. Each of these consoles controls hundreds of downstream systems. Lose the console and you lose the fleet.

**Action item:** List every vendor that holds your credentials or a cross-account role. Rotate Railway secrets today and search CloudTrail for Qubole role assumptions going back 30 days. Get every internet-facing httpd to 2.4.71 or set `Protocols http/1.1` until you can. Push the Outlook fix before the weekend, then block outbound SMB at the perimeter.
