# Tasks: Parallel GC Marking

## Phase 1: Port

- [ ] Fetch DetSys PR #168 diff
- [ ] Identify GC initialization code (likely `src/libexpr/eval.cc` or `src/libutil/`)
- [ ] Set `GC_set_markers_count()` or `GC_MARKERS` env to use available cores
- [ ] Ensure nix packaging builds boehm-gc with `--enable-parallel-mark`

## Phase 2: Verify

- [ ] Run `meson test` — no regressions
- [ ] Run a large eval (nixpkgs `nix-env -qa`) and compare timing before/after
- [ ] Commit on a new branch `parallel-gc-2.33.3`
