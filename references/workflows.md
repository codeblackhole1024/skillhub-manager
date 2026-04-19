# SkillHub Manager Workflows

The following are standard operational workflows for managing operations in a SkillHub Instance. You must always prepend `CLAWHUB_REGISTRY=http://localhost:18081` to route the OpenClaw commands to the user's specific backend.

## 1. Publishing a Skill (Submit / Upload)
When asked to *submit* or *publish* a skill package or directory to SkillHub, use the `publish` command.

1. Ensure you have the target skill codebase prepared inside a local folder (e.g., `./my-skill`).
2. Log into the registry using the API Token:
   ```bash
   CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub login --token <TOKEN>
   ```
3. Run the publishing command:
   ```bash
   # Usage: npx clawhub publish <path> --slug <slug> --name <Title> --version <SemVer>
   CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub publish ./my-skill --slug my-skill --name "My Awesome Skill" --version 1.0.0
   ```
   *Note: For team spaces, use `--slug team-space--my-skill`*

## 2. Previewing a Skill (Inspect)
When a user wants to preview or inspect a specific skill from the remote registry, use the `inspect` command to view its metadata.

```bash
CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub inspect <skill-slug>
```

You can view the latest skills available on the hub via exploration:
```bash
CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub explore --limit 10
```

## 3. Searching for a Skill
If a user asks what skills are available regarding a specific topic, use the `search` command.

```bash
CLAWHUB_REGISTRY=http://localhost:18081 npx clawhub search <query> --limit 5
```
