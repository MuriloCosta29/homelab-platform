# ADR-0001: Use a dedicated SSH key for the homelab, protected by a passphrase

Date: 2026-09-06
Status: Accepted

## Context

The Macbook was already connecting to the Ubuntu Server before this project started.

State at the time of the decision:

- A single key pair existed on the Mac: `~/.ssh/id_ed25519`.
- That same key was used for GitHub (verified with `ssh -T git@github.com`).
- The key had no passphrase.
- `~/.ssh/config` had one host entry:

```
Host starplatinum
    HostName 192.168.0.50
    User murilo
```

- I set this up about 3 months ago, in ~20 minutes, by pasting commands from an LLM.
  I did not understand what I had configured.
- I still have physical access to the server (keyboard + monitor), so locking myself
  out of SSH is recoverable.

## Decision

Create a new, dedicated key pair for the homelab (`~/.ssh/id_homelab`), protected by
a passphrase, and keep the existing `id_ed25519` untouched as the GitHub key.

Reasons:

- One key per purpose. If the homelab key leaks, my code on GitHub is not exposed.
- A passphrase means a stolen key file alone is not enough to reach the server.
- Rebuilding the access from scratch forces me to understand each step instead of
  inheriting a configuration I cannot explain.

## Discarded Alternatives

**Keep the existing setup as it is.**
Rejected because: I could not explain what it did, a single key served both GitHub
and the server, and it had no passphrase. Working configuration that I do not
understand is technical debt, not an asset.

**Reuse `id_ed25519` for the server but add a passphrase to it.**
Rejected because: it fixes the passphrase problem but keeps the blast radius
problem — one key still unlocks both GitHub and the server.

## Consequences

- I now maintain two key pairs instead of one.
- Every host in `~/.ssh/config` must declare explicitly which key it uses:
  `IdentityFile` (which key) and `IdentitiesOnly yes` (use only that key, do not
  offer the others). Without this the client decides for me and may present the
  GitHub key to the server.
- The passphrase must be unlocked on each use, or cached by `ssh-agent` /
  the macOS Keychain. That is a setup step I did not have before.
- The server's `~/.ssh/authorized_keys` has to be rebuilt with the new public key.
- (expected, not validated) With only two keys I probably will not hit
  `MaxAuthTries` (the server-side limit in `/etc/ssh/sshd_config`, default 6).
  The real reason for `IdentitiesOnly` today is hygiene, not that error.
  To validate in Phase 2.

## Lessons Learned

- SSH is not one thing. A connection has three layers, and they must be diagnosed
  in order: **Network → Service → Authentication**. Most "SSH is broken" problems
  die at the network layer.
- `known_hosts` is not about my key. It stores the *server's* public key so I can
  detect if the machine was swapped. Authentication runs the other way around.
- `ssh-keygen -t ed25519` without `-f` prompts for a path and offers
  `~/.ssh/id_ed25519` as the default — the GitHub key. Pressing Enter and
  confirming the "already exists / Overwrite (y/n)?" prompt would have destroyed
  it. A deleted private key cannot be recovered. Always pass `-f` explicitly. 
- inventory before destruction: list what exists and who depends on it before deleting anything.

