# dev-skills (Coding Agents Skills)

このディレクトリは、**コーディングエージェント（OpenCode / Antigravity / Claude Code 等）用のスキル置き場**です。

> [!WARNING]
> **`librechat.yaml` の `skillSync` 設定（`paths`）に `dev-skills` を追加しないでください。**
> LibreChat 側は `paths: [skills]` のみを監視しており、`dev-skills/` 配下は LibreChat には取り込まれません。`paths` に `dev-skills` を追加すると、コーディング・開発特化のスキルが LibreChat の一般チャット用スキルカタログを汚染してしまいます。

## ルールと構成

- 各スキルは `dev-skills/<name>/SKILL.md` の形式で配置します（`dev-skills/` 直下には `SKILL.md` を置きません）。
- **ライセンス**: 再配布可能なオープンソースライセンス（MIT / Apache-2.0 等）のスキルのみを配置してください（Source-Available や再配布不可のものは置かないこと）。

```text
dev-skills/
├── README.md
└── <skill-name>/
    ├── SKILL.md
    └── LICENSE
```

## 各コーディングエージェントへの配置方法

- **TODO**: 各エージェント（OpenCode / Antigravity / Claude Code 等）のローカルスキル参照パス・シンボリックリンク配置・設定方法は、各ツールの公式ドキュメントを確認して追記する。
