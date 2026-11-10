# ML / LLM 学習リポジトリ

2026年11月9日開始の学習計画、週ごとのチェックリスト、学習メモ、実験成果を管理します。元の `llm_research_learning_plan.md` の学習内容・工数・目標日を引き継いでいます。

採用する基準は**25暦週・約300時間の加速案**です。2027年3月28日に評価・agentの応募用初版、5月2日にLoRA-SFTを含む報告を目指します。週ごとの時間は見積もりで、実績に合わせて次週の作業と現在の完了見込みを調整します。

## 最初に開くファイル

1. [W01のチェックリスト](weekly/W01.md)を開き、完了した項目だけ `[ ]` を `[x]` に変えます。
2. 同じファイルの「今週の実績欄」に、予定時間・実績時間・途中の作業・次週の可処分時間を記入します。
3. 講義や演習のメモは [notes/W01.md](notes/W01.md)、物理題材のメモは [notes/physics_task_seed.md](notes/physics_task_seed.md) に残せます。
4. 週末に [進捗ログ](plan/progress-log.md)へ週次レビューを追記します。

W01-02は講座のブラウザNotebookで進められます。ローカルへのダウンロード・実行は任意です。Markdownの編集だけで学習管理を始められます。

## 構成と役割

```text
llm-learning/
├── README.md
├── AGENTS.md
├── .gitignore
├── .gitattributes
├── plan/
│   ├── master-plan.md
│   ├── progress-log.md
│   └── archive/
│       └── llm_research_learning_plan.md
├── weekly/
│   ├── W01.md
│   └── TEMPLATE.md
├── notes/
│   ├── README.md
│   ├── W01.md
│   └── physics_task_seed.md
├── notebooks/
│   └── README.md
└── experiments/
    └── README.md
```

| ファイル・場所 | 役割 |
| --- | --- |
| [plan/master-plan.md](plan/master-plan.md) | 加速案の基準計画、25週の参照表、講座と受講範囲、段階ごとの通過条件、成果物・応募計画 |
| [weekly/W01.md](weekly/W01.md) | W01の14項目と完了条件、時間別の優先順位、当週の実績・再開位置。タスクのチェック状態はここで管理 |
| [weekly/TEMPLATE.md](weekly/TEMPLATE.md) | 実績と次週の可処分時間を確認してから使う週次ファイルのひな形 |
| [plan/progress-log.md](plan/progress-log.md) | 節目の現在の完了見込み、週次レビュー、計画の変更記録 |
| [notes/](notes/README.md) | 講義・演習のメモと物理題材の整理 |
| [notebooks/](notebooks/README.md) | 自作Notebookなど、保存する必要がある実行成果 |
| [experiments/](experiments/README.md) | 後の評価・agent・SFT実験のコード、設定、小さな結果 |
| [plan/archive/llm_research_learning_plan.md](plan/archive/llm_research_learning_plan.md) | 分割前の元ファイル。内容確認用に変更せず保管 |
| [AGENTS.md](AGENTS.md) | 今後このリポジトリを更新するアシスタント向けの運用ルール |

元ファイルの「今週のタスクリスト」は `weekly/W01.md`、「週次報告のひな形」「節目の進捗」「計画の変更記録」は `plan/progress-log.md` に分けました。その他の学習計画は `plan/master-plan.md` にあります。元ファイル中のチェックボックスは、保管用のコピーとして扱います。

## 毎週の進め方

- **学習中**：当週の `weekly/Wxx.md` にチェックを付けます。途中の項目は未チェックのまま、再開位置と残り作業を書きます。メモやNotebookへのリンクも残します。
- **週末**：当週の実績欄を埋め、進捗ログに振り返りを記録します。完了番号の記録は週次ファイルへの参照でも構いません。
- **次週を組むとき**：実績、未完了作業、次週の可処分時間を使い、優先順位を付け直します。未完了分を機械的に全部上乗せしません。
- **日程が変わったとき**：当初の目標日は残し、進捗ログの「現在の完了見込み」と変更理由を更新します。

タスク番号は `W01-01` のように固定します。持ち越す場合も元の番号を参照し、完了状態は元の週次ファイルで管理します。翌週に同じタスクのチェックボックスを複製しません。通過条件のチェックは基準計画、節目全体のチェックは進捗ログで管理します。

## ローカルで保存する

ローカルの作業場所は `~/works/llm-learning` です。GitHubへの初回commit・pushと、`origin` の設定は済んでいます。

作業前にローカルの状態を確認し、GitHub上の更新を取り込みます。

```sh
cd ~/works/llm-learning
git status
git pull --ff-only
```

進捗を書いた後、変更したファイルをcommit・pushします。次はW01と週次レビューを更新した場合の例です。

```sh
git diff
git add weekly/W01.md notes/W01.md plan/progress-log.md
git commit -m "Record W01 progress"
git push
```

## GitHubと同期する

接続先は [SoChigusa/llm-learning](https://github.com/SoChigusa/llm-learning)、使用するブランチは `main` です。

ChatGPTに週次更新を依頼した場合も、変更はGitHub上のcommitとして保存します。

ローカルで書いた進捗はcommit・pushしてから週次更新を依頼してください。ChatGPTが更新した後は、次のローカル編集を始める前に `git pull --ff-only` で取り込みます。未commitの変更や履歴の分岐で同期が止まる場合は、作業中の変更を保持してから内容を確認します。

## 週次更新を依頼する

GitHub上の更新をcommit/pushした後、対象リポジトリへアクセスできるチャットで、URL・対象週・次週の可処分時間を伝えます。この作成時点で自動更新の設定はしていません。

依頼例：

> 対象リポジトリ：[SoChigusa/llm-learning](https://github.com/SoChigusa/llm-learning)。W01の進捗を確認してください。次週に使える時間は約8時間です。AGENTS.md、基準計画、進捗ログ、W01と関連メモを読み、実績を踏まえてW02を作成し、必要なら現在の完了見込みを更新してください。既存のチェック状態と当初の目標日は保持してください。

リポジトリを更新してもらった後は、ローカルでも同期してから次の記録を始めます。
