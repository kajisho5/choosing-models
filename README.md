# choosing-models

AI エージェントが、作業に合う Claude のモデル（haiku・sonnet・opus・fable）と考える深さ（effort）を選び、下請けのエージェントに振り分けるための Agent Skill。

今のモデルでは難しいと分かったときは、目に見える事実（2回失敗した、調べる範囲が広がるだけ、など）を根拠に正直に伝え、別のモデルへの切り替えを勧めます。単純作業が続くときは、安いモデルへの切り替えも勧めます。

## 入れ方

`skills/choosing-models/` フォルダを、使うツールのスキル置き場にコピーします。

- Claude Code（自分用）：`~/.claude/skills/choosing-models/`
- Claude Code（リポ用）：`.claude/skills/choosing-models/`
- claude.ai：スキルの設定から `choosing-models` フォルダを zip にして追加

## 中身

- `skills/choosing-models/SKILL.md`：スキル本体

モデル名・料金は変わるので、スキル本体には別名（`opus` など）だけを書いています。正確な値は使うたびに公式ドキュメントで確かめる決まりです。

- [Claude Code のモデル設定](https://code.claude.com/docs/en/model-config)
- [Claude Code のモデルと effort の選び方（公式ブログ）](https://claude.com/blog/claude-model-and-effort-level-in-claude-code)

## リリース

`skills/choosing-models/SKILL.md` の `metadata.version` を上げて main に入れると、まだそのバージョンのリリースがなければ GitHub Actions が自動でリリース（zip 付き）を作ります。
