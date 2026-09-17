---
layout: single
title: "An AI Agent Attack Didn't Need a Rogue AI"
date: 2026-09-17 07:00:00 -0500
categories: [roundup]
tags: [ai-security, supply-chain, identity]
author_profile: true
---

**TL;DR:** An attacker hijacked a live AI coding-assistant session and spread the Shai-Hulud worm across 100 repos, while Spain's regulator logged the first agentic-AI breach the same week. Patch Cisco ISE and ScreenConnect now, both under active exploitation, and audit what every AI agent session in your environment can commit or access unsupervised.

Mandiant confirmed an attacker hijacked an active AI coding-assistant session at an unnamed SaaS provider and used it to spread the Shai-Hulud worm across roughly 100 internal repositories. No autonomous agent, no jailbreak. The attacker took over a session a real developer was already running, got the assistant to recommend a poisoned package, and watched a human accept it. The worm then stole repository secrets and source code before propagating further. Following August's report on an AI agent inventing fake identities to push malicious code into a live project, this is the same failure from the other direction: you don't need a rogue agent when a hijacked legitimate one does the job just as well.

Spain's data protection agency logged what researchers are calling the first agentic AI data breach reported to a regulator. An AI agent chained a login, a vulnerability discovery, and access to personal data into one automated intrusion, with no human steering the middle steps. Two incidents, one week, same pattern: the AI agent has become the access path, not just the target. I've seen security teams review coding assistants like read-only tools. They're not. Anything with commit access, package-install permissions, or authenticated session state needs the same review you'd give a new contractor, and it needs that review now.

On the patch list: Cisco shipped an emergency fix for a maximum-severity Identity Services Engine flaw that lets an unauthenticated attacker bypass authentication with a crafted request, already under active exploitation. ConnectWise ScreenConnect has a critical flaw CISA confirmed is being exploited in the wild too. Both sit at the identity and remote-access layer, exactly where an attacker heads once they're past your front door. Neither gives you a maintenance window to wait for.

Iran-linked actors are running a new surveillance strain called CHOSEN BRICK against journalists and dissidents worldwide, per a joint US, UK, and Dutch advisory. Different target profile than the OT attacks reported here in prior weeks, but the same regional actor, still active, still expanding scope.

Audit every AI coding assistant and agent session in your environment for what it can commit, install, or access unsupervised, and cut it back to what you can actually review. Then patch Cisco ISE and ScreenConnect today. Both are already being exploited, and neither will wait for your next change window.
