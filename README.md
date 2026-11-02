# bashscripts

Small, portable (Linux + macOS, bash 3.2+) helper scripts.

| Script | Purpose |
| --- | --- |
| `setup_ssh_keys [comment]` | Create an ed25519 key if missing and load it into the ssh-agent (uses the macOS keychain on Darwin). |
| `test_ssh_connection [host]` | Check SSH auth against a git host (default `github.com`). |
| `ssh_tunnel <host> [port \| local:remote]...` | Forward remote ports to localhost over SSH (default `3000`), e.g. to view a remote dev server in a local browser. |

## Roadmap

Planned scripts and ideas live in [ROADMAP.md](ROADMAP.md).

## Install

    mkdir -p ~/.local/bin
    ln -s "$PWD"/{setup_ssh_keys,test_ssh_connection,ssh_tunnel} ~/.local/bin/

Make sure `~/.local/bin` is on your `PATH`.

## Tunnel from an iPad (Termius)

`ssh_tunnel` is `ssh -N -L local:localhost:remote host`. Termius does the same with **Port Forwarding**:

1. Add the remote machine (e.g. the Mac mini) as a Host. Use a key from Termius' Keychain and add its public key to the mini's `~/.ssh/authorized_keys`.
2. Enable Remote Login on the mini (System Settings → General → Sharing).
3. In Termius go to **Port Forwarding → New → Local** and set local port `3000`, destination `localhost:3000`, host = the mini.
4. Start the rule, then open `http://localhost:3000` in Safari on the iPad.

Reaching the mini away from home:

- **Tailscale (recommended):** install it on the mini and the iPad, and use the mini's Tailscale name or IP as the Termius host. No router port-forwarding and nothing exposed publicly.
- **Router port-forward of SSH:** possible but exposes SSH to the internet. Use key-only auth, disable password login and use a non-default external port.

Caveats: iOS suspends background apps, so the tunnel can drop when you leave Termius. Running emacs/tmux in a Termius session on the mini survives disconnects, and the tunnel is then only needed for browser previews.

## Development

Scripts are linted with [shellcheck](https://www.shellcheck.net/) on Ubuntu and macOS via GitHub Actions.
