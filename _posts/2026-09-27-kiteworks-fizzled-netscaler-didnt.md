---
layout: single
title: "Kiteworks Fizzled, NetScaler Didn't: A Weekend Shift for Defenders"
date: 2026-09-27 07:00:00 -0500
categories: [roundup]
tags: [zero-day, vulnerability]
author_profile: true
---

**TL;DR:** The Kiteworks shutdown passed quietly with no CVE, no new build, and no confirmed attack, while two Citrix NetScaler RCE zero-days went from Reddit rumor to vendor-confirmed exploitation inside 48 hours. Upgrade NetScaler to 14.1-73.37 or 13.1-64.23 today, then hunt for compromise, because the patch won't evict anyone already inside.

Yesterday I wrote about Kiteworks telling customers to unplug on federal intel alone. The update is short. The advisory warned that a threat actor may target "some" Kiteworks systems, and as of Sunday the window has passed with no CVE, no new build, no indicators of compromise, and no confirmation an attack was even attempted. Limited scope, precautionary, done. I still stand by the call. A quiet weekend is what a correct precaution looks like from the outside.

Citrix didn't get a quiet weekend. NetScaler admins started posting on Reddit that IT suppliers, CERTs, and law enforcement were calling with the same message: shut your NetScalers down, no details. On Saturday, watchTowr confirmed two unpatched RCE flaws were being exploited in the wild. On Sunday, Citrix published bulletin CTX697096 and confirmed both.

CVE-2026-88771 lets an unauthenticated attacker run commands on any NetScaler ADC or Gateway, default configuration included. CVE-2026-88772 is a memory overflow reachable when DTLS is on, and DTLS ships enabled on VPN virtual servers. Both score 9.5. Following August's report on the NetScaler auth bypass, here's the part that stings: appliances you patched for CVE-2026-19490 last month are still exposed. Those builds predate this fix.

Two vendors, two shutdown orders, one weekend. Kiteworks got ahead of an attack that never showed. Citrix found out from incidents already inside customer networks. I've run enough weekend bridges to know which one burns out a team. If your shop heard about NetScaler on Reddit before your vendor or your intel feed told you, fix that pipeline this week.

Upgrade NetScaler ADC and Gateway to 14.1-73.37 or 13.1-64.23 now. On 13.1, run `show ns variable` first; if it returns anything, go to 13.1-64.24 to dodge a reboot loop. Confirm your IdP signs SAML assertions, since the new builds reject unsigned ones. Then treat every exposed appliance as compromised until you prove otherwise: ship logs to your SIEM, request Citrix's IOCs, and check file integrity. If you powered it down this weekend, patch it before it comes back online.
