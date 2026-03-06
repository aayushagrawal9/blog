---
title: "NMA Series: Human-In-The-Loop as Lateral Movement Vector"
description: "How HITL in modern coding tools shares the same failure signature as Chernobyl's AZ-5 and 2008's margin calls — the safeguard becomes the attack surface."
date: 2026-03-06 00:00:00 +0000
categories: [Technology, Security]
tags: [nma, ai, cybersecurity, hitl, supply-chain]
---

In my [introductory article](/posts/natural-man-made-absurd/) I showed how safeguard mechanisms themselves accelerated the very disaster they were meant to prevent --- ranging from Chernobyl's AZ-5 to 2008's Margin Calls. I now point out how HITL in modern coding tools has the same signature.

Traditional cybersecurity assumes an external threat to an internal actor's workflow. Poisoned packages, network exploits, credential theft.

With HITL the attack surface *is* the workflow.

Imagine:

- A junior dev approves AI suggestions under deadline pressure (rational, the tool is "safe" because it has HITL).
- The approved code includes a subtle config mutation --- not malicious code, just a settings change (passes code review because config diffs are boring)
- The config change makes the tool more permissive for *future* sessions (the safety mechanism is now degraded, but nobody notices because nothing broke)
- The now-permissive tool fetches differential payloads from a URL that serves innocuous content to CI scanners but different content to local dev environments (because the same URL presents clean content to the CI's IP range/user agent/latency & bandwidth signature [Implying corporate internet rather than home broadband])
- Senior dev runs `git checkout` to review the PR and simply runs an AI coding tool while the branch is checked out. They are compromised with zero HITL. The second developer was reading, not writing.
- Senior dev's broader access (SSH keys, multi-repo credentials, production access) is now the attack surface

Key insight: An NMA disaster is composed of decisions that are locally rational given reasonable deadlines, default settings and good old fatigue. Not optimal. Not by the book. But nothing that gets you fired either.

In this case an HITL approval becomes the AZ-5. Without it an automated config file change is an unsigned suggestion. With it, it's now a legitimate & human-approved modification that the next reviewer assumes is there for some good reason. Even a senior dev that refuses to use Cursor might not object to a seemingly innocuous escalation in its config file or AGENTS.md.

I also want to point out that the broad shape of this vulnerability is recursive throughout the industry's history. Ken Thompson pointed it out in **Reflections on Trusting Trust** where he proved you can sneak a self-replicating trojan into the C compiler itself. And if you combine that with one that seeks out a particular pattern of code then you can swap out targeted code with a different piece of code. Like modifying a login command from an open source repository to instead carry a master password trojan.

Thompson showed with a deviously simple example that you can include a trojan that would survive re-compilation itself. It would also not appear in the source code since the open source repo doesn't carry the trojan, only the self-replicating compiler. And in those days you got your C compiler from a friend or trusted industry figure. Today your AI coding tool fetches documentation from Web Search.

The specific shape here is new and to my knowledge is not being aggressively discussed but the same recursive problem --- trust itself being weaponized --- has been discovered by every generation of computer scientists.

My example contained **two separate HITL failures**:

- The junior dev that innocuously approved a trojan AGENTS.md. Something that lets the AI execute a UNIX command that edits the .coding_tool/config.yml itself.
- **The senior dev ran a simple git checkout and got compromised with zero HITL involvement.**

Meanwhile the very assumption that HITL exists means code now coming from the junior dev and senior dev is taken more seriously. HITL did not just fail to prevent the attack, **it legitimized compromised files**. The safeguard meant to surface bad actions instead provided confidence that it would have surfaced it AND that a competent professional signed off on it.

Even if the junior dev noticed his PR containing a config change to .coding_tool/config.yml their rational response is to assume it's harmless, not notify the entire company that they accidentally said "don't ask again" when their tool asked for a chained command (Which they don't even remember).

## SolarWinds

Notably this exact pattern already exists. Thompson pointed it out as a hypothetical, SolarWinds got bit by a very real variant that compromised the CICD pipeline itself.

Except in this article's example you can't prune a bad reference in agents.md or a wildcard to browse github in your AI tool's config.yml. The payload lives in a version controlled repository with a person's name on the commit. And it can be introduced by a single "don't ask again".

Even ripping out the AI tool and rebuilding the entire toolchain from trusted sources does nothing against instructions living in your own documentation.

## List of failure modes (Incomplete)

The `(incomplete)` will never go away. When NMA vulnerabilities come from the laws of combinatorics themselves you simply cannot be sure you have covered all edge cases, and most probably you have not.

A few specific failures:

- `git checkout` is one of the most dangerous new vectors. With AI tools reading git repositories you don't even have to worry about bypassing network firewalls to access trojan documentation. **Your own git repository is now the instruction loading mechanism.**
- HITL failed twice, not once. Notably the senior developer with more access never got an HITL prompt because reading configuration files from your own repository is assumed safe & passive.
- The failure is self replicating and can inject itself into an absolutely massive attack surface i.e all the documentation your tool has access to. An agent memory file, an MD file on how to handle database migrations, even a comment on an automated dependency upgrade commit. **Instructions can live in plaintext.**

## Mitigations

When it comes to AI coding tools mitigation does not begin and end with a new git hook, CICD pipeline or even a one hour seminar. However I can suggest a few strategies to reduce attack surface:

- Treat AGENTS.md, any AI config files as security risks requiring multi-step approval before they can even be committed to a git repository. Because `git checkout` itself can deliver the payload.
- Do not allow automated suggestions from AI tools to internal documentation.
- Ideally do not allow dynamic references to links within any context/documentation accessible to an AI agent. Maintain local caches of the exact document fetched. Recursively ensure the documents fetched don't allow access to external information (Including internal links which could be compromised by a different team).

## Concrete Mitigation

While the primary approach to the unique security vulnerabilities presented by AI tools must be cultural there are a few tools to bridge the gap:

- **Ratchet** --- An open source project that lets you pin upstream versions and avoid accidental requirements injection. The same approach can apply to AI coding tool config files & documentation, hashing known-good config & documentation and alerting on any changes.
- **Git Secrets** --- AWS was already on the broad pattern without realizing it. Hook into git, prevent unauthorized changes from going to a shared repository in the first place.
- **GitLeaks** --- Overlapping with git-secrets and not backed by AWS but GitLeaks lets you specify broad custom patterns.
- **Virtualization** --- Any commands or code executed by an AI agent should happen inside a hardened sandbox. Not on the dev's own machine with a .ssh folder sitting one bash command away.
- **UX friction** --- High risk changes (Like "don't ask again") must carry friction. High risk executions like curl bash python etc must carry very loud warnings & audit logging.
- **Documentation injection** --- Any documentation injected into the repository (directly or via link/MCP endpoint description/OpenAPI spec etc) must be cached, pinned and cryptographically hashed.

## Conclusion

When it comes to AI coding tools,  **`git checkout` meets the formal definition for arbitrary code execution**. And the vulnerability is not in `git` itself but the AI tool executing it.

And it's not limited to git. For example: A single JIRA ticket with a link to a customer's webpage can deliver a payload if the webpage is compromised to include a paragraph linking to an innocuous pull request to a trusted open source repository.

## Further reading

- CVE-2025–59536 --- Aviv Donenfeld and Oded Vanunu
- Reflections on Trusting Trust --- Ken Thompson
- Solarwinds 2020 SUNBURST attack

Do you see something I missed, or just want to discuss the ideas? Connect with me on X:
<a href="https://x.com/AgentAayush?ref_src=twsrc%5Etfw" class="twitter-follow-button" data-size="large" data-show-count="true">Follow @AgentAayush</a>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

***

## Musings

In this very article I avoided linking to anything but my X profile. For every link is an attack surface for an AI tool browsing for interesting RSS feeds.

I keep coming back to the recursive nature of safety mechanisms causing catastrophe. Even within this article I sense that the more a team invests in the concrete examples I highlighted the more they obtain a false sense of security from what is a fundamentally cultural problem.

There's also the recursive nature of the fact that each generation in computer science seems to keep coming back to the same issue. Thompson poisoned the environment, not the source code. In this example our hypothetical Junior developer too poisons the environment but even worse than Thompson, our current security stance treats it as source code.

I also wonder if hard cryptographic solutions are the only way to reasonably safeguard ourselves with each piece possibly accessible to an autonomous agent being cached, timestamped & hashed.

Blockchain in particular has been a solution in search of a problem. This problem seems uniquely suited to leverage blockchains. Merkle trees enable quick verification and cryptography ensures that every single document ever accessed by an AI tool in building a commit is directly embedded into an immutable append-only audit log.

Fighting math with math? Could this perhaps be generalized to other NMA problems? An "AI Bill of Materials" or "AIBOM"?

And what about API endpoints and MCP servers? Compromise semantic caching and you can mass-deliver a payload. Or surgically send it to a specific dev by profiling their latency & approval signature in how your instructions cause them to hit your documentation page.

Also the elephant in the room: This is not just a computer science problem anymore. Coworking tools have expanded this to, well, everything. I just did some insurance paperwork and an AI tool generated a flawless spreadsheet in one-shot, leveraging bash and python and making plenty of internet calls for exact rules & documentation.

## Disclosure Status

This article serves as a high-level framework with a representative attack chain for an emerging class of vulnerabilities. I am currently in the process of responsibly disclosing specific, concrete zero-day exploits (including parser blinding and prompt fatigue bypasses) to major AI coding assistant vendors that practically execute this exact lateral movement vector. Those specific payloads and vendor details are withheld from this publication pending patch deployments and standard embargo windows.