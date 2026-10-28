# LibreChat Skills Repository

自宅サーバー（Docker）の LibreChat で利用する Agent Skills を一元管理するためのプライベートリポジトリ（LibreChat Skill Sync の参照元）です。

## 構成と LibreChat 側の設定

LibreChat 側は `librechat.yaml` の `skillSync` 設定で、このリポジトリの `paths: [skills]` を監視しています。

```
skills-repo/
├── skills/
│   ├── yomiyasu/          # nanaism/yomiyasu の完全ミラー
│   └── <skill-name>/      # 追加スキル
│       └── SKILL.md
├── .github/workflows/
│   └── sync-upstream.yml  # yomiyasu の週次上流同期ワークフロー
├── .gitignore
└── README.md
```

## スキルの追加方法

新しいスキルを追加する場合は、`skills/<skill-name>/SKILL.md` を配置して GitHub へ push するだけで、LibreChat の Skill Sync により取り込まれます。

1. `skills/<skill-name>/` ディレクトリを作成する（`<skill-name>` は `^[a-z0-9][a-z0-9-]*$` に適合する名前）
2. `skills/<skill-name>/SKILL.md`（および必要に応じた `references/`・`assets/` 等）を配置する
3. コミットして `main` ブランチへ push する

## 同梱スキル: `yomiyasu`

- 上流リポジトリ（[nanaism/yomiyasu](https://github.com/nanaism/yomiyasu)）の `skills/yomiyasu` を改変なしの完全ミラーとして配置しています。
- `.github/workflows/sync-upstream.yml` により、GitHub Actions が毎週月曜（`0 3 * * 1` UTC）および手動実行（`workflow_dispatch`）で上流の `skills/yomiyasu` に自動追従します。
- モデル自動選択時のカタログでは説明文が切り詰められるが、`$` による手動呼び出しには影響しない。
- **任意機能の前提（`skills/yomiyasu/scripts/`）**: 同梱の検査スクリプト群（`yomiyasu_lint.py` / `yomiyasu_check.py` / `yomiyasu_diff.py` 等）を実行する場合は `python3` が必要です（Python 3 標準ライブラリのみで動作し、`pyyaml` 等の外部パッケージ依存はありません）。
- 同梱している外部スキルの出典・ライセンス一覧は [THIRD_PARTY_NOTICES.md](./THIRD_PARTY_NOTICES.md) を参照してください。
