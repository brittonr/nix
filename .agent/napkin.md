# Napkin

## Corrections
| Date | Source | What Went Wrong | What To Do Instead |
|------|--------|----------------|-------------------|

## User Preferences
- Working on a CppNix 2.33.3 fork, cherry-picking from DetSys and Lix
- Uses openspec for change management
- Build system: meson, C++23, Nix flake

## Patterns That Work
- (accumulate here as you learn them)

## Patterns That Don't Work
- (accumulate here as approaches fail and why)

## Domain Notes
- wasmtime downgraded from v40.0.2 to v36.0.0 (v40 needs rustc 1.89, nixpkgs has 1.86)
- v36 C++ wrapper: no `capi()`, no `WASMTIME_OWN_WRAPPER`, no custom stdout/stderr callbacks
- v36 adaptation: replaced `InstancePre` wrapper with `Linker` + `Module` pair, file-based I/O capture
- `ImportType::Ref::module()` is non-const in v36 — use `auto ref` not `const auto & ref`
- `WasiConfig::stdout_file()` / `stderr_file()` are `[[nodiscard]]` — must check return values
- `builtins.wasm` cherry-pick (23f3ccee2) already included the merged wasm/wasi from DetSys #359 + #370
- Commit d444c28c4 fixed compilation against 2.33.3 API (wasmRealisePath, .fun field, explicit std::vector)
- Zero wasm/wasi tests exist in the repo
- Experimental feature gate: `Xp::WasmBuiltin` / `--extra-experimental-features wasm-builtin`
