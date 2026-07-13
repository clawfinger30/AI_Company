# runtime

AI 社員の実行結果、会話ログ、変更案、レポート、トリガ記録を置く場所です。

この配下は運用データです。仕様書本文ではなく、作業履歴として扱います。

仕様影響がある会話、調査、コード変更は、仕様書メモAIが明示依頼なしで自動記録します。自動記録の出力もこの配下に保存します。

## 構成

```text
runtime/
├─ conversation_logs/
├─ spec_changes/
│  ├─ pending/
│  ├─ approved/
│  ├─ applied/
│  └─ rejected/
├─ reports/
└─ triggers/
```
