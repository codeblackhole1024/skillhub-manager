# SkillHub Manager Workflows

The following are standard operational workflows for managing skills in SkillHub compatible registries.

Use the default clawhub registry unless the user explicitly provides a custom registry URL. For self-hosted registries, prepend `CLAWHUB_REGISTRY=<url>` to the commands below.

## 1. Publishing a Skill (Submit / Upload)
When asked to submit or publish a skill package or directory to SkillHub, use the `publish` command.

1. Ensure the target skill codebase is prepared inside a local folder such as `./my-skill`.
2. Validate whether you already have a working token:
   ```bash
   npx clawhub whoami
   ```
3. If authentication is missing, log in with an API token:
   ```bash
   npx clawhub login --token <TOKEN>
   ```
4. Run the publishing command:
   ```bash
   # Usage: npx clawhub publish <path> --slug <slug> --name <Title> --version <SemVer>
   npx clawhub publish ./my-skill --slug my-skill --name "My Awesome Skill" --version 1.0.0
   ```
5. When targeting a custom or self-hosted registry, add the registry override:
   ```bash
   CLAWHUB_REGISTRY=https://your-registry.example npx clawhub publish ./my-skill --slug my-skill --name "My Awesome Skill" --version 1.0.0
   ```
6. Verify the result with:
   ```bash
   npx clawhub inspect my-skill
   ```

## 2. Previewing a Skill (Inspect)
When a user wants to preview or inspect a specific skill from the remote registry, use the `inspect` command to view its metadata.

```bash
npx clawhub inspect <skill-slug>
```

You can view recently updated skills via exploration:
```bash
npx clawhub explore --limit 10
```

## 3. Searching for a Skill
If a user asks what skills are available regarding a specific topic, use the `search` command.

```bash
npx clawhub search <query>
```

## 4. Practical Notes
- Use explicit `--slug`, `--name`, `--version`, and `--tags` values when publishing so the release is reproducible.
- Keep `README.md` and `SKILL.md` in sync before publishing.
- Prefer `npx clawhub whoami` before any publish attempt so you can fail fast on expired tokens.
- Use `CLAWHUB_REGISTRY` only when the user actually wants a non-default registry.
