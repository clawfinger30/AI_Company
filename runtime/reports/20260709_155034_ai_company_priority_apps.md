# 00_ai_company 汎用AI社員基盤・重点管理アプリ追加レポート

---
tracking_id: TRACK-20260709-155034
app: 00_ai_company
app_path: C:\App_Make\00_ai_company
ai_employee: spec-memory-ai
work_type: docs-update
status: completed
created_at: 2026-07-09T15:50:34+09:00
updated_at: 2026-07-09T15:50:34+09:00
source_conversation_id: conv-20260709-0001
source_request_summary: 00_ai_companyを汎用AI社員基盤として整理し、RakuteRoom、HitoriOyakataMemo、RoomBridgeForX、PintarestRoom、Oyakataを重点管理できるようにする。
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

`00_ai_company` を特定名称に依存しない汎用AI社員基盤として整理し、重点管理アプリ5件を台帳、共通規則、仕様書に明示した。未登録だった Oyakata は部署ルール、専属仕様書メモAI、runtime 保存先を追加した。

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |
| change | `README.md` | 共通基盤説明を汎用AI社員向けに変更し、重点管理アプリを追加 | 入口文書から重点管理対象を確認できるようにするため | ユーザー依頼 |
| change | `SPEC.md` | 共通基盤名を `00_ai_company` として明確化し、重点管理対象と Oyakata を追加 | 共通仕様から特定名称依存を外すため | ユーザー依頼 |
| change | `registry/apps.md` | 表記揺れ対応の重点管理アプリ表と Oyakata 行を追加 | 入力名から正式部署へ対応付けるため | ユーザー依頼 |
| change | `company_rules/employee-handbook.md` | アプリ名照合と重点管理対象の共通規則を追加 | AI社員が対象を混在させないため | ユーザー依頼 |
| change | `app_departments/HitoriOyakataMemo/app-rules.md` | 用途説明の日本語ドメイン表現を一般化 | 共通基盤側の運用文書から対象文字を外すため | ユーザー依頼 |
| add | `app_departments/Oyakata/app-rules.md` | Oyakata の部署ルールを追加 | 重点管理対象として管理可能にするため | ユーザー依頼、`oyakata/README.md`、`composer.json`、`package.json` |
| add | `app_departments/Oyakata/employees/spec-memory-ai.md` | Oyakata 専属仕様書メモAIルールを追加 | 読む順番と出力先を定義するため | 既存部署ルール形式 |
| add | `runtime/spec_changes/pending/Oyakata/README.md` | Oyakata 仕様変更案置き場を追加 | 出力先を明示するため | 既存runtime構成 |
| add | `runtime/reports/Oyakata/README.md` | Oyakata レポート置き場を追加 | 出力先を明示するため | 既存runtime構成 |
| add | `runtime/conversation_logs/2026-07-09.jsonl` | 根拠会話ログを追加 | 仕様影響のある作業を追跡するため | 共通規則 |
| add | `runtime/reports/20260709_155034_ai_company_priority_apps.md` | 本レポートを追加 | 変更追跡を残すため | 共通規則 |
| change | `runtime/reports/20260624_152523_oyakata_current_spec.md` | 過去レポート内の対象文字を Oyakata 表記へ変更 | `00_ai_company` 全体で対象文字が残らないようにするため | ユーザー依頼 |
| change | `runtime/reports/Oyakata/20260625_105212_database_spec.md` | 過去レポート内の対象文字を Oyakata 表記へ変更 | `00_ai_company` 全体で対象文字が残らないようにするため | ユーザー依頼 |

## バージョン

`00_ai_company` 自体に製品バージョン定義はないため、変更前後とも `n/a`。

## Git

`git status --short -- 00_ai_company` は `fatal: not a git repository` で失敗した。既存仕様どおり、Git追跡は不可として記録する。

## 検証

| コマンド | 結果 | 補足 |
| --- | --- | --- |
| `$pattern = [char]0x89aa + [char]0x65b9; rg -n $pattern .` | pass | `00_ai_company` 全体で対象文字を検出しない |
| `rg -n "Oyakata" README.md SPEC.md company_rules registry app_departments templates` | pass | 重点管理アプリ名、HitoriOyakataMemo名、過去変更履歴としてのみ検出 |
| `Test-Path` による重点管理5アプリの部署ルール確認 | pass | 5件すべての部署ルールが存在 |
| `Get-ChildItem app_departments\Oyakata, runtime\spec_changes\pending\Oyakata, runtime\reports\Oyakata` | pass | Oyakata 用ルールと保存先を確認 |

## 生成物

| パス | 作成日時 | 補足 |
| --- | --- | --- |
| `runtime/reports/20260709_155034_ai_company_priority_apps.md` | 2026-07-09T15:50:34+09:00 | 本レポート |
| `runtime/conversation_logs/2026-07-09.jsonl` | 2026-07-09T15:50:34+09:00 | 根拠会話ログ |

## 未コミット差分

Gitリポジトリとして認識されないため取得不可。

## Git管理外ファイル

Gitリポジトリとして認識されないため取得不可。

## 残課題

- 重点管理対象以外を定期監査に含めるかは未定義。
- `00_ai_company` の規則を自動検証する実行ツールは未実装。
