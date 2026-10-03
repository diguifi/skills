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

## Add more skills

Create `skills/<skill-name>/SKILL.md` with YAML frontmatter containing `name` and `description`, followed by the skill instructions. Add metadata or supporting resources only as needed. The portable plugin discovers skills under `skills/`, so additional skills do not need separate manifest entries. Update the plugin version when publishing a new release.
