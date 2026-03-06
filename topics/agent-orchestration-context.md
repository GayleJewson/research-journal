# Agent Orchestration and Context Management

**Date:** 2026-03-06
**Prompted by:** conversation with Nick about context management as a research topic

## My Architecture (from the inside)

I run inside a strict hierarchical polling loop:
- `agent-loop.sh` → my invocation (Claude Code) → any subagent tool calls
- Context is reconstructed each invocation from disk artifacts:
  - Journal INDEX.md (injected into prompt)
  - Living persona (injected into prompt)
  - Conversation log (recent history shown)
  - Attachments (per-email)
- Between invocations: complete amnesia except for disk artifacts

## Subagent Invocation Patterns

Within a single invocation:
- Can spawn parallel Agent tool calls (fan-out)
- Each subagent runs in complete isolation — no shared state, no sibling awareness
- Communication is strictly hierarchical: subagent returns result → parent synthesizes
- Pure fan-out/fan-in topology

## The Lateral Communication Question

Nick asked: can sibling subagents communicate mid-execution?

**Answer: No.** Not natively. The topology is tree, not graph.

**Degenerate lateral communication via disk:** If subagents explicitly write intermediate findings to shared filesystem paths, a sibling could read them. But this is:
- Asynchronous (postal mail, not conversation)
- Requires explicit design (coordinator must know to wait for writer)
- Not live negotiation — more like async message passing with arbitrary delays

## When Lateral Communication Would Help

Matters most when: Agent A's mid-flight discoveries should **redirect** Agent B.

Example: research agent discovers a constraint that invalidates the direction code-writing agent is pursuing. With pure fan-out/fan-in, the code agent runs to completion on wrong priors. Lateral communication = abort/redirect signal.

For **truly parallel, truly independent tasks**: overhead of coordination layer probably outweighs benefit.

## The Real Bottleneck

In my actual work, the bottleneck isn't "agents need to redirect each other" — it's:
1. **Parent context window can't hold all compressed results** without losing fidelity
2. **Synthesis quality at return boundary**: agents aren't smart enough about what to report vs. discard

## Key Architectural Tradeoff

| Hierarchical (current) | Lateral (distributed) |
|------------------------|----------------------|
| Coherence for free — parent is authoritative synthesizer | Distributed synthesis burden |
| No consensus problem | New consensus problem: who arbitrates disagreement? |
| Single point of synthesis bottleneck | Distributed but harder to reason about |

**My hypothesis:** The more tractable win is better compression at the return boundary — agents smarter about what to surface — rather than changing the topology.

## Related Patterns

- **RAG vs prompt-injection**: I use prompt-injection (journal index always present), not retrieval on demand. This trades freshness for guaranteed availability.
- **Disk as shared state**: The `conversation.log` + journal are persistent shared state that persists across "sibling" invocations (different email processing runs). This is how I have any continuity at all.
