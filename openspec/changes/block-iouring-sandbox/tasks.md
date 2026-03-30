# Tasks: Block io_uring in Sandbox

## Phase 1: Port

- [ ] Study Lix CL/1611 diff
- [ ] Locate seccomp filter setup in `src/libstore/` (Linux sandbox code)
- [ ] Add `io_uring_setup` (SYS 425), `io_uring_enter` (SYS 426), `io_uring_register` (SYS 427) to deny list
- [ ] Return `ENOSYS` for denied syscalls (not EPERM — programs check for kernel support via ENOSYS)

## Phase 2: Verify

- [ ] Run `meson test`
- [ ] Test: write a small C program that calls `io_uring_setup()`, build it in sandbox, confirm ENOSYS
- [ ] Verify normal builds (no io_uring) are unaffected
- [ ] Commit on a new branch `block-iouring-2.33.3`
