# XserverVPS VPS運用AIルール作成レポート

---
tracking_id: TRACK-20260702-140346
app: XserverVPS
app_path: infra/ and ssh alias xserver-vps-wg
ai_employee: vps-operator-ai
work_type: docs
status: applied
created_at: 2026-07-02T14:03:46+09:00
updated_at: 2026-07-02T14:03:46+09:00
source_conversation_id: current-session-20260702
source_request_summary: Xserver VPSへVSCode/SSHで接続して操作できるAI社員の職種定義、部署ルール、コマンド方針、承認方針、作業ログ・検証・ロールバック方針を作成する
version_before: n/a
version_after: n/a
git:
  available: false
  repo_path: C:\App_Make
  reason: C:\App_Make was not recognized as a git repository by git status
---

## 要約

Xserver VPSをVSCode Remote-SSH経由で扱うためのAI社員と部署ルールを追加した。

実VPSへの接続、設定変更、デプロイ、再起動、認証情報確認は行っていない。

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |
| add | `00_ai_company/ai_employees/vps-operator-ai/role.md` | VPS運用AIの職種定義を追加 | 新しいAI社員の責務と禁止事項を定義するため | ユーザー依頼 |
| add | `00_ai_company/ai_employees/vps-operator-ai/workflow.md` | VPS運用AIの作業順序を追加 | 調査、承認、変更、記録の流れを明確化するため | ユーザー依頼 |
| add | `00_ai_company/app_departments/XserverVPS/app-rules.md` | XserverVPS部署ルールを追加 | VPS固有の対象範囲と参照ルールを定義するため | ユーザー依頼 |
| add | `00_ai_company/app_departments/XserverVPS/employees/vps-operator-ai.md` | XserverVPS担当ルールを追加 | 対象部署でのVPS運用AIの読み順と承認対象を定義するため | ユーザー依頼 |
| add | `00_ai_company/app_departments/XserverVPS/command-policy.md` | 許可・承認・禁止コマンド方針を追加 | 危険操作を分離するため | ユーザー依頼 |
| add | `00_ai_company/app_departments/XserverVPS/approval-policy.md` | 承認が必要な操作一覧を追加 | 本番環境操作の承認境界を明確化するため | ユーザー依頼 |
| add | `00_ai_company/app_departments/XserverVPS/log-verification-rollback-policy.md` | 作業ログ、検証、ロールバック方針を追加 | 追跡可能な運用にするため | ユーザー依頼 |
| change | `00_ai_company/registry/apps.md` | XserverVPSを管理対象に追加 | 台帳から部署ルールを参照できるようにするため | 00_ai_company構成 |
| change | `00_ai_company/registry/ai-employees.md` | VPS運用AIをAI社員一覧に追加 | 台帳から職種定義を参照できるようにするため | 00_ai_company構成 |
| add | `00_ai_company/runtime/conversation_logs/2026-07-02.jsonl` | 会話ログを追加 | 仕様影響がある作業の根拠会話を残すため | 00_ai_company構成 |

## バージョン

`00_ai_company` 自体にアプリ版数が定義されていないため、バージョン変更は行っていない。

## Git

`git -C C:\App_Make status --short --branch` は `not a git repository` で失敗したため、コミットIDは取得できない。

## 検証

| コマンド | 結果 | 補足 |
| --- | --- | --- |
| `Test-Path` | pass | 追加した10ファイルの存在を確認した |
| `rg -n "VPS運用AI|XserverVPS|xserver-vps-wg|承認|ロールバック|禁止"` | pass | 追加文書と台帳から主要語句を確認した |
| `ConvertFrom-Json` | pass | `2026-07-02.jsonl` の各行がJSONとして読めることを確認した |
| `git -C C:\App_Make status --short --branch` | fail | `not a git repository` のためGit状態は取得できない |

## 生成物

なし。

## 未コミット差分

Git管理外またはGit状態を取得できないため不明。

## Git管理外ファイル

`C:\App_Make` がGitリポジトリとして認識されなかったため不明。

## 残課題

- 実VPSへの接続確認は未実施。
- 実際のサーバーユーザー、作業ディレクトリ、デプロイ対象サービスは未確定。
- 初回の読み取り調査を行う前に、対象パスと作業範囲の確認が必要。
