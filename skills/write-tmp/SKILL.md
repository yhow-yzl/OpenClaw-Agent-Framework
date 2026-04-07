---
name: write-tmp
description: >
  Writing temporary files in this workspace. Use when you need to save files to a temporary location — the workspace root /tmp is blocked; use /root/clawd/tmp/ instead.
user-invocable: true
---

# Write Tmp Files

## Rule

`/tmp` is outside the workspace root and will fail with "Path escapes workspace root".

**Always use `/root/clawd/tmp/` for temporary files.**

```bash
# ❌ Wrong
/tmp/output.md

# ✅ Correct
/root/clawd/tmp/output.md
```

## Setup

The directory may not exist yet:

```bash
mkdir -p /root/clawd/tmp
```

## Cleanup

Files here are not auto-cleaned. Remove when done:

```bash
rm /root/clawd/tmp/<file>
```

## Common Use Cases

| Scenario | Example |
|----------|---------|
| Download temporary data | `/root/clawd/tmp/downloaded-file.json` |
| Intermediate processing | `/root/clawd/tmp/processing-step-1.md` |
| Debug output | `/root/clawd/tmp/debug-log.txt` |
| Test file creation | `/root/clawd/tmp/test-output.md` |

## Related

- AGENTS.md → Red Lines: `trash > rm` (for non-temporary files)
- TOOLS.md → Active Connections (for permanent config)
