# Work In Progress: HLS Plugin for Claude Code

## Current Status

**Phase**: 7 of 7 (Testing & Verification) - READY FOR TESTING
**Last Updated**: 2026-01-01

## Project Summary

Built a Claude Code plugin that integrates Haskell Language Server (HLS) for Haskell development. The plugin provides LSP features (diagnostics, navigation, completions, etc.) and guided troubleshooting.

## Completed Work

### Phase 1: Discovery ✓

- [x] Reviewed PRD.md requirements
- [x] Reviewed Claude Code plugin documentation
- [x] Reviewed HLS documentation
- [x] Clarified requirements with stakeholder
- [x] Updated PRD.md with technical details

### Phase 2: Component Planning ✓

- [x] Analyzed needed components
- [x] Decided: Skill focuses on troubleshooting only
- [x] Decided: Single `/hls:status` command
- [x] Decided: XML docs in skill's references directory

### Phase 3: Detailed Design ✓

- [x] Designed LSP config with loggingConfig
- [x] Designed skill with trigger phrases
- [x] Designed status command with 3-level checks

### Phase 4: Plugin Structure Creation ✓

- [x] Created directory structure
- [x] Created plugin.json manifest
- [x] Created .lsp.json for HLS
- [x] Moved XML docs to skill references

### Phase 5: Component Implementation ✓

- [x] Implemented `/hls:status` command
- [x] Implemented HLS troubleshooting skill

### Phase 6: Validation & Quality Check ✓

- [x] Validated plugin structure
- [x] Validated skill (725 words, no second-person, imperative form)
- [x] All components pass validation

### Phase 7: Testing & Verification (CURRENT)

- [ ] Test with `claude --plugin-dir`
- [ ] Verify LSP features work on `.hs` files
- [ ] Test `/hls:status` command
- [ ] Test troubleshooting skill triggers
- [ ] Test `--enable-lsp-logging` if available

## Final Plugin Structure

```
claude-hls/
├── .claude-plugin/
│   └── plugin.json              ✓
├── .lsp.json                    ✓
├── commands/
│   └── status.md                ✓
└── skills/
    └── hls-troubleshooting/
        ├── SKILL.md             ✓
        └── references/
            ├── hls-docs.xml     ✓
            ├── ghc-user.xml     ✓
            └── cabal-docs.xml   ✓
```

## Key Decisions

| Decision | Resolution |
|----------|------------|
| LSP command | `haskell-language-server-wrapper --lsp` |
| File extensions | `.hs`, `.lhs` |
| LSP features | All available |
| Debug logging | Via `--enable-lsp-logging`, logs to `~/.claude/debug/` |
| Skill focus | HLS troubleshooting only |
| Status checks | PATH + version + startup test |

## Testing Instructions

### Run Plugin

```bash
claude --plugin-dir /mnt/c/Users/Justin/Source/claude-hls
```

### Test Commands

1. **Status check:**
   ```
   /hls:status
   ```

2. **Skill trigger (try any of these):**
   ```
   HLS is not working, can you help?
   ```
   ```
   Why am I not getting Haskell completions?
   ```
   ```
   Troubleshoot HLS for me
   ```

3. **LSP verification:**
   - Open a `.hs` file
   - Check for diagnostics, completions, hover info

### Expected Results

- `/hls:status` performs 3 checks with pass/fail output
- Troubleshooting skill loads when HLS issues mentioned
- LSP features work for `.hs` and `.lhs` files (requires HLS installed)

## Files Not Shipped (Development Only)

These files are for development reference and should not be included in distribution:

- `plugins.html`
- `plugins-reference.html`
- `settings.html`
- `claude-code.xml`
- `PRD.md`
- `WIP.md`

## Next Steps After Testing

1. Fix any issues found during testing
2. Add utility scripts if needed
3. Consider publishing to marketplace
4. Create README.md for users
