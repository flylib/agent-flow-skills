# agent-flow-skills

Free skills for AgentWorkFlow agents, published as a
[Claude Code plugin marketplace](https://docs.claude.com/en/docs/claude-code/plugin-marketplaces):
the same repository works in AgentWorkFlow and in Claude Code.

## Use it

- **AgentWorkFlow**: Agents → Skills → 市场 → 「添加 AgentWorkFlow 官方市场」, then install a plugin. Its skills are
  imported as versions; tick them on an agent to use them. After this repository changes, sync the
  marketplace and press 「更新」.
- **Claude Code**: `/plugin marketplace add flylib/agent-flow-skills`, then `/plugin install dev-extras@agent-flow-skills`.

## Plugins

| Plugin | Skills |
| --- | --- |
| [dev-extras](plugins/dev-extras) | `release-notes` 发布说明 · `commit-message` 提交信息 |

## Layout

```
.claude-plugin/marketplace.json     the plugin list
plugins/<plugin>/
  .claude-plugin/plugin.json        name, version, description
  skills/<skill>/SKILL.md           one skill: frontmatter (name, description) + instructions
  skills/<skill>/references/…       files the skill points to (templates, examples, scripts)
```

## Add a skill

1. Put it under an existing plugin's `skills/`, or add a plugin folder and list it in
   `marketplace.json`.
2. `SKILL.md` needs `name` (the folder name) and `description` (when to use it). Optional AgentWorkFlow
   metadata:
   ```yaml
   metadata:
     agentflow-requires-tools: [git.diff, fs.read]   # tools the agent needs
   ```
3. Bump `version` in `plugin.json` and the marketplace entry, so installs show the update.

Skills written for Claude Code work too: AgentWorkFlow maps Claude Code tool names to its own and flags
anything it cannot map when the skill is installed.

## License

Apache-2.0
