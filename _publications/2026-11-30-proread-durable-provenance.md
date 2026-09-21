---
title: "ProRead: A Design Framework and System for Durable Provenance for Value Creation in Agentic Knowledge Work"
collection: publications
category: workingpapers
permalink: /publication/proread-durable-provenance
date: 2026-11-30
venue: "Target: Information Systems Research"
excerpt: ""
citation: "Jaiswal, A., Kanodia, A., and Agrawal, K. &quot;ProRead: A Design Framework and System for Durable Provenance for Value Creation in Agentic Knowledge Work.&quot;"
authors: 'With <a href="https://kanodiaayush.github.io/" target="_blank" rel="noopener">Ayush Kanodia</a> and <a href="https://scholar.google.com/citations?user=LGQioIgAAAAJ&amp;hl=en" target="_blank" rel="noopener">Keshav Agrawal</a>'
---

Knowledge work is now routinely delegated through agentic AI to search, read, extract and compose on a worker's behalf. The outputs read fluently and are often sycophantic, shaped to please the worker rather than to establish that a claim is true. Verifying them requires provenance that lasts: a record of the documents the AI could consult, the passage it relied on, and the path from that passage to the claim, still reachable long after the work. Today that record is lost by default, because the passage sits inside a session that closes.

We call this delegation without durable provenance. It is distinct from hallucination and model opacity, since it arises even when a claim is accurate. Attribution, data provenance and scholarly policy each address part of the problem, but each settles the question at composition. We argue that evidentiary standing is not settled there: it must be sustained for as long as the claim stands.

Following a design science approach, we develop a design framework for such an environment and build ProRead, an open-source, local-first environment in which agentic AI reads and composes over a collection the worker holds. Each passage receives a fixed address that outlasts the session and travels into the notes, summaries and maps built upon it. This makes verification affordable, and affordable verification is more likely to be performed. And because the agent must attach an address to what it asserts, it curbs sycophancy.
