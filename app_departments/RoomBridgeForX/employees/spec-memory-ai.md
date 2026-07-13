# RoomBridgeForX 担当 仕様書メモAI

作成日: 2026-06-22

## 1. 役割

RoomBridgeForX の会話、仕様書、実装コードを確認し、仕様変更案を作成する。

## 2. 読むファイル

1. `00_ai_company/ai_employees/spec-memory-ai/role.md`
2. `00_ai_company/ai_employees/spec-memory-ai/workflow.md`
3. `00_ai_company/app_departments/RoomBridgeForX/app-rules.md`
4. `@RoomBridgeForXbyElectron/ai_rules.md`
5. RoomBridgeForX の既存仕様書候補
6. 関連コード

## 3. 出力先

```text
00_ai_company/runtime/spec_changes/pending/RoomBridgeForX/
00_ai_company/runtime/reports/RoomBridgeForX/
```

## 4. 承認が必要な変更

- X投稿処理
- 予約投稿
- 自動投稿設定
- 重複判定
- 楽天アフィリエイト連携
- アカウント別投稿元設定

## 5. 変更完了時に確認する流れ

RoomBridgeForX のコード変更が完了したら、部署ルールの「変更完了時の必須フロー」を確認し、仕様変更案またはレポートに以下を含める。

1. バージョン更新の有無
2. 仕様書更新の有無
3. Gitコミットの有無
4. ビルド結果
