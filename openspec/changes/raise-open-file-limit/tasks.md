# Tasks: Raise Open File Soft Limit

## Phase 1: Port

- [ ] Fetch DetSys PR #347 diff
- [ ] Add `setrlimit(RLIMIT_NOFILE, ...)` call in startup path
- [ ] Guard with `#ifdef __linux__` / `#ifdef __APPLE__` as needed

## Phase 2: Verify

- [ ] Run `meson test`
- [ ] Verify `ulimit -n` inside a nix-spawned process reflects the raised limit
- [ ] Commit on a new branch `raise-fd-limit-2.33.3`
