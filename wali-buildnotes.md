## Build Notes for WALI

You should be able to build the current commit simply with the 
`wasm32-wali-linux-musl` target.
Below are a list of concrete changes made to make that happen

### Crate Patches

Patches are required for `libc`, `nix` and `chrono`.
> NOTE: These will be removed after upstream

```toml
[patch.crates-io]
# REDOX START, Uncomment when you want to compile/check with redoxer
# REDOX END
libc = { git = "https://github.com/arjunr2/rust-libc.git", branch = "libc-0.2" }
nix = { git = "https://github.com/arjunr2/nix.git", branch = "r0.23" }
chrono = { git = "https://github.com/chronotope/chrono.git" }
```

The `Cargo.lock` should already be updated, but you can run an update command
again if necessary:
```shell
cargo update -p libc chrono nix
```

## Running Notes for WALI

Need stack size of at least 4MiB. If you see a 'Real Time Signal 5' error, try increasing stack size,
you might be overflowing
