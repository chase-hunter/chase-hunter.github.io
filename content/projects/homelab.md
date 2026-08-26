---
title: "Homelab: Self-Hosted Infrastructure on Hyper-V"
date: 2026-08-26
url: /thoughts/homelab/
author: Chase Hunter
description: Homelab overview.
cover:
    image: " "
    alt: " "
showToc: false
disableAnchoredHeadings: false
---

## Overview

I run a small homelab on Hyper-V that mirrors a lot of what I do professionally as an IT specialist: virtualization, DNS management, network security, and service reliability, but on hardware I fully control. 

It's where I test ideas before I'd ever bring them near a client environment, and it's taught me more about the "why" behind enterprise tooling than any single client engagement has.

## Stack

- Hypervisor: Hyper-V, hosting all services as isolated VMs

- Pi-hole: Network-wide DNS filtering, with a custom Local Domain Fallback configured using a .home.lan suffix so internal hosts resolve cleanly without hitting public DNS

- Homebridge: Bridges non-HomeKit smart home devices into Apple's ecosystem

- AzerothCore: A private World of Warcraft server, mostly for tinkering with game server administration and database management outside of a "serious" production context

- Cloudflare Zero Trust (ZTNA): Secure remote access into the lab without exposing anything directly to the internet

## Why this setup?

Running Pi-hole with a proper local domain suffix instead of just relying on IP addresses was a deliberate choice. It's a small thing, but it's the same kind of decision I make for clients when I'm setting up split-DNS or internal domain resolution. Doing it at home first meant I understood the tradeoffs before I ever touched a client's DNS config.

Cloudflare ZTNA plays a similar role. Instead of punching holes in my firewall or running a traditional VPN, I get access into the lab the same way I'd want a client's remote workforce to access internal resources: authenticated, tunneled, and without a public-facing attack surface.

## What I've learned

- How Pi-hole's local DNS record handling actually behaves versus how the documentation describes it

- Practical Hyper-V VM management outside of a corporate vCenter/System Center context

- Where Cloudflare's tunnel model breaks down and where it genuinely simplifies things over a traditional VPN