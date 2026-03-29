# Tasks: Merge builtins.wasm and builtins.wasi

## Phase 1: Verify Existing Implementation

- [ ] Diff our `wasm.cc` against upstream merge commit `3306013` and confirm no behavioral differences beyond 2.33.3 API adaptations
- [ ] Diff our `doc/manual/source/protocols/wasm.md` against upstream and confirm docs are current
- [ ] Build the project with wasm support enabled and confirm it compiles clean

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
