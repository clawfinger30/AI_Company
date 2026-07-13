# 共通変更追跡ポリシー追加レポート

---
tracking_id: TRACK-20260623-113003
app: 00_ai_company
app_path: C:\App_Make\00_ai_company
ai_employee: codex
work_type: docs
status: applied
created_at: 2026-06-23T11:30:03+09:00
updated_at: 2026-06-23T11:30:03+09:00
source_conversation_id: current-session-20260623
source_request_summary: 共通のAI社員仕様で、追加日、バージョン、Gitなどを詳細に追跡できるようにする。
version_before: n/a
version_after: n/a
git:
  available: false
  reason: "00_ai_company is not a git repository"
---

## 要約

全AI社員共通の変更追跡仕様として `company_rules/change-tracking-policy.md` を追加した。仕様変更案、仕様書、作業レポート、リリースレポートに、追加日、更新日、バージョン、Git、変更ファイル、検証、生成物、未コミット差分を残す運用にした。

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |
| add | `company_rules/change-tracking-policy.md` | 共通の追跡メタデータ仕様を追加 | 全AI社員で同じ追跡形式を使うため | ユーザー依頼 |
| change | `company_rules/employee-handbook.md` | 読む順番に変更追跡ポリシーを追加 | 全AI社員が作業前に読むようにするため | 共通運用 |
| change | `company_rules/history-policy.md` | 変更履歴項目に版数、Git、検証、生成物を追加 | 変更履歴を後から復元できる粒度にするため | 共通運用 |
| change | `ai_employees/spec-memory-ai/spec-change-format.md` | 仕様変更案のfront matterと本文セクションを拡張 | 仕様変更案に追跡情報を必ず残すため | 共通運用 |
| change | `ai_employees/spec-memory-ai/workflow.md` | バージョン/Git/対象ファイル確認を処理順に追加 | 仕様メモAIの実行手順に組み込むため | 共通運用 |
| change | `ai_employees/release-manager-ai/role.md` | リリース管理AIの追跡責務を追加 | リリース前後の履歴を詳細に残すため | 共通運用 |
| change | `templates/spec-template.md` | 仕様書テンプレートに追跡ID、版数、Git、変更履歴表を追加 | 新規仕様書で追跡欄を標準化するため | 共通運用 |
| change | `templates/spec-change-proposal-template.md` | 仕様変更案テンプレートに追跡欄を追加 | 新規変更案で追跡欄を標準化するため | 共通運用 |
| add | `templates/change-tracking-report-template.md` | 作業完了レポート用テンプレートを追加 | Git/版数/検証/生成物を残すため | 共通運用 |
| change | `templates/app-rules-template.md` | 部署ルールテンプレートに追跡ポリシー参照を追加 | 新規部署でも共通追跡を読むため | 共通運用 |
| change | `app_departments/*/app-rules.md` | 既存部署ルールに追跡ポリシー参照を追加 | 既存アプリ部署にも共通追跡を適用するため | 共通運用 |
| change | `README.md` | 基本方針に追跡ポリシーを追加 | 入口文書から追跡方針を確認できるようにするため | 共通運用 |
| change | `runtime/reports/README.md` | レポート必須項目を追記 | レポート作成時の記録漏れを防ぐため | 共通運用 |

## バージョン

`00_ai_company` 自体にはアプリ版数がないため、`version_before` と `version_after` は `n/a` とした。

## Git

`C:\App_Make\00_ai_company` は Git リポジトリではないため、コミットIDは記録できない。

## 検証

| コマンド | 結果 | 補足 |
| --- | --- | --- |
| `rg -n "change-tracking-policy|tracking_id|version_before|commit_before|Git管理外|変更追跡|追加日時|Git リポジトリ" ...` | pass | 共通ルール、テンプレート、各部署ルールへの反映を確認 |

## 生成物

| パス | 作成日時 | 補足 |
| --- | --- | --- |
| `00_ai_company/runtime/reports/20260623_113003_common_change_tracking_policy.md` | 2026-06-23T11:30:03+09:00 | 本レポート |

## 未コミット差分

`00_ai_company` は Git 管理外のため未コミット差分は取得不可。

## 残課題

既存の過去レポートや過去仕様変更案には、新しい追跡メタデータは自動では付与していない。必要な場合は個別に追記する。
