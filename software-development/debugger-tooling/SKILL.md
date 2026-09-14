---
name: debugger-tooling
description: "Use when attaching language/runtime debuggers from Hermes, especially Python debugpy/pdb and Node.js inspector/Chrome DevTools Protocol workflows."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [debugging, debugpy, pdb, node-inspect, cdp, breakpoints]
    related_skills: [software-development-lifecycle]
---

# Debugger Tooling

## Overview

Use this umbrella when a bug requires an interactive debugger rather than logs/tests alone. Python `debugpy`/`pdb` and Node's inspector expose different protocols, but the workflow is the same: reproduce under debugger, set targeted breakpoints, inspect state, step minimally, and turn the finding into a small fix plus regression check.

## When to Use

- A test or process fails but logs do not reveal the wrong state.
- You need to inspect live variables, call stacks, async behavior, or runtime objects.
- Python code benefits from `pdb`, `debugpy`, or DAP-style attachment.
- Node.js code benefits from `--inspect`, DevTools Protocol, breakpoints, or heap/runtime inspection.

## Universal Debugger Workflow

1. Reproduce the failure with the smallest command.
2. Start the target with debugger hooks enabled.
3. Attach with the appropriate client/protocol.
4. Set breakpoints near the suspected root cause.
5. Inspect variables/call stack; step only as much as needed.
6. Patch the root cause and rerun tests without the debugger.

## Python: pdb/debugpy

Use `python -m pdb ...` for local CLI stepping or `debugpy` when attaching to running/test processes.

```bash
python -m debugpy --listen 5678 --wait-for-client -m pytest tests/test_x.py::test_case
```

Avoid leaving `breakpoint()`/debugpy waits in committed code.

## Node.js Inspector

Start with `node --inspect-brk script.js` or the test runner's inspect flag, then connect through Chrome DevTools Protocol tooling. Use breakpoints and runtime evaluation to inspect objects without broad code edits.

## Common Pitfalls

1. **Debugging a different command than the failing one.** Keep flags/env/working directory identical.
2. **Stepping blindly.** Break near the suspected state transition.
3. **Port conflicts.** Check and choose free debugger ports.
4. **Committing debugger hooks.** Remove waits, breakpoints, and verbose probes.
5. **No post-debug test.** The debugger explains; tests verify.

## Verification Checklist

- [ ] Failure reproduced under the debugger.
- [ ] Root cause identified from runtime state, not guessed.
- [ ] Debug hooks removed after patching.
- [ ] Targeted and relevant broader tests reran.
