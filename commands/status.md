---
name: status
description: Check if HLS is available, get version info, and verify it can start
allowed-tools:
  - Bash
---

# HLS Status Check

Perform a comprehensive health check of the Haskell Language Server (HLS) installation.

## Checks to Perform

Run these checks in order, reporting results for each:

### 1. PATH Check

Check if `haskell-language-server-wrapper` is available in PATH:

```bash
which haskell-language-server-wrapper || where haskell-language-server-wrapper
```

If not found, report common installation locations:
- `~/.ghcup/bin` (GHCup - recommended)
- `~/.local/bin`
- `~/.cabal/bin`

### 2. Version Check

If found, get version information:

```bash
haskell-language-server-wrapper --version
```

Report the HLS version and supported GHC versions.

### 3. Startup Test

Verify HLS can initialize by checking it responds to a simple request. Run:

```bash
echo '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"capabilities":{}}}' | timeout 10 haskell-language-server-wrapper --lsp 2>/dev/null | head -1
```

A valid JSON response indicates HLS can start successfully.

## Output Format

Report results clearly:

```
HLS Status Check
================

1. PATH:    [PASS/FAIL] - location or "not found"
2. Version: [PASS/FAIL] - version string or error
3. Startup: [PASS/FAIL] - "responds to LSP" or error

Overall: [HEALTHY/ISSUES DETECTED]
```

If any check fails, suggest running the troubleshooting skill or checking the HLS documentation.
