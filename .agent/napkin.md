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
- `builtins.wasm` already exists with basic WASI auto-detection (checks for `wasi_snapshot_preview1` imports)
- Current WASI support: stdout/stderr capture, argv passing, `return_to_nix` callback
- Missing from current WASI: filesystem preopens, environment variable passing
- DetSys PRs: #359 (builtins.wasi), #370 (merged wasi into wasm)
