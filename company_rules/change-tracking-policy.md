# 変更追跡ポリシー

作成日: 2026-06-23  
適用範囲: `C:\App_Make` 配下の全 AI 社員、全アプリ部署

## 1. 目的

仕様変更、コード変更、設定変更、ビルド、リリース作業を後から追跡できる状態で残す。

AI 社員は「何を、いつ、どの版で、どの Git 状態から、どのファイルに、なぜ変更したか」を記録する。

## 2. 必須メタデータ

仕様変更案、仕様書、作業レポート、リリースレポートには、可能な限り以下を残す。

```yaml
tracking_id: TRACK-YYYYMMDD-HHMMSS
app:
app_path:
ai_employee:
work_type: spec | code | docs | build | release | investigation
status: draft | pending | applied | blocked | rejected
created_at: YYYY-MM-DDTHH:mm:ss+09:00
updated_at: YYYY-MM-DDTHH:mm:ss+09:00
source_conversation_id:
source_request_summary:
```

## 3. バージョン追跡

アプリに版数がある場合は、変更前後を必ず記録する。

```yaml
version_before:
version_after:
version_files:
  - package.json
  - package-lock.json
  - appsscript.json
  - その他の固定表示ファイル
version_change_required: true | false
version_change_reason:
```

版数を上げない場合も、`version_change_required: false` と理由を残す。

## 4. Git追跡

Git 管理下の作業では、作業前後の状態を記録する。

```yaml
git:
  repo_path:
  branch:
  commit_before:
  commit_after:
  status_before:
  status_after:
  tag:
  remote:
```

Git 管理外の場合は、以下のように明示する。

```yaml
git:
  available: false
  reason: "not a git repository"
```

## 5. ファイル変更追跡

変更したファイルは、本文に表で記録する。

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |
| add/change/deprecate/remove_candidate | path | summary | reason | conversation/code/spec |

記録する内容:

- 追加した日
- 変更した日
- 対象アプリ
- 対象ファイル
- 変更種別
- 変更理由
- 参照した会話、仕様書、コード
- 承認が必要か
- 未確定事項

## 6. 検証追跡

コード変更、ビルド、リリース作業では、実行した確認を残す。

```yaml
verification:
  commands:
    - command:
      result: pass | fail | skipped
      note:
  artifacts:
    - path:
      created_at:
      note:
```

テストやビルドを実行しない場合は、`skipped` と理由を残す。

## 7. 承認追跡

承認対象は、承認状態を明示する。

```yaml
approval:
  required: true | false
  reason:
  requested_at:
  approved_by:
  approved_at:
```

承認が必要な変更を未承認で反映した場合は、理由とユーザー指示を本文に残す。

## 8. 完了時の最低記録

作業完了時のレポートには最低限以下を含める。

- 作業日時
- 対象アプリ
- 変更前後のバージョン
- Git リポジトリ、ブランチ、コミットID
- 変更ファイル一覧
- 実行した検証
- ビルド生成物
- 未コミット差分の有無
- Git 管理外ファイルの有無
- 残課題

## 9. 記録できない場合

情報を取得できない場合は空欄にせず、理由を記録する。

例:

```yaml
commit_after: unavailable
commit_after_reason: "00_ai_company is not a git repository"
```
