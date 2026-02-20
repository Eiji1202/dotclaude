# dotclaude

Claude Code（`~/.claude/`）の個人設定を管理するリポジトリです。

## 含まれるもの

- `rules/` — 全セッションで適用されるルール（セキュリティ、Git ワークフロー）
- `commands/` — スラッシュコマンド（`/plan`、`/code-review`）
- `plugins/` — インストール済みプラグイン設定
- `settings.json` — パーミッション、hooks 設定

## セットアップ

```bash
git clone git@github.com:/dotclaude.git ~/develop/Claude/dotclaude

ln -s ~/develop/Claude/dotclaude/rules ~/.claude/rules
ln -s ~/develop/Claude/dotclaude/commands ~/.claude/commands
ln -s ~/develop/Claude/dotclaude/plugins ~/.claude/plugins
ln -s ~/develop/Claude/dotclaude/skills ~/.claude/skills
ln -s ~/develop/Claude/dotclaude/settings.json ~/.claude/settings.json
```
