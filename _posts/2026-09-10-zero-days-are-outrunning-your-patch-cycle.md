---
layout: single
title: "Zero-Days Are Outrunning Your Patch Cycle"
date: 2026-09-10 07:00:00 -0500
categories: [roundup]
tags: [patch-tuesday, zero-day, nation-state]
author_profile: true
---

**TL;DR:** Microsoft's record 973-CVE Patch Tuesday landed next to two already-exploited zero-days and a fileless rootkit inside F5 BIG-IP APM devices right now. Patch the Cisco FMC and Chrome zero-days today, then check BIG-IP APM process memory instead of trusting a clean patch report.

Microsoft's September Patch Tuesday shipped a record 973 CVEs, blowing past July's previous high of 622 in two months. Two of those bugs were already under active exploitation before the fixes landed, and neither is the only zero-day burning right now. Cisco confirmed a maximum-severity authentication bypass in Secure Firewall Management Center, tracked as CVE-2026-20079, is being exploited in live attacks eight months after disclosure. Google patched its seventh actively-exploited Chrome zero-day of the year. And within hours of Microsoft's own patches landing, a researcher published "ShieldCrash," a Defender exploit that grants full SYSTEM privileges on machines running the brand-new update. I've seen security teams treat Patch Tuesday as a monthly checkbox: apply, verify, move on. That cadence assumed attackers waited for you. They don't anymore, and neither does the researcher community publishing exploits same-day.

Attackers already inside are the bigger problem. A Linux rootkit is hitting F5 BIG-IP APM devices, intercepting PHP file loads and injecting a fileless web shell straight into memory. Nothing touches disk, so file-integrity monitoring won't catch it. If you run BIG-IP APM, check process memory and network egress, not just file hashes.

Following July's report on ShinyHunters exploiting OAuth trust in Salesforce environments, the group has a new confirmed victim. AdaptHealth disclosed that a July breach tied to ShinyHunters exposed 4.1 million people's data. The access method hasn't changed. The victim count keeps climbing because nobody revisited what OAuth grants were still live.

US intelligence agencies confirmed six Chinese AI companies ran industrial-scale distillation attacks against American frontier models going back to late 2024, systematically querying US models to train competing systems on the extracted outputs. Any API you expose to a frontier model is also a data-exfiltration channel for whoever queries it enough times.

Patch the Cisco FMC and Chrome zero-days today, both confirmed under active exploitation. Then pull your BIG-IP APM process list and look for anything that doesn't belong in memory. A patch report with no findings doesn't mean the box is clean.
