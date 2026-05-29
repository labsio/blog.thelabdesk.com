+++
title = "My homelab, end to end"
date = 2026-05-15T09:00:00+02:00
draft = false
description = "A tour of what's running, what's planned, and why I'm keeping two stacks instead of one."
tags = ["homelab", "proxmox", "kubernetes", "docker", "gitops"]
+++

First post laid out the stack in one sentence. This one walks the whole thing.

## One host, two platforms

Everything sits on a single **Proxmox** host (currently a laptop - real hardware later).

**Docker Compose** handles the simple services - one folder each, reverse-proxied through **Caddy** with Let's Encrypt TLS via Cloudflare DNS-01. Things that just need to run and stay running.

**k3s** is the platform I'm betting on long-term - same TLS via **cert-manager**, state in Git, **Argo CD** reconciling via app-of-apps so the whole cluster comes from one path.

Both stay, on purpose. Compose is the simpler path; k3s is where I practise the patterns I want to be good at. Services migrate when there's a reason. I plan to improve both.

The hostnames look public, but they aren't - DNS resolves to private addresses, reachable only over **Tailscale**. The one real exception is this blog.

## Where it is right now

Running: Caddy, FreshRSS, ChangeDetection, the Proxmox UI proxy, Linkding on k3s. Wildcard TLS on both stacks. Internal-only services on isolated Docker networks - small thing, but the kind of default I want everywhere.

Still test mode. A laptop is not production, even if the patterns are. I run it as if it were the real thing - so the move to real hardware changes only the host.

## What I'm building toward

End state: one command brings the whole thing up on fresh hardware, production-grade for me and my family, secured and backed up by default.

Concrete pieces, roughly in order:

- **Ansible** for host bootstrap - the actual one command.
- **Terraform** for Cloudflare DNS, then Proxmox VMs.
- **Monitoring** - Prometheus + Grafana + Loki, with alerts I'll actually see.
- **Secrets in Git, done right** - External Secrets or SOPS.
- **Restore-tested backups** - Velero for k3s, a script for Docker volumes. Untested backups don't count.
- **Migrations and hardening** - FreshRSS and ChangeDetection to k3s; Docker stays as the simple-path reference.
- **Renovate** - version bumps as PRs, not something to remember.

Lots of plans. Schedule: "as I get to it." Each will get its own post - including what broke.
