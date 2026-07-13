# 00_ai_company AGENTS入口・ai-company skill追加レポート

---
tracking_id: TRACK-20260709-161428
app: 00_ai_company
app_path: C:\App_Make
ai_employee: spec-memory-ai
work_type: tooling-docs
status: completed
created_at: 2026-07-09T16:14:28+09:00
updated_at: 2026-07-09T16:14:28+09:00
source_conversation_id: conv-20260709-0002
source_request_summary: AGENTS.mdを短く追加し、00_ai_companyをskill化する。
version_before: n/a
version_after: n/a
git:
  available: false
  repo_path: C:\App_Make
  branch: unavailable
  commit_before: unavailable
  commit_after: unavailable
  status_before: "git status failed: not a git repository"
  status_after: "git status failed: not a git repository"
---

## 要約

`C:\App_Make\AGENTS.md` を短い入口ルールとして追加し、`00_ai_company` を必要時だけ読むための repo-scoped skill `ai-company` を `.agents/skills/ai-company/` に追加した。

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |
| add | `AGENTS.md` | `00_ai_company` の使用条件、重点管理アプリ、最小読込方針を追加 | 毎回大量の文書を読ませないため | ユーザー依頼 |
| add | `.agents/skills/ai-company/SKILL.md` | `00_ai_company` の最小ルーティング、起動条件、完了ルールを定義 | progressive disclosure で必要時だけ詳細を読むため | ユーザー依頼、Codex skill形式 |
| add | `.agents/skills/ai-company/agents/openai.yaml` | skill UI metadataを追加 | skill一覧で判別しやすくするため | skill-creator |
| change | `00_ai_company/runtime/conversation_logs/2026-07-09.jsonl` | 根拠会話ログを追記 | 仕様影響のある作業を追跡するため | 共通規則 |
| add | `00_ai_company/runtime/reports/20260709_161428_agents_skill_entrypoint.md` | 本レポートを追加 | 変更追跡を残すため | 共通規則 |

## バージョン

`00_ai_company` 自体に製品バージョン定義はないため、変更前後とも `n/a`。

## Git

`C:\App_Make` は Git リポジトリとして認識されないため取得不可。

## 検証

| コマンド | 結果 | 補足 |
| --- | --- | --- |
| `python ...\quick_validate.py C:\App_Make\.agents\skills\ai-company` | skipped | `ModuleNotFoundError: No module named 'yaml'` のため公式検証スクリプトは実行不可 |
| Python手動frontmatter検証 | pass | `name: ai-company`、`description`、frontmatter区切りを確認 |
| `rg -n 'TODO\|Use -company\|...' AGENTS.md .agents\skills\ai-company` | pass | TODO、誤ったdefault prompt、対象文字がないことを確認 |
| ファイルサイズ確認 | pass | `AGENTS.md` 543 bytes、`SKILL.md` 2080 bytes |

## 生成物

| パス | 作成日時 | 補足 |
| --- | --- | --- |
| `AGENTS.md` | 2026-07-09T16:14:28+09:00 | 短い入口ルール |
| `.agents/skills/ai-company/SKILL.md` | 2026-07-09T16:14:28+09:00 | repo-scoped skill |
| `.agents/skills/ai-company/agents/openai.yaml` | 2026-07-09T16:14:28+09:00 | UI metadata |

## 未コミット差分

Gitリポジトリとして認識されないため取得不可。

## 残課題

- 追加した `AGENTS.md` と repo skill は、通常は次回の Codex セッション開始時に読み込まれる。
- 公式 skill validator は Python環境に `PyYAML` がないため未実行。
