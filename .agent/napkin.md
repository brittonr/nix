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
- wasmtime v40.0.2 is the Wasm runtime dependency
- `builtins.wasm` cherry-pick (23f3ccee2) already included the merged wasm/wasi from DetSys #359 + #370
- Commit d444c28c4 fixed compilation against 2.33.3 API (wasmRealisePath, .fun field, explicit std::vector)
- The proposal's "filesystem mappings and environment" language was aspirational — neither DetSys PR added those
- Zero wasm/wasi tests exist in the repo
- Experimental feature gate: `Xp::WasmBuiltin` / `--extra-experimental-features wasm-builtin`
