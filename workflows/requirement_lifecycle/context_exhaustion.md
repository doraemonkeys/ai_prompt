**Context: Your program has detected that this orchestrator's context window is nearly exhausted. This prompt is injected automatically to trigger a graceful handoff.**

---

**⚠️ CONTEXT LIMIT — IMMEDIATE HANDOFF REQUIRED**

Stop all current work. Do not dispatch any new agents. Perform these two actions only:

**Action 1:** Write the following state file.

**File:** `.agents/handoff.md`

```markdown
# Orchestrator Handoff

## Current Phase
{requirement_intake | goal_decomposition | plan_creation | plan_review_round_N | plan_execution | goal_completion}

## Current Goal
Goal {N}: {goal_name} — {brief status}

## Progress Summary
{2-3 sentences: what has been completed, what is in progress}

## Active Agents
{List any Sub-Agents or teammates still running, with their assigned tasks. Write "None" if all have completed.}

## Key Decisions
{Design decisions confirmed with the user during this session. Reference clarifications.md for full history.}

## Next Action
{The exact next step the replacement orchestrator should take. Be specific: e.g., "Read verdict for plan_review round 3. If no major issues, proceed to final user checkpoint."}

## Warnings
{Anything the replacement orchestrator must be careful about: file conflicts, partial state, user preferences expressed in conversation but not yet recorded, etc.}
```

**Action 2:** Output this exact line when done:

`Handoff complete. State written to .agents/handoff.md.`
