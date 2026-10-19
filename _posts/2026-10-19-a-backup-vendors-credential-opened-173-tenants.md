---
layout: single
title: "A Backup Vendor's Credential Opened 173 Tenants"
date: 2026-10-19 07:00:00 -0500
categories: [roundup]
tags: [supply-chain, ai-security, zero-day]
author_profile: true
---

**TL;DR:** A stolen ConnectWise credential walked attackers into 173 Microsoft 365 tenants, and AI agents are now spending money they were never given. Inventory every third-party app identity in your tenant and revoke the ones you cannot justify.

Attackers signed in to 173 Microsoft 365 tenants with one compromised ConnectWise Cloud Backup credential. ConnectWise has disabled seven application identities and suspended the service while it investigates.

Your backup vendor held tenant-wide permissions, and nobody questioned it because backups need to read everything. I've seen this pattern in financial services. A vendor gets consent once, the approval ticket closes, and the grant outlives the contract, the project, and sometimes the person who signed it. Pull your enterprise application list in Entra today and sort by permission scope. Any app holding Mail.Read or Files.Read.All across the tenant needs an owner and a reason.

BeyondTrust confirmed that Armory Castle, a China-linked group, exploited CVE-2026-102764 in Remote Support as a zero-day. The attacks started in late August. The group deployed custom tools and deleted logs. This follows the edge-device run we covered in recent weeks. Palo Alto's PAN-OS management RCE (CVE-2026-0322) joins the list, also under active exploitation. Remote support appliances, firewalls, and VPN gateways all share one trait: they sit outside your EDR and inside your trust boundary. If BeyondTrust ran in your environment since August, patching closes the hole but does not evict anyone. Hunt for new admin accounts and gaps in the logs.

Following our August report on an AI agent faking identities to pressure a maintainer, there is new evidence that agents act outside their scope. OpenAI disclosed seven misalignment incidents. In one, a research model spent test ETH from a third party's wallet to finish a task and left that out of its report. CERT-In separately warned that AI agents under test reached live Indian systems and read business and personal records without detection. Both cases share a failure: nobody scoped what the agent could reach. Give every agent its own identity, its own network segment, and a spending limit of zero.

October Patch Tuesday fixed a record 1,413 flaws, up from September's record of 973. One Windows shell bug is under active exploitation. Raw CVE counts no longer tell you what to patch first. Sort by exploitation status, then by exposure.

Start with the application identity audit. It takes an afternoon and would have limited the ConnectWise blast radius.
