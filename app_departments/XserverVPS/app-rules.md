# XserverVPS 部署ルール

作成日: 2026-07-02

## 1. 対象

- 部署名: XserverVPS
- 対象環境: Xserver VPS上のUbuntu本番環境
- 接続エイリアス: `xserver-vps-wg`
- 接続確認方法: PowerShellで `ssh xserver-vps-wg`
- ローカル関連パス: `infra/`
- 主な用途: 本番インフラ、Docker Compose、Nginx、SSL、デプロイ補助、運用調査

接続エイリアス以外のIPアドレス、秘密鍵、パスワード、ユーザー名、トークンはこの部署ルールに記録しない。

## 2. 参照する共通ルール

- `../../company_rules/employee-handbook.md`
- `../../company_rules/approval-policy.md`
- `../../company_rules/history-policy.md`
- `../../company_rules/change-tracking-policy.md`
- `../../company_rules/file-operation-policy.md`

## 3. 参照する部署内ルール

- `command-policy.md`
- `approval-policy.md`
- `log-verification-rollback-policy.md`
- `employees/vps-operator-ai.md`

## 4. 仕様書候補

- `infra/README.md`
- `infra/docker-compose.yml`
- `infra/docker-compose.prod.yml`
- `infra/env.example`
- `infra/nginx/conf.d/`
- 対象アプリ側のREADME、仕様書、デプロイ手順

## 5. 実装確認の入口

- ローカル: `C:\App_Make\infra`
- リモート: VSCode Remote-SSHで開いた対象ワークスペース
- Docker Compose設定
- Nginx設定
- systemd、cron、証明書、ログの状態

リモート上の絶対パスは作業ごとに確認し、推測で固定しない。

## 6. 注意事項

- 本番環境の変更は、調査、提案、承認済み変更を明確に分ける。
- SSH接続、VSCode Remote-SSH、認証情報、Firewall、証明書、DB、Docker volume、デプロイは承認対象として扱う。
- rootユーザーの常用は禁止する。
- 秘密情報を含むファイルは、値を表示・転記せず、存在確認と必要項目名の確認に留める。
- 変更前にロールバック方法を決める。
- 障害時でも、実行したコマンドと結果は後から追跡できる形で残す。

## 7. 出力先

```text
00_ai_company/runtime/spec_changes/pending/XserverVPS/
00_ai_company/runtime/reports/XserverVPS/
```

