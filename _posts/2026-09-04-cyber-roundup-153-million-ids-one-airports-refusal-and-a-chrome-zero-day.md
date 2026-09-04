---
layout: single
title: "Cyber Roundup: 153 Million IDs, One Airport's Refusal, and a Chrome Zero-Day"
date: 2026-09-04 07:00:00 -0500
categories: [roundup]
tags: [data-breach, zero-day, vulnerability]
author_profile: true
---

**TL;DR:** Manchester Airports Group's ransom refusal cost 8.8 million people their data, a broker breach put 153 million driver's license images on the dark web, and Chrome patched its sixth actively-exploited zero-day of the year. Patch Chrome today, and find out who on your vendor list is holding scanned government IDs on your behalf.

Sorry for the lapse in posting. I was out of town on a trip. My company has a mandatory time away requirement which means I have 2 weeks of no phone buzzing for alerts or escalations. We took a nice trip up to the Northwest. Now back to regularly scheduled programming!

Manchester Airports Group refused to pay a ransom, and the attacker published anyway. Roughly 550GB of data covering 8.8 million people is now public, and the group says it got in through exposed admin keys, not some novel zero-day. I've told clients for years that the ransom-refusal decision isn't really about the ransom. It's an information-exposure decision, and MAG's board just made that call in public. If your incident response plan treats "we didn't pay" as the end of the story, it isn't. Build your breach notification and PR response around the assumption that a refusal gets your data dumped, because that's the operator's next move now.

Separately, criminals are offering scans of 153 million US and Canadian driver's licenses on a new dark web platform, most likely sourced from IDScan.net. Krebs and several other outlets independently confirmed the FBI is investigating. Driver's license images aren't passwords. You can't rotate them. If your org verifies identity using a photo of a license, that control just got weaker for everyone, not just people caught in this breach. Treat license-photo verification as a secondary factor at best, never a primary one.

Google shipped its sixth Chrome zero-day patch of the year: CVE-2026-85046, a type confusion bug in the V8 engine already under active exploitation. Six zero-days in a year that isn't over means Chrome's exploit market hasn't slowed down at all. Push the update today. Don't wait for your normal browser patch cycle to catch up.

Quick hits worth your patch queue: CISA added seven actively exploited flaws to its KEV catalog, with attackers chaining reverse shells and crypto miners through them. Cisco patched critical Nexus 9000 switch flaws allowing unauthenticated root-level code execution, and separately disclosed unpatched S/MIME flaws in Secure Email with no fix yet. JFrog Artifactory customers got hit by an auth-bypass bug exploited to forge admin tokens within days of disclosure, the same pattern we keep seeing: exploited before most teams finish reading the advisory.

Patch Chrome today. Then pull your vendor list and find out who's holding scanned government IDs on your behalf, because MAG and IDScan.net just showed you what happens when that data gets loose.

