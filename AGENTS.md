# choosing-models

Agent Skill のリポ。本体は `skills/choosing-models/SKILL.md` の1ファイルだけ。

## 決まり

- 文章は分かりやすい日本語で書く。「版」ではなく「バージョン」と書く。
- モデル名・料金・バージョン番号は SKILL.md に書かない（別名の `haiku`・`sonnet`・`opus`・`fable` だけ）。事実を足すときは公式ドキュメントで確かめ、README のリンクに足す。
- SKILL.md の本文は 500 行・約 5,000 トークン以内。`name` は英小文字・数字・ハイフンのみ、`description` は 1,024 文字以内。
- 例やテストに実在の人・案件・会場の名前を使わない。

## 確かめ方

```bash
python3 - <<'EOF'
import re,pathlib
t=pathlib.Path("skills/choosing-models/SKILL.md").read_text()
fm=re.match(r"^---\n(.*?)\n---\n",t,re.S).group(1)
name=re.search(r"^name: (.*)$",fm,re.M).group(1); desc=re.search(r"^description: (.*)$",fm,re.M).group(1)
assert re.fullmatch(r"[a-z0-9-]{1,64}",name) and name=="choosing-models"
assert 0<len(desc)<=1024 and "<" not in desc and ">" not in desc
assert re.search(r'^  version: "\d+\.\d+\.\d+"$',fm,re.M)
assert t.count("\n")<500 and "版" not in t
print("OK")
EOF
```

## 配り方

`metadata.version` を上げて main に入れる。`.github/workflows/release.yml` が未リリースのバージョンなら `v<バージョン>` のリリースを zip 付きで作る。タグを手で作らない。
