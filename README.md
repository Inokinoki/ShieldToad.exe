# ShieldToad.exe

Prebuilt binaries of [ShieldToad](https://github.com/Inokinoki/ShieldToad-RS) —
a cross-platform sandboxed process launcher that compiles one unified policy
to macOS Seatbelt, Linux Landlock + seccomp, and Windows AppContainer.

Binaries are organised by version, one directory per release:

```
v0.2.0/
├── shieldtoad-0.2.0-aarch64-apple-darwin.tar.gz       # macOS, Apple Silicon
├── shieldtoad-0.2.0-x86_64-apple-darwin.tar.gz        # macOS, Intel
├── shieldtoad-0.2.0-x86_64-unknown-linux-gnu.tar.gz   # Linux x86_64
├── shieldtoad-0.2.0-x86_64-pc-windows-msvc.zip        # Windows x86_64
└── *.sha256                                           # SHA-256 for each archive
```

Each archive contains the `shieldtoad` binary (`shieldtoad.exe` on Windows),
`LICENSE` and the project `README.md`.

## Install

```bash
# pick the archive for your platform, e.g. macOS Apple Silicon
curl -LO https://github.com/Inokinoki/ShieldToad.exe/raw/main/v0.2.0/shieldtoad-0.2.0-aarch64-apple-darwin.tar.gz
curl -LO https://github.com/Inokinoki/ShieldToad.exe/raw/main/v0.2.0/shieldtoad-0.2.0-aarch64-apple-darwin.tar.gz.sha256
shasum -a 256 -c shieldtoad-0.2.0-aarch64-apple-darwin.tar.gz.sha256
tar xzf shieldtoad-0.2.0-aarch64-apple-darwin.tar.gz
./shieldtoad-0.2.0-aarch64-apple-darwin/shieldtoad --version
```

On Linux use `sha256sum -c`; on Windows compare
`Get-FileHash <zip> -Algorithm SHA256` with the `.sha256` file.

The Linux binary dynamically links the system `libseccomp`
(e.g. `sudo apt-get install libseccomp2`).

## Usage

```bash
shieldtoad -- /bin/echo hello                     # platform default preset
shieldtoad --preset claude-code -- claude         # built-in preset
shieldtoad --default deny --allow-read /tmp --allow-stdio -- /bin/cat /tmp/f
```

See the [main repository](https://github.com/Inokinoki/ShieldToad-RS) for the
full documentation, policy grammar and known limitations.

## Provenance

These are the unmodified archives attached to the corresponding
[ShieldToad-RS GitHub Releases](https://github.com/Inokinoki/ShieldToad-RS/releases),
built by that repository's release workflow. Source and issues live there.

## License

Apache License 2.0 (same as ShieldToad).
