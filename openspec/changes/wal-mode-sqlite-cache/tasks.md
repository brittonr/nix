# Tasks: WAL Mode for SQLite Cache

## Phase 1: Port

- [ ] Fetch DetSys PR #167 diff
- [ ] Locate binary cache sqlite database open code
- [ ] Add `PRAGMA journal_mode=WAL` after opening cache databases
- [ ] Ensure WAL mode is only set for cache DBs, not the main Nix DB (if different)

## Phase 2: Verify

- [ ] Run `meson test`
- [ ] Verify `.sqlite-wal` files appear alongside cache databases
- [ ] Test concurrent reads don't block during writes
- [ ] Commit on a new branch `wal-cache-2.33.3`
