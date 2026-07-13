# 会話ログスキーマ

作成日: 2026-06-22

会話ログは JSON Lines 形式で保存する。

## 1. 保存先

```text
00_ai_company/runtime/conversation_logs/{YYYY-MM-DD}.jsonl
```

## 2. レコード形式

```json
{
  "conversation_id": "conv-20260622-0001",
  "turn_id": "turn-0001",
  "timestamp": "2026-06-22T10:30:00+09:00",
  "app": "RakuteRoom",
  "speaker": "user",
  "message": "仕様メモして",
  "summary": "仕様書更新依頼",
  "tags": ["spec", "request"],
  "source": "chat"
}
```

## 3. 必須項目

- `conversation_id`
- `turn_id`
- `timestamp`
- `speaker`
- `message`

## 4. 任意項目

- `app`
- `summary`
- `tags`
- `source`
- `related_files`
- `confidence`

