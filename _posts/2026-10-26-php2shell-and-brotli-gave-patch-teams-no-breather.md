---
layout: single
title: "PHP2Shell and Brotli Gave Patch Teams No Breather"
date: 2026-10-26 07:00:00 -0500
categories: [roundup]
tags: [zero-day, supply-chain, vulnerability]
author_profile: true
---

**TL;DR:** PHP2Shell was exploited four days before its patch, and Brotli CVE-2026-111497 hit every runtime that bundles the decoder. Patch PHP and Node, then inventory every product that ships its own Brotli, and restart processes and rebuild images.

PHP2Shell was under attack four days before a patch existed. Amazon's MadPot honeypot logged an exploit attempt on October 17. PHP shipped emergency fixes on October 21 in versions 8.5.12, 8.4.27, 8.3.36, and 8.2.35. Two days later, PHP disclosed CVE-2026-115560, another RCE with no fix, and told admins to disable a feature.

Attempts now reach millions of hosts. Operators of a Mirai variant called Potassium joined in, and ASLR bypass exploits are circulating. No one has confirmed a mass compromise. Unit 42 retracted its claim that PHP2Shell hit a European government agency, so keep attribution out of your incident notes.

Node.js gave nobody a breather. It shipped 22.23.4, 24.22.1, and 26.12.1 on October 21 for CVE-2026-111497, an out-of-bounds write in the Brotli decoder. Every runtime bundles its own copy, so one patch fixes one product. Bun 1.4.3 and earlier, .NET 8 through 10, Envoy, Istio, and the Python Brotli and brotlicffi packages all need separate updates. Apache Arrow has no fix yet. Imperva ran attacker code on an unmodified Node 24.22.0 build through a fetched response and an Express request body. It took several tries, and the exploit is unreleased. CISA lists no exploitation.

Exposure requires decoding untrusted Brotli, which fetch() and Express 5 body parsers do. Restart processes and rebuild container images, because a running process keeps the old decoder. Node 20 and earlier get no fix. If you cannot update today, reject inbound Content-Encoding: br and uninstall the Python packages. Removing br from Accept-Encoding does nothing, since servers can send Brotli anyway.

I've watched teams hold a critical fix for a change window while scanners worked through their address space. A patch SLA measured in days assumes you get days.

Speed is the pattern. Microsoft tied the ConnectWise Cloud Backup compromise to Storm-0940, which used the ARTEX AI pentest framework against more than 2,200 tenants. INC and The Gentlemen affiliates ran an AI-driven kill chain called Phantom. Following the Q3 lookback's mention of LiteLLM, it got hit again: a master key committed to a public repo in May let attackers push a malicious 1.107.0 to PyPI and Docker Hub on October 21. Railway told customers to rotate environment variables the next day.

This week: search PHP logs back to October 17, inventory every product that bundles Brotli, and rotate any secret LiteLLM or Railway touched.
