# Agent Skills

Reusable AI agent skills packaged as one portable plugin. Installing the plugin makes its bundled skills available together.

## Repository layout

```text
.
|-- plugin.json
|-- .agents/plugins/marketplace.json
|-- skills/
|   `-- plan-creator/
|       |-- SKILL.md
|       `-- agents/openai.yaml
|-- README.md
|-- repo_structure.md
`-- plan_skill_prompt.md
```

`repo_structure.md` is the original packaging guide. `plan_skill_prompt.md` is the original installation prompt; its two embedded files are bundled under `skills/plan-creator/`.

## Install on another machine

After these files have been committed and pushed to GitHub, register the marketplace:

```sh
codex plugin marketplace add diguifi/skills
```

In the desktop app, restart the app, open the Plugins Directory, select **Diguifi Skills**, and install **Agent Skills**. Start a new session after installation.

Codex CLI versions that provide `codex plugin add` also support:

```sh
codex plugin add agent-skills@diguifi-skills
```

For local development, clone the repository and register it from the repository root:

```sh
git clone https://github.com/diguifi/skills.git
cd skills
codex plugin marketplace add .
```

The marketplace points at `./`, relative to its repository root, so it works regardless of the checkout location. Install the plugin through the desktop app or the CLI command above. Installed plugins use a cached copy; restart the app and refresh or reinstall the plugin after updates.

See the official [plugin packaging and marketplace documentation](https://developers.openai.com/plugins/build/plugins).

## First skill: plan-creator

Creates Markdown plans and reviews them with fresh subagents, one at a time. Automatic invocation is enabled. The default review limit is five attempts, with an early stop after a completed review that makes no edits. You can override the limit or skip reviews.

Example requests:

- `Create a plan for adding password reset.`
- `plan migration.md: migrate the database; use a maximum of 3 reviews.`
- `Create a release plan; skip automatic reviews.`
- `review migration.md`

Independent reviews require fresh-context subagent tools. When those tools are unavailable, the skill keeps the draft and reports that independent reviews could not run.

## Use the skill without a plugin

For an agent that supports `SKILL.md` discovery, copy or link `skills/plan-creator/` into its supported skills directory. For Codex, use `~/.agents/skills/plan-creator/` for user-wide discovery or `<project>/.agents/skills/plan-creator/` for a single project. Restart or start a new session to refresh discovery. Other agents may use different installation mechanisms.

## Add more skills

Create `skills/<skill-name>/SKILL.md` with YAML frontmatter containing `name` and `description`, followed by the skill instructions. Add metadata or supporting resources only as needed. The portable plugin discovers skills under `skills/`, so additional skills do not need separate manifest entries. Update the plugin version when publishing a new release.
