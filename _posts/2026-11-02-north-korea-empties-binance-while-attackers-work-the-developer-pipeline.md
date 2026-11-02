---
layout: single
title: "North Korea Empties Binance While Attackers Work the Developer Pipeline"
date: 2026-11-02 07:00:00 -0500
categories: [roundup]
tags: [north-korea, developer-tooling, supply-chain]
author_profile: true
---

**TL;DR:** North Korea drained about $6.3 billion from Binance, and attackers hit developer infrastructure the same week through a trojanized Claude Code extension and a CVSS 10.0 GitLab flaw. Patch GitLab, and pull every IDE extension on developer machines against an approved list.

North Korea's TraderTraitor took about $6.3 billion from Binance on October 29. The FBI confirmed the attribution on November 1, and Binance froze nearly $3 billion on-chain. It is the largest crypto heist on record. Following our September coverage of the Bitget theft, the pattern holds: DPRK crews target custody and signing workflows, then move funds across chains faster than freezes land. If your organization holds digital assets, test your freeze and recovery playbook this week.

The lesson most of us can use came from developer tooling. Cursor's marketplace hosted trojanized versions 2.1.312 and 2.1.313 of the Claude Code extension under the legitimate publisher identity. They tried to install a persistent SSH backdoor. The listing stayed up for about 11 hours on October 29 and reached up to 5,000 developers. Symantec also found an unauthorized relay at 12 organizations that installs the official Codex and Claude Code CLIs and rewrites their settings to turn off sandboxing. Developers trust publisher names. Attackers know that.

GitLab shows the same weakness from the server side. CISA added CVE-2026-97229, a CVSS 10.0 remote code execution flaw in GitLab CE and EE, to KEV on October 30. Alpine Linux saw an attacker try it on October 20 and 21, a week after the fix shipped. Alpine found no evidence the attack worked, rebuilt its GitLab server, and reset every password. A source host holds deploy keys and secrets, so a compromised GitLab hands over production. One week is your patch window now. Ivanti Connect Secure (CVE-2026-111357) and Drupal Commerce Core (CVE-2026-118539) are under active exploitation too.

AI is speeding up the attackers' side. Chainalysis disclosed that an actor using agentic offensive techniques reached internal tools and pulled customer names, emails, user IDs and roles. CrowdStrike says the China-based Vapor Panda group used a Go-based AI pentest framework called ARTEX against more than 200 organizations. Detection that relies on a human noticing slow, noisy recon will miss this.

This week: patch GitLab and check logs back to October 20 for unauthenticated requests. Inventory IDE extensions across developer endpoints, flag Claude Code 2.1.312 and 2.1.313, and check `authorized_keys` on any host where they ran. Then enforce an extension allowlist.
