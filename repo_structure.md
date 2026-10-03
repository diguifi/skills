# Shared AI Skills Repository

For Codex, an entire skills repository can be packaged as one plugin. Installing the plugin makes all its bundled skills available.

## Suggested structure

```text
my-agent-skills/
├── plugin.json
├── skills/
│   ├── plan-creator/
│   │   └── SKILL.md
│   ├── plan-checker/
│   │   └── SKILL.md
│   └── code-review/
│       ├── SKILL.md
│       └── scripts/
└── README.md
```

Each `SKILL.md` contains a name, description, and instructions. A plugin groups the skills into one installable package, and a Git-backed marketplace can distribute it.

See the official documentation for [skill distribution](https://learn.chatgpt.com/docs/build-skills) and [plugin packaging and installation](https://developers.openai.com/plugins/build/plugins).

## Local installation

For personal use, clone the repository and link its individual skill folders into either:

- `~/.agents/skills/` for access across projects.
- `<project>/.agents/skills/` for access within one project.

Codex supports linked skill folders. It discovers available skills and reads their full instructions when needed. See [local skill discovery](https://learn.chatgpt.com/docs/build-skills).

## Use across different agents

Keep each skill in a separate folder with a `SKILL.md` file, and provide installation instructions for each supported agent. The skill content can be reusable, but different agents may require different import mechanisms.
