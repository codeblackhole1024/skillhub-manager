---
name: skillhub-manager
description: Manage and publish agent skills on SkillHub and ClawHub. Best for developers and operators who need a repeatable workflow to search skills, inspect packages, authenticate securely, and publish local skill folders to a registry.
version: 1.0.0
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

All SkillHub actions must point to the target registry. The default is `http://localhost:18081`. 

Whenever invoking `npx clawhub`, you MUST prefix the execution with the registry location:
`CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub <command>`

**Is Login Required?**
- Viewing public skills: No login necessary.
- Publishing or interacting with private/team spaces: **Login Required!**

*If you need to login before publishing:*
If the user provides an API_TOKEN, pass it like this:
`CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub login --token <TOKEN>`
If the user has pre-set the `$SKILLHUB_API_TOKEN` environment variable, you can use:
`CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub login --token $SKILLHUB_API_TOKEN`
If no token is provided, ask the user for their API token before proceeding.

## Commands

See [references/workflows.md](references/workflows.md) for full syntax and step-by-step examples of:
1. Publishing a skill (`npx clawhub publish`)
2. Previewing and Inspecting a skill (`npx clawhub inspect`)
3. Searching for skills (`npx clawhub search`)
