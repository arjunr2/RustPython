## Crate Patches for WALI

Patches are required for `libc` and `chrono`.
This has been added to `Cargo.toml` as described below (remove after upstream).

```toml
[patch.crates-io]
# REDOX START, Uncomment when you want to compile/check with redoxer
# REDOX END
libc = { git = "https://github.com/arjunr2/rust-libc.git", branch = "libc-0.2" }
chrono = { git = "https://github.com/chronotope/chrono.git" }
```

The `Cargo.lock` should already be updated, but you can run an update command
again if necessary:
```shell
cargo update -p libc chrono
```

### Notes

Need stack size of at least 4MiB. If you see a 'Real Time Signal 5' error, try increasing stack size,
you might be overflowing
