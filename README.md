# tarzen

Universal `.tar.xz` / `.tar.gz` installer for Linux. One command to extract, detect, and install — no matter what's inside.

## Install

```bash
curl -sL https://raw.githubusercontent.com/mxskeen/tarzen/main/tarzen | sudo bash
```

## Usage

```bash
sudo tarzen install ./app.tar.xz   # local file
sudo tarzen install ./app.tar.gz   # local file (gzipped)
sudo tarzen install https://example.com/app.tar.xz # from URL
tarzen list # see installed apps
sudo tarzen uninstall <app-name> # remove an app
tarzen info # show system info
```

## What it handles

| Content Type | Behavior |
|---|---|
| Pre-built binary | Moves to `/opt`, symlinks to `/usr/local/bin`, creates `.desktop` entry |
| AppImage | Installs to `/opt`, symlinks, desktop entry |
| Nested `.deb` | Installs via `apt`/`dpkg` |
| Nested `.rpm` | Installs via `dnf`/`zypper`/`rpm` |
| Source (CMake) | `cmake .. && make && make install` |
| Source (Make) | `make && make install` |
| Source (Autotools) | `./configure && make && make install` |
| Source (Meson) | `meson setup && ninja && ninja install` |
| Source (Cargo) | `cargo build --release && cargo install` |
| Source (Go) | `go build && go install` |

Detection is automatic. Just point tarzen at a file and it figures out the rest.

## Distro support

Auto-detects your distro and package manager via `/etc/os-release`. Works on Ubuntu, Debian, Fedora, RHEL, Arch, Manjaro, openSUSE, Alpine, Void, Gentoo, NixOS, and more.

## Self-management

```bash
tarzen --self-install # install/update tarzen itself
tarzen --self-uninstall # remove tarzen from system
```

## Uninstall tarzen

```bash
sudo tarzen --self-uninstall
```

## Requirements

- Linux with Bash
- `sudo` access for install/uninstall operations
- `curl` or `wget` for URL downloads

Zero dependencies. Single file. One command install.

## License

MIT
