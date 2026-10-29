# bashscripts

Small, portable (Linux + macOS, bash 3.2+) helper scripts.

| Script | Purpose |
| --- | --- |
| `setup_ssh_keys [comment]` | Create an ed25519 key if missing and load it into the ssh-agent (uses the macOS keychain on Darwin). |
| `test_ssh_connection [host]` | Check SSH auth against a git host (default `github.com`). |

## Roadmap

Planned scripts and ideas live in [ROADMAP.md](ROADMAP.md).

## Install

    mkdir -p ~/.local/bin
    ln -s "$PWD"/{setup_ssh_keys,test_ssh_connection} ~/.local/bin/

Make sure `~/.local/bin` is on your `PATH`.

## Development

Scripts are linted with [shellcheck](https://www.shellcheck.net/) on Ubuntu and macOS via GitHub Actions.
