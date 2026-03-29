# Tasks: build-dir Setting

## Phase 1: Port

- [ ] Study Lix CL/1514 and upstream gh#10303 diffs
- [ ] Add `build-dir` setting to `src/libstore/globals.hh`
- [ ] Use `build-dir` in sandbox temp directory selection in `local-derivation-goal.cc`
- [ ] Remove `XDG_RUNTIME_DIR` from default temp directory candidates
- [ ] Add documentation for the setting

## Phase 2: Verify

- [ ] Run `meson test`
- [ ] Test: set `build-dir = /var/tmp/nix-builds`, build a derivation, confirm sandbox uses it
- [ ] Test: verify `nix-shell` / `nix develop` TMPDIR is NOT affected by `build-dir`
- [ ] Commit on a new branch `build-dir-2.33.3`
