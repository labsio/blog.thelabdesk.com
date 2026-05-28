+++
title = "Hello - and what this blog is about"
date = 2026-04-28T09:00:00+02:00
draft = false
description = "First post. What this blog is and what to expect."
tags = ["homelab", "devops"]
+++

First post, so: why this blog exists.

I run a small homelab - one Proxmox host running the services I actually use, and a place to practise tools I want to get good at. The infrastructure lives in Git; the reasoning lives here. Writing forces the lesson to stick: if I can't explain why I chose something, I didn't understand it well enough to choose it.

The stack, in the order I'll cover it: **Proxmox**, **Docker Compose** for the simple stuff, **k3s** as the platform I'm betting on, **Argo CD** for GitOps, **Terraform** for DNS, **Tailscale** holding it together. Posts lean practical - how I set it up, why, and what broke. Less tutorial, more "here's the thing nobody told me."

Some of this is running, some is half-built, some is just a plan. I'll always say which.
