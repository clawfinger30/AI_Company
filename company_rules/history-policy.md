# 履歴・タイムスタンプ規則

作成日: 2026-06-22

## 1. 日時形式

日時は JST の ISO 8601 形式で記録する。

```text
2026-06-22T10:30:00+09:00
```

## 2. 仕様 ID

仕様には、アプリ名を含む ID を付ける。

```text
APP-SPEC-0001
```

例:

```text
RAKUTEROOM-SPEC-0001
ROOMBRIDGE-SPEC-0001
PINTARESTROOM-SPEC-0001
INSTAROOM-SPEC-0001
ATTENDANCE-SPEC-0001
```

## 3. 変更履歴に残す項目

- 仕様 ID
- 追跡 ID
- ステータス
- 作成日時
- 更新日時
- 追加日時
- 廃止日時
- 対象アプリ
- 対象ファイル
- 変更種別
- アプリバージョン変更前
- アプリバージョン変更後
- バージョン記載ファイル
- Git リポジトリ
- Git ブランチ
- Git コミット変更前
- Git コミット変更後
- Git 状態
- ビルド生成物
- 検証コマンドと結果
- 根拠会話 ID
- 根拠コード
- 変更理由
- 承認者
- AI 社員名

## 3.1 追加・変更・廃止の詳細

追加、変更、廃止候補は以下を分けて記録する。

- `added_at`: 初めて仕様またはコードに追加した日時
- `changed_at`: 既存項目を変更した日時
- `deprecated_at`: 廃止候補または廃止済みにした日時
- `added_by`: 追加した AI 社員または担当者
- `change_reason`: 変更理由
- `source_request_summary`: ユーザー依頼または根拠の要約
- `affected_files`: 影響ファイル
- `verification`: 確認内容

詳細な記録形式は `change-tracking-policy.md` に従う。

## 4. ステータス

```text
draft       # 下書き
pending     # 承認待ち
approved    # 承認済み
applied     # 反映済み
deprecated  # 廃止予定または廃止済み
rejected    # 却下
```

## 5. 会話ログとの紐づけ

仕様変更案には、可能な限り `source_conversation_id` を記録する。

会話 ID が不明な場合は、日時と要約を残す。
