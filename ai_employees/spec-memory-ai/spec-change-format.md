# 仕様変更案フォーマット

作成日: 2026-06-22

仕様変更案は Markdown で作成する。

## テンプレート

```md
---
change_id: CHANGE-YYYYMMDD-HHMMSS
tracking_id: TRACK-YYYYMMDD-HHMMSS
app: RakuteRoom
app_path:
ai_employee: spec-memory-ai
status: pending
change_type: add
work_type: spec
created_at: 2026-06-22T10:30:00+09:00
updated_at: 2026-06-22T10:30:00+09:00
added_at:
source_conversation_id: conv-20260622-0001
source_request_summary:
confidence: 0.85
requires_approval: true
version_before:
version_after:
version_files: []
git:
  available:
  repo_path:
  branch:
  commit_before:
  commit_after:
  status_before:
  status_after:
---

# 変更案タイトル

## 要約

## 根拠

## 対象仕様書

## 追加・変更・廃止内容

## コード確認結果

## 追跡メタデータ

## バージョン確認

## Git確認

## 変更ファイル詳細

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
| --- | --- | --- | --- | --- |

## 未確定事項

## 承認が必要な理由
```

## change_type

```text
add
change
deprecate
remove_candidate
question
code_gap
```

## 必須記録

仕様変更案には `change-tracking-policy.md` の必須メタデータを可能な限り含める。

Git管理外、バージョンなし、検証未実施などの場合も、空欄にせず理由を記録する。
