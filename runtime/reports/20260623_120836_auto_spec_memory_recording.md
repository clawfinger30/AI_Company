# 仕様書メモAI 自動記録ルール追加レポート

---
tracking_id: TRACK-20260623-120836
app: 00_ai_company
app_path: C:\App_Make\00_ai_company
ai_employee: codex
work_type: docs
status: applied
created_at: 2026-06-23T12:08:36+09:00
updated_at: 2026-06-23T12:08:36+09:00
source_conversation_id: current-session-20260623
source_request_summary: 仕様書メモは自動で記録するようにしたい。
version_before: n/a
version_after: n/a
git:
  available: false
  reason: "00_ai_company is not a git repository"
---

## 要約

仕様書メモAIの運用を、明示依頼がある場合だけでなく、仕様影響がある会話、調査、コード変更を自動記録する方針に変更した。

自動記録は会話ログ、仕様変更案、差分レポートの作成までとし、仕様書本文への自動反映は行わない。

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |
| change | `ai_employees/spec-memory-ai/role.md` | 自動記録責務と完了条件を追加 | 仕様影響がある作業を明示依頼なしで記録するため | ユーザー依頼 |
| change | `ai_employees/spec-memory-ai/workflow.md` | 自動記録の対象、対象外、出力先、仕様書本文への反映範囲を追加 | 自動記録と自動反映を分けるため | ユーザー依頼 |
| change | `company_rules/employee-handbook.md` | 出力ルールに自動記録方針を追加 | 全AI社員の共通運用にするため | ユーザー依頼 |
| change | `runtime/triggers/manual.md` | 手動トリガを補助ルートとして再定義 | 手動依頼がなくても記録する運用に合わせるため | ユーザー依頼 |
| change | `runtime/triggers/file-watch.md` | 外部監視なしでもAI作業中の変更を自動記録する旨を追加 | ファイル監視未導入でも運用できるようにするため | ユーザー依頼 |
| change | `runtime/triggers/pre-commit.md` | Git hook未導入とAI作業時の自動記録を区別 | 各アプリGit運用と仕様記録を混同しないため | ユーザー依頼 |
| change | `runtime/triggers/schedule.md` | 定期監査未導入とAI作業時の自動記録を区別 | スケジューラー未導入でも自動記録方針を明確にするため | ユーザー依頼 |
| change | `runtime/README.md` | runtime配下に自動記録の出力を保存する旨を追加 | 保存先の意味を明確にするため | ユーザー依頼 |

## バージョン

`00_ai_company` 自体にはアプリ版数がないため、`version_before` と `version_after` は `n/a` とした。

## Git

`00_ai_company` は Git 管理対象外として扱う。各アプリのGit運用とは分離する。

## 検証

| コマンド | 結果 | 補足 |
| --- | --- | --- |
| `rg -n "自動記録|明示依頼なし|仕様書本文への反映|Git hook|手動トリガ|外部のファイル監視" ...` | pass | 関連文書への反映を確認 |

## 残課題

OSレベルのファイル監視、Git hook、スケジューラーは未実装。現時点の自動記録は、AI社員が仕様影響のある作業を扱ったときに自動で記録する運用ルールとして定義した。
