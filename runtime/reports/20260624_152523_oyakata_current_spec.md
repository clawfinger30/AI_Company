# Oyakata 現行仕様書作成レポート

---
tracking_id: TRACK-20260624-152523
app: Oyakata
app_path: C:\App_Make\00_ai_company
ai_employee: codex
work_type: spec
status: applied
created_at: 2026-06-24T15:25:23+09:00
updated_at: 2026-06-24T15:25:23+09:00
source_conversation_id: current-session-20260624
source_request_summary: Oyakataの現在のコードを00_ai_companyから仕様書化する
version_before: n/a
version_after: n/a
version_change_required: false
version_change_reason: 00_ai_company に製品バージョン定義が存在せず、文書追加のみのため
git:
  available: false
  repo_path: C:\App_Make\00_ai_company
  reason: Gitリポジトリとして認識されないため
approval:
  required: false
  reason: 現行ファイルを根拠とする新規仕様書の作成であり、実行コードや既存仕様の変更を伴わないため
---

## 要約

`00_ai_company` 配下の全社共通規則、AI社員定義、5アプリ部署ルール、テンプレート、台帳、トリガ定義、既存運用レポートを確認し、現行実装を `SPEC.md` に仕様書化した。

Oyakata の現行実体は Markdown 文書によるファイルベースの AI 社員運用基盤であり、常駐プロセス、UI、DB、外部API、Git hook、OSレベルの監視、定期実行コードは含まれないことを明記した。

## 確認対象

- `README.md`
- `company_rules/*.md`
- `ai_employees/*/*.md`
- `app_departments/*/*.md`
- `app_departments/*/employees/*.md`
- `templates/*.md`
- `registry/*.md`
- `runtime/README.md`
- `runtime/triggers/*.md`
- `runtime/spec_changes/*/README.md`
- `runtime/reports/*.md`
- `runtime/reports/*/*.md`

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |
| add | `00_ai_company/SPEC.md` | Oyakata の現行仕様書を追加 | 現行ファイルからシステム全体の仕様を参照可能にするため | ユーザー依頼、`00_ai_company` 配下の現行文書 |
| change | `00_ai_company/README.md` | `SPEC.md` への参照を追加 | 入口文書から仕様書を発見できるようにするため | 新規仕様書 |
| add | `00_ai_company/runtime/reports/20260624_152523_oyakata_current_spec.md` | 作業内容と追跡情報を記録 | 変更追跡ポリシーに従うため | `company_rules/change-tracking-policy.md` |

## バージョン

`00_ai_company` にバージョン定義ファイルは存在しないため、変更前後とも `n/a` とした。

## Git

`C:\App_Make\00_ai_company` は Git リポジトリとして認識されなかったため、ブランチ、コミットID、未コミット差分は取得できない。

## 検証

| コマンド | 結果 | 補足 |
| --- | --- | --- |
| `rg --files 00_ai_company` | pass | 調査対象ファイルを列挙 |
| `rg -n -i "oyakata|仕様書|spec" .` | pass | 既存名称と仕様関連記述を確認 |
| `Get-Content -Raw` による規則・役割・部署・テンプレート・レポート確認 | pass | 現行文書の内容を確認 |
| `git rev-parse --is-inside-work-tree` | pass | Git管理外であることを確認 |
| `SPEC.md` の必須セクションおよび参照整合確認 | pass | 必須11セクション、主要参照ファイル、登録アプリ5件、AI社員4件を確認 |

## 生成物

| パス | 作成日時 | 補足 |
| --- | --- | --- |
| `00_ai_company/SPEC.md` | 2026-06-24T15:25:23+09:00 | Oyakata 現行仕様書 |
| `00_ai_company/runtime/reports/20260624_152523_oyakata_current_spec.md` | 2026-06-24T15:25:23+09:00 | 本レポート |

## 未コミット差分

Git 管理外のため取得できない。

## Git管理外ファイル

`00_ai_company` 全体が Git リポジトリとして認識されないため、個別ファイルの追跡状態は判定できない。

## 残課題

- Oyakata 名称の正式採用範囲は未確定。
- `00_ai_company` のバージョン付与は未確定。
- Git hook、定期実行、ファイル監視、スキーマ検証は未実装。
