# Claude Code Agent Skills by migo

- https://github.com/Satjopg/claude-skills

## インストール方法

### 1. マーケットプレイスを登録

```bash
/plugin marketplace add Satjopg/claude-skills
```

### 2. スキルをインストール

```bash
/plugin install pr-review-companion@satjopg-claude-skills
/plugin install structure-review@satjopg-claude-skills
```

## 含まれるスキル

### pr-review-companion

人間がPRを読んでレビューするのを補助するスキルです。merge可否の判定や指摘はせず、PRを読む順番と各箇所で分かる事、壊れた時の影響とそれを防ぐ処理の場所を、20行程度の手引きにまとめます。手引きを出した後は、レビュー中の単発の問いに1〜2行と根拠の `file:line` で答えます。

```bash
/pr-review-companion:pr-review-companion [PR-URL-or-number]
```

レビュー中に「このPRの読み方を教えて」「どこから読めばいい」と伝えても発動します。

### structure-review

動作が正しいPRやbranchに対して、その分け方が後の変更に耐えるかを点検するスキルです。次の5つの観点で見て、ギャップと直す案、ユーザーが決める事(決めごと)を報告します。

1. 概念とモジュールの対応
2. 依存の向きと循環
3. 変更シナリオごとの影響範囲
4. 関数のステートレス性
5. repoの作りとの整合

報告を出したら止まります。直す作業は、決めごとに答えて計画を承認してから始めます。

```bash
/structure-review:structure-review [PR-or-branch] [概念の範囲]
```

作業中に「構造を点検して」「この分け方で合ってるか」と伝えても発動します。
