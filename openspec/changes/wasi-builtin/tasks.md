# Tasks: Merge builtins.wasm and builtins.wasi

## Phase 1: Verify Existing Implementation

- [x] Diff our `wasm.cc` against upstream merge commit `3306013` and confirm no behavioral differences beyond 2.33.3 API adaptations ✅ 30m (started: 2026-03-29T19:04Z -> completed: 2026-03-29T19:17Z)
- [x] Diff our `doc/manual/source/protocols/wasm.md` against upstream and confirm docs are identical ✅ 5m (started: 2026-03-29T19:09Z -> completed: 2026-03-29T19:09Z)
- [x] Fix wasmtime build: downgrade v40.0.2 -> v36.0.0 (v40 requires rustc 1.89, nixpkgs has 1.86) ✅ 12m (started: 2026-03-29T19:10Z -> completed: 2026-03-29T19:22Z)
- [x] Adapt wasm.cc for wasmtime 36 C++ API (InstancePre -> Linker+Module, file-based I/O capture, const-correctness) ✅ 5m (started: 2026-03-29T19:17Z -> completed: 2026-03-29T19:22Z)
- [x] Build nix-expr with wasm support enabled — compiles clean ✅ 1m (started: 2026-03-29T19:21Z -> completed: 2026-03-29T19:22Z)

## Phase 2: Test Fixtures

- [ ] Build a minimal non-WASI `.wasm` module (pure function: takes int, returns int) using `nix-wasm-rust` as reference
- [ ] Build a minimal WASI `.wasm` module (reads arg from argv, calls `return_to_nix`) using `nix-wasm-rust` as reference
- [ ] Build a WASI module that writes to stdout/stderr for I/O capture testing
- [ ] Commit fixtures to `tests/functional/wasm/` with a README documenting how they were built

## Phase 3: Functional Tests

- [ ] Add `tests/functional/wasm.sh` test script
- [ ] Test: non-WASI pure function call succeeds and returns correct result
- [ ] Test: WASI module call succeeds and returns correct result via `return_to_nix`
- [ ] Test: WASI stdout/stderr captured as warnings
- [ ] Test: error on missing `path` attribute
- [ ] Test: error on unknown attribute in config
- [ ] Test: error on `function` attribute with WASI module
- [ ] Test: error on missing `function` attribute with non-WASI module
- [ ] Test: error when WASI module finishes without calling `return_to_nix`
- [ ] Test: error without `--extra-experimental-features wasm-builtin`
- [ ] Wire `wasm.sh` into the meson test suite
