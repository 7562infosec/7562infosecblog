---
layout: single
title: "Cyber Roundup: A Perfect-10 Zero-Day and the RMM Meltdown"
date: 2026-09-08 07:00:00 -0500
categories: [roundup]
tags: [zero-day, credential-theft, ai-security]
author_profile: true
---

**TL;DR:** Adobe Commerce's StyleSmuggler zero-day, N-able's fourth N-central hotfix in five weeks, and active MikroTik router hijacking all say the same thing: edge infrastructure keeps losing before patches land. Patch both now, audit MikroTik for accounts you didn't create, and check what your AI coding agents are installing from unverified llms.txt entries.

Adobe Commerce and Magento got hit with a perfect 10 this week. Sansec discovered StyleSmuggler, tracked as CVE-2026-75650, under active exploitation since September 4, dropping a Rust backdoor and a PHP web shell on unpatched stores. Adobe shipped the fix Monday. If you run Magento Open Source or Adobe Commerce, patch now and pull logs back to September 4, not just forward from today. A backdoor planted before the patch survives the patch.

RMM and edge infrastructure took hits from three directions this week. N-able issued its fourth N-central hotfix in five weeks for an unauthenticated RCE flaw, and every on-premises build below 2026.3.1.14 needs it, including servers patched with hotfix 3 a day earlier. N-able's incident notice says the flaw is being exploited; its release notes call that unconfirmed. When a vendor can't agree with itself on exploitation status, patch like it's true. Separately, CERT Polska is warning that attackers are hijacking MikroTik routers through internet-exposed SSH with no authentication required, adding new accounts to keep access after victims patch. I've watched teams treat network appliances as set-and-forget hardware. Attackers treat them as permanent real estate. If you run N-central or MikroTik gear facing the internet, check for accounts you didn't create before you trust a patch to fix things.

On the credential theft side, a phishing-as-a-service kit called BigBear 2.0 intercepted authenticated Microsoft 365 sessions at 258 organizations, stealing more than 5,000 credentials and defeating MFA along the way. This is Evilginx2 in a new coat. MFA stops password replay. It does nothing against a proxy sitting between the user and Microsoft, capturing the session token after the user does everything right.

Bruce Schneier flagged research worth reading in full. A team scanned over 6,200 corporate domains and found AI coding agents, including Claude, Codex, and Nous Research's Hermes, installing packages and reaching out to domains listed in llms.txt files that were never actually registered. Researchers claimed a handful of those names, and within an hour got a phone-home from a Fortune 500 network. The agents treated vendor documentation as ground truth. Nobody checked whether the packages existed first.

Patch Magento and N-central this week. Pull your MikroTik account list and look for anything you didn't add. And if your AI agents read documentation and install what it tells them to, that's a supply chain control you don't have yet.

