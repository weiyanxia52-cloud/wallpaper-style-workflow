# Host compatibility

The canonical package is the folder containing `SKILL.md`. Supporting agents should read the same source rather than maintaining independent copies.

## Portable core

Every host needs:

- `SKILL.md`;
- the `references/` directory;
- access to the user's reference images and generated artifacts;
- an image generator for media creation, or the ability to return a portable prompt package;
- a video generator with image-to-video support for dynamic wallpaper creation.

`agents/openai.yaml` is optional UI metadata for Codex-compatible hosts. Other hosts may ignore it.

## Tool discovery

At the start of media work:

1. discover the host's current image, video, file, and media-inspection tools;
2. read their current instructions and model limits;
3. map the workflow's capability requirements to available tools;
4. tell the user when a capability is unavailable or requires an external project/import step.

Do not embed one host's MCP tool names into the portable workflow.

## Installation principle

Keep one canonical source and prefer symbolic links or the host's official skill importer. Do not copy divergent versions unless a host cannot follow links. Preserve the complete tree, including `references/`.

After installation, verify:

- the host entrypoint resolves to the canonical `SKILL.md`;
- the frontmatter `name` is `wallpaper-style-workflow`;
- every linked reference exists;
- no host has two active entries pointing to the same source;
- the source package remains intact;
- no private or credential directory was copied.

When a host does not have a documented Skill directory, deliver a portable package and a host-specific import note rather than inventing an installation path.

## Known host entrypoints

Verify that the host root already exists before installing. Current supported conventions include:

| Host | Skill entrypoint |
|---|---|
| Codex and compatible general agents | `~/.agents/skills/<skill-name>` |
| Claude Code | `~/.claude/skills/<skill-name>` |
| WorkBuddy | `~/.workbuddy/skills/<skill-name>` |
| WorkBuddy AI desktop builds that use a separate root | `~/.workbuddy-ai/skills/<skill-name>` |
| DeepSeek Harness | `~/.dsh/skills/<skill-name>` when the existing installation already uses that directory |
| Doubao desktop Agent Mode | `~/Library/Application Support/Doubao/Default/.doubao/agent_mode/workspace/.user_skills/<skill-name>` when that existing user-skill directory is present |

Use these as verified local conventions, not universal paths for every operating system or release. Prefer the host's official importer when it exposes one. After linking a new skill, restart or refresh the host and confirm that the skill appears before claiming runtime discovery.
