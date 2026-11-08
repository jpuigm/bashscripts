# Roadmap

Ideas for scripts to create and maintain. All should work on Linux (Ubuntu) and macOS using bash 3.2+ and tools that ship on both. GNU vs BSD differences (`sed`, `date`, `stat`, `readlink`) are handled in a shared helper.

## Shared foundation
- [ ] `lib/common.sh`: `is_mac`, `is_linux`, portable `sed -i` / `stat` wrappers, `die`. Sourced by the other scripts.
- [ ] Move scripts under `bin/` and make the shellcheck workflow cover everything there.

## Git and repo workflow
- [ ] `git-sync-all`: walk `~/dev/src/github.com/*/*`, `git fetch --prune`, report dirty / ahead / behind repos.
- [ ] `git-clean-branches`: delete local branches merged into the default branch (dry-run by default).
- [ ] `git-clone-to`: `git-clone-to user/repo` clones into `~/dev/src/github.com/user/repo`.
- [ ] `git-whoami-check`: show the identity (name, email, signing key) a repo will commit with.

## Machine setup and portability
- [ ] `bootstrap`: install baseline tools via `apt` or `brew` from one package list.
- [ ] `dotfiles-link`: symlink dotfiles into `$HOME`, backing up existing files.
- [ ] `doctor`: check expected tools, versions and PATH entries.
- [ ] `mini-setup`: configure and verify the Mac mini as an always-on SSH server: `pmset` no-sleep / wake-for-network / autorestart, Remote Login enabled, Tailscale running with MagicDNS, and sshd keepalive settings. Print a client-side `~/.ssh/config` alias snippet (`ServerAliveInterval`, etc.).

## Everyday system utilities
- [ ] `backup-home`: incremental rsync backup with excludes and dry-run.
- [ ] `disk-hogs`: largest directories under a path, portable across GNU/BSD `du`.
- [ ] `port-who`: which process listens on a port (`lsof -i :PORT`).
- [ ] `clean-caches`: clear package manager, Docker and build caches; list first.
- [ ] `extract`: unpack any archive type (zip, tar.gz, tar.xz, 7z).

## Quality of life
- [ ] `clip`: `pbcopy`/`pbpaste` on macOS, `xclip`/`wl-copy` on Linux, so `... | clip` works everywhere.
- [ ] `notify`: desktop notification after long commands (`osascript` / `notify-send`).
- [ ] `tmpnote`: open a dated scratch note in `$EDITOR`.
- [ ] `mkcd`, `serve`: possibly better as shell functions than scripts.

## Suggested order
1. `lib/common.sh`
2. `git-sync-all`
3. `clip` and `notify`
4. `bootstrap`

## Done
- [x] `setup_ssh_keys`
- [x] `test_ssh_connection`
- [x] `ssh_tunnel`
