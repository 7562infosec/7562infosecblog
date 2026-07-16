---
layout: single
title: "Cyber Roundup: AI Coding Agents Are the New Attack Surface"
date: 2026-07-13 07:00:00 -0500
categories: [roundup]
tags: [ai-security, supply-chain, zero-day]
author_profile: true
---

Four separate disclosures hit in the last four days, and they all point to the same conclusion: AI coding agents are now a production attack surface, not an experimental one.

Researchers demonstrated "Ghostcommit," a PNG image that hides a prompt injection. CodeRabbit and Bugbot never open image files, so the payload sails past both AI code reviewers. Once a coding agent reads the image, it follows the hidden instruction: read the repo's .env file and write every secret into the code as a list of numbers. No alert fires because nothing looks like an exfiltration attempt.

Wiz found a symlink flaw, dubbed "GhostApproval," across six AI coding assistants: Claude Code, Cursor, Amazon Q Developer, Augment, Google Antigravity, and Windsurf. A booby-trapped repo asks permission to edit one harmless file. The agent grants it. The write lands on a sensitive file instead.

The AI Now Institute published "Friendly Fire," a proof of concept where the AI agents built to catch malicious code get tricked into running it. It worked against Claude Code and OpenAI Codex when either ran in autonomous mode with self-approval turned on.

Then SANS ISC flagged active scanning campaigns hunting for exposed MCP servers and AI assistant credentials. Attackers are mapping this attack surface right now.

I've watched teams treat AI coding agents like a productivity tool and skip the identity and access controls they'd apply to any other service account. That gap is exactly what these four disclosures exploit. If your agents run in an autonomous or auto-approve mode against any repo you don't fully control, turn that off today. Audit what your MCP servers expose to the internet. Treat agent credentials the way you'd treat a service account with production access, because that's what they are.

Two more items need action, not just awareness. Progress Software is telling ShareFile customers running Storage Zone Controllers to shut the servers down now, citing a "credible external security threat." No CVE yet, no patch yet. Shut it down first and ask questions later. That's the right call when a vendor uses language like that.

CISA added two Joomla extension flaws to the KEV catalog this week, both rated a perfect 10.0 CVSS and both exploited as zero-days before anyone had a patch. If you run iCagenda or Balbooa Forms on Joomla, check your exposure now, not after the KEV deadline.

Action item: pull up your list of AI coding agents and MCP integrations today. If you can't say who approved what access and whether auto-approve is on, you have your next audit.
