# XserverVPS 作業ログ・検証・ロールバック方針

作成日: 2026-07-02

## 1. 作業ログの保存先

XserverVPSに関する調査、変更案、承認済み操作、検証結果は以下に保存する。

```text
00_ai_company/runtime/reports/XserverVPS/{YYYYMMDD_HHmmss}_{summary}.md
```

仕様変更が発生する場合は以下に変更案を作成する。

```text
00_ai_company/runtime/spec_changes/pending/XserverVPS/{YYYYMMDD_HHmmss}_{summary}.md
```

## 2. ログに残す項目

- 作業日時
- 作業モード
- 対象サーバー
- 対象パス
- 対象サービス
- 作業目的
- 実行したコマンド
- 変更したファイル
- Git状態
- Docker、Nginx、systemdなどの状態
- 検証コマンドと結果
- 生成物
- 未コミット差分
- 未確定事項
- 残課題
- 承認が必要な未実施操作

秘密情報は記録しない。表示された場合は `***` でマスクする。

## 3. 変更前チェック

変更前に、可能な限り以下を確認する。

```text
pwd
whoami
hostname
git status
git diff --stat
docker compose ps
nginx -t
df -h
free -h
```

DB、volume、証明書、`.env`、nginx設定、systemd設定を変更する場合は、バックアップまたは復元方法を先に決める。

## 4. 検証方針

変更後は、対象に応じて以下を確認する。

- 構文確認: `nginx -t`、設定ファイルのlint、アプリのビルド
- サービス確認: `docker compose ps`、`systemctl status`
- ログ確認: `docker compose logs --tail 200`、`journalctl -n 200`
- 外形確認: 対象URL、ヘルスチェック、API疎通
- Git確認: `git status`、差分、コミットID

検証できない場合は、未検証の理由を記録する。

## 5. ロールバック方針

変更前に、次のいずれで戻すかを決める。

- Gitで戻す
- 事前バックアップファイルへ戻す
- 直前のDocker imageまたはcompose設定へ戻す
- DBバックアップから復元する
- Nginxまたはsystemd設定を旧版へ戻す
- ユーザーに手動復旧を依頼する

ロールバック手順には、実行コマンド、成功条件、失敗時の次の対応を含める。

## 6. 完了報告の最低項目

- 実施したこと
- 実施しなかったこと
- 承認を受けた操作
- 実行コマンド
- 検証結果
- ロールバック可否
- 残課題

