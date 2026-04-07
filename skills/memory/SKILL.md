---
name: memory
description: >
  Save important information from conversations to the memory system. Triggers when user says
  "remember this" "save this" "don't forget" "record this" or /memory command. Also proactively
  triggers on new decisions, config changes, problem solutions, and preference updates.
user-invocable: true
---

# Memory Skill

## Trigger Scenarios

**Explicit:** "remember this" "save this" "don't forget" "record this" "/memory"

**Implicit (proactive):**
- Technical decisions or config changes
- Problem solutions
- Infrastructure changes
- User preference/requirement changes
- **Compaction test:** Would this info be lost on compaction? Yes → record it

## Workflow

### 1. Scan Conversation
Review all conversation from last memory write to now. Identify new decisions/settings/preferences.

### 2. Duplicate Check (mandatory before writing)

```bash
# Check journal + long-term index
grep -i "keyword" MEMORY.md memory/*.md

# Check knowledge base (notes/ included in memory_search)
memory_search "keyword"
```

- Exact duplicate → skip
- Partially related → merge into existing entry
- Conflict → keep newer, note replacement date

### 3. Classify and Store

**Follow `AGENTS.md` Classification Tree** for detailed logic.

Quick reference:
```
"What happened" (event/decision/status) → memory/YYYY-MM-DD.md
"What was learned" (knowledge/method) → notes/ or MEMORY.md
Error/Correction → .learnings/LEARNINGS.md
Preference/Infra → MEMORY.md (P0)
```

### 4. Check Patterns

After writing to `.learnings/LEARNINGS.md`:
- If `recurring_count ≥ 3` → Update `.learnings/PATTERNS.md`, propose system update

### 5. Report

List: what was recorded (summary), where it was stored, what priority level.
Nothing to record → `✅ No unrecorded important information`

## Condensation Principles

- Long conversations → condense to 3-5 sentences (keep: decisions, actions, conclusions)
- Keep specific numbers (IPs, ports, prices, parameters)
- Omit chitchat and intermediate attempts

## Quick Reference

```bash
# Check today's memory
cat memory/$(date +%Y-%m-%d).md

# Search memory
grep -rn "keyword" MEMORY.md memory/*.md

# Check MEMORY.md Events Timeline
grep "^- \*\*" MEMORY.md | tail -10
```

## Related Files

- **AGENTS.md** → Full Classification Tree and Memory Extraction logic
- **MEMORY.md** → Long-term index (P0/P1/P2)
- **.learnings/LEARNINGS.md** → Errors and corrections
- **.learnings/PATTERNS.md** → Recurring patterns (≥ 3 times)
