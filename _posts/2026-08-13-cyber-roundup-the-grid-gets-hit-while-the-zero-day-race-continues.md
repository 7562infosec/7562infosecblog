---
layout: single
title: "Cyber Roundup: The Grid Gets Hit While the Zero-Day Race Continues"
date: 2026-08-13 07:00:00 -0500
categories: [roundup]
tags: [zero-day, nation-state, vulnerability]
author_profile: true
---

**TL;DR:** Lazarus burned a Windows zero-day against defense contractors before Microsoft's 398-bug Patch Tuesday closed it, and attackers took down a Polish power plant turbine over a private cellular link while water utilities across a dozen US states report the same pattern. Patch CVE-2026-68820 this week and inventory every cellular or VPN path into your OT environment.

Lazarus Group ran CVE-2026-68820, a privilege escalation flaw in the Windows afd.sys driver, against defense and aerospace firms in France, Germany, Brazil, and India before Microsoft shipped a fix. Check Point tied the activity to Operation Dream Job, the North Korean group's long-running fake-recruiter campaign. Microsoft's August Patch Tuesday landed the same day at 398 CVEs, 42 critical, and this flaw was the only one confirmed under active exploitation. The pattern is routine now: a nation-state actor finds the bug, uses it quietly, and the vendor confirms it once the patch ships. If you're in defense, aerospace, or supply either, treat this as an assume-breach event and hunt for the backdoor Check Point described, not just the patch.

Two operational technology attacks landed the same week, and neither needed a sophisticated exploit. Attackers shut down a steam turbine and a water treatment system at a Polish combined heat and power plant supplying roughly 50,000 residents, getting in through the private cellular network the grid operator uses to reach remote equipment. Separately, the water-system intrusions active across a dozen US states are still spreading, with Iran suspected, hitting internet-exposed PLCs that should never have been reachable at all. I've seen this pattern before: OT failures are rarely about sophistication. They're about a remote-access path someone forgot existed. If your utility or plant uses cellular modems or VPN gateways to reach field equipment, inventory every one of them this week and confirm who can authenticate to them.

On the patch list: Cisco confirmed active exploitation of CVE-2026-20349, a DoS flaw in ASA and FTD software that crashes firewalls remotely. VMware vCenter's CVE-2026-59310, a directory traversal bug scoring 9.8, is being exploited for persistent access. And Gunra ransomware is chaining old Fortinet FortiOS and FortiProxy flaws to bypass MFA and get into critical infrastructure networks, per a joint South Korea-US advisory. None of these are novel techniques. They're unpatched appliances doing what unpatched appliances do.

Patch CVE-2026-68820 and CVE-2026-20349 this week if you run the affected Windows or Cisco gear. Then pull the list of every cellular and VPN path into your OT environment and confirm each one is still supposed to be there.
