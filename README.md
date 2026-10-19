# ShieldToad.exe

Prebuilt binaries of [ShieldToad](https://github.com/Inokinoki/ShieldToad-RS) —
a cross-platform sandboxed process launcher that compiles one unified policy
to macOS Seatbelt, Linux Landlock + seccomp, and Windows AppContainer.

**Binaries are distributed through [Releases](https://github.com/Inokinoki/ShieldToad.exe/releases)**,
one release per version (tag `vX.Y.Z`). This repository holds no binaries in git.

| Platform | Asset |
|---|---|
| macOS, Apple Silicon | `shieldtoad-<ver>-aarch64-apple-darwin.tar.gz` |
| macOS, Intel | `shieldtoad-<ver>-x86_64-apple-darwin.tar.gz` |
| Linux x86_64 | `shieldtoad-<ver>-x86_64-unknown-linux-gnu.tar.gz` |
| Windows x86_64 | `shieldtoad-<ver>-x86_64-pc-windows-msvc.zip` |

Every asset has a matching `.sha256`. Archives contain the `shieldtoad`
binary (`shieldtoad.exe` on Windows), `LICENSE` and the project `README.md`.

## Install

With the GitHub CLI (latest release):

```bash
gh release download --repo Inokinoki/ShieldToad.exe --pattern '*aarch64-apple-darwin*'
shasum -a 256 -c shieldtoad-*-aarch64-apple-darwin.tar.gz.sha256
tar xzf shieldtoad-*-aarch64-apple-darwin.tar.gz
./shieldtoad-*-aarch64-apple-darwin/shieldtoad --version
```

Or with curl, pinned to a version:

```bash
VER=0.2.0; T=aarch64-apple-darwin
curl -LO https://github.com/Inokinoki/ShieldToad.exe/releases/download/v$VER/shieldtoad-$VER-$T.tar.gz
```

Use `sha256sum -c` on Linux; on Windows compare
`Get-FileHash <zip> -Algorithm SHA256` with the `.sha256` file.
The Linux binary dynamically links the system `libseccomp`
(e.g. `sudo apt-get install libseccomp2`).

## Usage

```bash
shieldtoad -- /bin/echo hello                     # platform default preset
shieldtoad --preset claude-code -- claude         # built-in preset
shieldtoad --default deny --allow-read /tmp --allow-stdio -- /bin/cat /tmp/f
```

See the [main repository](https://github.com/Inokinoki/ShieldToad-RS) for
documentation, policy grammar and known limitations.

## Provenance

Assets are the unmodified archives from the matching
[ShieldToad-RS release](https://github.com/Inokinoki/ShieldToad-RS/releases),
built by that repository's release workflow.

## License

Apache License 2.0 (same as ShieldToad).
