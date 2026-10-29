---
layout: single
title: "PHP2Shell Is Our Log4j, and the Long Tail Has Started"
date: 2026-10-29 07:00:00 -0500
categories: [roundup]
tags: [zero-day, vulnerability, china]
author_profile: true
---

**TL;DR:** PHP2Shell is one week old, exploitation is confirmed, and the cleanup will run for weeks, as Log4j did. Patch PHP to 8.5.12, 8.4.27, 8.3.36 or 8.2.35, pull every admin interface off the internet, and track each app owner's verified patch date.

This is my third post on PHP2Shell, and the last one paired it with the Brotli flaw. The PHP crisis is not over, and we are one week in. Disclosure was October 21. CISA added two PHP2Shell flaws, both CVSS 9.2, to the KEV catalog on October 27 for unauthenticated remote code execution. Palo Alto Networks reports attacks on internet-exposed management interfaces. A suspected China-nexus operator chained PHP2Shell with a kernel privilege escalation and took root on 25 servers inside a US government-affiliated network.

In my current role, my team works with app owners all day, patching and hunting for gaps. One week in, we are still finding systems. We will keep at it for weeks. We keep thinking back to Log4j. That cleanup took longer than anyone planned, and we still find remnants today. Expect PHP and Brotli to follow the same curve.

Attribution is still moving. Unit 42 retracted its claim that PHP2Shell hit a European government agency. Treat the victim lists as drafts and the patch list as final.

The Brotli decoder flaw, CVE-2026-111497, adds to the pile. CISA confirmed exploitation of the Node.js RCE, and the same memory-corruption bug sits inside Bun, .NET, Python Brotli packages, and Envoy. PHP shipped two Windows rebuilds in five days to fix its bundled copy. Your SBOM lists the library you imported. It does not list the copy baked into your runtime.

I've seen this pattern in financial services more than once. The patch report shows green while the firewall, VPN, or load balancer admin page sits on a public IP. Those interfaces run PHP. Attackers know it.

Do three things today. Patch PHP and every Brotli consumer. Find every management interface with a public route and close it. Build a tracker with each app owner and a verified patch date, because the long tail is where you get hit.
