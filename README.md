# multiroom-audio-apt

Signed apt repository with ARMv6 (Raspberry Pi Zero / 1) builds, for Raspberry Pi OS trixie 32-bit, of:

| Package | Upstream | Licence |
|---|---|---|
| `multiroom-endpoint` (scripts, boot chime, stream switching, update agent) | https://github.com/petekaik/multiroom-audio | MIT |
| `multiroom-shairport-sync` (AirPlay 2) | https://github.com/mikebrady/shairport-sync | MIT-style |
| `multiroom-nqptp` (AirPlay 2 timing) | https://github.com/mikebrady/nqptp | GPL-2.0 |
| `multiroom-librespot` (Spotify Connect) | https://github.com/librespot-org/librespot | MIT |

The packages are built **unmodified from the upstream release tag** named in the package version
(`<upstream-version>-<build>`); the corresponding source is the upstream tag. They are built in a
Raspbian trixie armhf chroot under ARMv6 emulation by the `multiroom-audio` project's CI.

Suites: `stable` (what devices should follow) and `canary` (newest builds, test devices only).

## Use

```bash
sudo install -d /usr/share/keyrings
curl -fsSL https://gitpages.morgeweb.com/multiroom-audio-apt/multiroom-archive.gpg | sudo tee /usr/share/keyrings/multiroom-archive.gpg >/dev/null
sudo tee /etc/apt/sources.list.d/multiroom.sources >/dev/null <<'EOF'
Types: deb
URIs: https://gitpages.morgeweb.com/multiroom-audio-apt
Suites: stable
Components: main
Architectures: armhf
Signed-By: /usr/share/keyrings/multiroom-archive.gpg
EOF
sudo apt update && sudo apt install multiroom-endpoint   # also pulls in the three programs below
```

Signing key fingerprint: `FC4E BB55 680B 9538 89FC  45FD D7AB 43C0 6442 791B`.
