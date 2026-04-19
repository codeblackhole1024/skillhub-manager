---
name: skillhub-manager
description: Manage and publish agent skills on SkillHub and ClawHub. Best for developers and operators who need a repeatable workflow to search skills, inspect packages, authenticate securely, and publish local skill folders to a registry.
version: 1.0.1
author: Agent Skill Master
license: MIT
metadata:
  hermes:
    tags: [skillhub, clawhub, skills, publishing, registry, authentication]
---

# SkillHub Manager

This skill gives you the ability to interact with a SkillHub ecosystem using the `clawhub` CLI. It supports previewing available skills and uploading/publishing new skills securely to the server.

## Overview

SkillHub instances host agents, profiles, and skills securely. As an AI Agent, you might be asked to publish a local folder as a skill, or to preview an existing skill to see what it does.

No need to write raw HTTP REST requests; SkillHub provides full compatibility with the `npx clawhub` toolchain.

## General Authentication & Environment

All SkillHub actions must point to the intended registry.

Use the default clawhub CLI target when the user does not specify a custom registry. Only set `CLAWHUB_REGISTRY` or pass `--registry <url>` when targeting a non-default or self-hosted SkillHub instance.

Examples:
- default registry: `npx clawhub <command>`
- custom registry: `CLAWHUB_REGISTRY=https://your-registry.example npx clawhub <command>`

**Is Login Required?**
- Viewing public skills: usually no login required.
- Publishing or interacting with private/team spaces: login required.

*If you need to login before publishing:*
- explicit token: `npx clawhub login --token <TOKEN>`
- custom registry plus token: `CLAWHUB_REGISTRY=https://your-registry.example npx clawhub login --token <TOKEN>`
- if the environment already provides `SKILLHUB_API_TOKEN`, `CLAWHUB_API_TOKEN`, or `CLAWHUB_TOKEN`, validate first with `npx clawhub whoami`
- if no working token is available, ask the user for one before proceeding

## Commands

See [references/workflows.md](references/workflows.md) for full syntax and step-by-step examples of:
1. Publishing a skill (`npx clawhub publish`)
2. Previewing and Inspecting a skill (`npx clawhub inspect`)
3. Searching for skills (`npx clawhub search`)
