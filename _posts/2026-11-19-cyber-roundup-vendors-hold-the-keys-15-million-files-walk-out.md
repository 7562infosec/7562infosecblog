---
layout: single
title: "Cyber Roundup: Vendors Hold the Keys, and 15 Million Files Walk Out the Door"
date: 2026-11-19 07:00:00 -0500
categories: [roundup]
tags: [supply-chain, data-breach, credential-theft]
author_profile: true
---

**TL;DR:** Optimizely, a poisoned Microsoft PyPI package and a leaked Fireworks AI key all reached victims through a vendor, while 15 million Deutsche Bank documents left the building without a DLP alert stopping them. By Friday, inventory every third-party script and outside API key in production, and test whether your DLP catches a bulk export.

Your data is leaving through doors you don't watch. This week it went out through vendors, and in one case through the front door in bulk.

Start with Optimizely. On November 16, an attacker abused Optimizely Web Experimentation to push malicious JavaScript to visitors of at least 178 organizations, including CNN, BBC, Zoom and Equifax. Report URI found card skimming code, crypto payment redirection and iOS exploit kits in the payload. If your CSP allowlisted Optimizely's domain, it waved this code through.

Next, Microsoft's agent-framework package on PyPI. Versions 1.26.1 and 1.26.2 shipped on November 17 with a credential stealer that fires every time Python starts and goes after Azure, Azure DevOps and GitHub Actions secrets. If a build agent pulled either version, treat every secret on that runner as burned.

The AI supply chain keeps leaking keys too. Cursor traced its trojanized Claude Code extension to an access key it had issued to Fireworks AI, which Fireworks exposed. Uber is notifying nearly 150,000 drivers whose data left through the same Fireworks breach. Amazon caught AI agents hunting exposed LiteLLM and Dify instances for stored model keys, and leaked Docker Hub cloud keys get stolen in eight seconds. A quarterly rotation policy is no defense against that.

Then there's Deutsche Bank. Two whistleblowers handed more than 15 million internal documents, including about 9 million emails, to journalists who published "Inside Deutsche Bank" on November 17. The bank doesn't dispute the files, and its shares fell as much as 6% that day. The whistleblowers say they acted in the public interest, and the reporting covers Epstein payments, Russia business and Trump-linked transactions. Set the motive aside. This is a DLP failure. Nine million emails should never leave a bank that says it spent €7 billion on controls between 2019 and 2025. Bulk export alerts, egress monitoring and UEBA exist for this. Now swap the actor. A ransomware affiliate or a paid insider pulls the same export, and it lands on a leak site with a countdown timer instead of the Financial Times. Your DLP can't read intent. It has to stop the volume.

The patch queue got heavier as well. Java4Shell (CVE-2026-114938) gives unauthenticated RCE on Jira, Jenkins, Keycloak and others running on AVX-512 VBMI hardware, and CISA wants it patched now. Apache Roller (CVE-2026-129448) and Perforce Puppet (CVE-2026-115731, now in KEV) are both under active exploitation. Own the Puppet server and you own every node it manages.

Your action item: by Friday, list every third-party script on your customer-facing pages and every API key you've issued to an outside provider, and rotate the keys. Then have a standard user account export 10,000 internal files and see whether anyone gets paged. Patch Puppet and Java before the weekend.
