# Week 0 – Orientation and environment (2–6 Nov 2026)

## What I built
- WSL Ubuntu on Surface Pro 11 (ARM64), least-privilege user with sudo
- uv 0.13.6 (installer reviewed before running), Python 3.13.18, Git 2.53
- VS Code connected to WSL; AI completions off for Phase 1
- GitHub hardened: 2FA, passkey, Ed25519 SSH key for auth and signing
- First signed, verified commit: capstone problem statement

## What broke and how I fixed it
- 

## Decisions and why
- 

## What I'd tell a security architect starting this
-# Week 0 – Orientation and environment (2–6 Nov 2026)

## What I built
- WSL Ubuntu 26.04 on a Surface Pro 11 (Snapdragon X, ARM64), with a
  least-privilege user and sudo
- uv 0.13.6 (installer reviewed before running) and Python 3.13.18
- Git 2.53 and VS Code connected to WSL, with AI completions switched off
  for Phase 1
- GitHub hardened: authenticator-app 2FA, passkey, recovery codes in a
  password manager, private no-reply email
- Ed25519 SSH key with a passphrase, registered for authentication and
  commit signing
- First signed, verified commit: the capstone problem statement
- This notes repo, with a threat register and weekly log

## What broke and how I fixed it
- **WSL "Catastrophic failure" (E_UNEXPECTED).** A partial earlier install
  plus an outdated engine. Fixed with `wsl --shutdown`, `wsl --update` and a
  restart.
- **Ubuntu logged me in as root.** User creation had failed. I created a
  normal user, added it to sudo, and set it as the default in
  `/etc/wsl.conf`. I first appended the setting twice with `>>`, then
  rewrote the file cleanly with `>`.
- **SSH key prompt.** I typed a name at the "save to file" prompt. That can
  put a private key inside a repo folder, one `git add .` away from being
  public. I located the key, confirmed it sat in `~/.ssh` with `600`
  permissions, and checked its fingerprint.
- **Smaller slips.** A Windows command typed inside Linux, a command typed
  into the editor instead of the terminal, running a script before saving
  it, and a placeholder email in my Git config. Each was caught by reading
  the output carefully.

## Decisions and why
- **Linux (WSL), not native Windows.** AI tooling, Docker and isolation work
  later in the programme all assume Linux.
- **A normal user, not root.** Least privilege applies to my own machine,
  and later to the agents I build.
- **Passphrase on the SSH key.** A stolen laptop should not mean a stolen
  GitHub identity.
- **Signed commits and a no-reply email.** Provenance for every change, and
  no real email address in public history.
- **Verified GitHub's host fingerprint before trusting it.** Trust on first
  use only works if the first use is checked.
- **AI coding assistants off until Week 5.** I need to be able to write the
  code myself before I can judge an AI's version of it.
- **Docker deferred to Week 3.** On ARM, install it just before it's needed.

## What I'd tell a security architect starting this
- Your instincts transfer directly: identity, permissions, keys and supply
  chain are where most of the set-up risk sits.
- Read the prompt and the output before typing the next command. Most of my
  mistakes came from moving faster than I was reading.
- Treat your own laptop like a production system from day one. The habits
  you set now are the habits your agents will inherit.