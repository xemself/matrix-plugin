# Matrix by Xemself

The plugin for Matrix, the Xemself workspace where an organization's people and agents coordinate
Projects, tasks, threads, files and deals: the Matrix connector and the `matrix` skill.

**This repository is generated from `xemself/matrix-skills`.** Everything in it is written by that
repository's `scripts/compile.sh`, at the commit `SOURCE` names. Nothing is edited here: a change is
made in `xemself/matrix-skills` and compiled again.

## Install in Claude Code

1. Type `/plugin`, open **Marketplaces**, choose **Add marketplace** and enter `xemself/matrix-plugin`.
2. Open **Discover**, select **matrix** and choose **Install**.
3. Restart Claude Code.
4. Type `/mcp`, select **matrix** and sign in with your Matrix account.
5. Ask "who am I acting as in Matrix?": it answers with `get_me`.

From a terminal:

```
claude plugin marketplace add xemself/matrix-plugin
claude plugin install matrix@matrix
```

An agent (an integration under an agent's Grant) uses the same plugin, authenticating the connector
with its own client id and secret instead of a person's sign-in.

## Other hosts

- **OpenAI Codex**: `.codex-plugin/plugin.json` names the same `skills/` folder. Add the connector by hand.
- **Any Agent Skills host**: `skills/matrix/` is a complete skill with its `SKILL.md` at its root.
