# RoomBridgeForX アプリ部署ルール

作成日: 2026-06-22

## 1. 対象アプリ

- アプリ名: RoomBridgeForX
- 実体パス: `@RoomBridgeForXbyElectron/`
- 主な用途: 楽天ROOMまたは楽天アフィリエイト候補から X へ投稿する Electron アプリ

## 2. 参照する共通ルール

- `../../company_rules/employee-handbook.md`
- `../../company_rules/approval-policy.md`
- `../../company_rules/history-policy.md`
- `../../company_rules/change-tracking-policy.md`
- `../../company_rules/file-operation-policy.md`

## 3. 仕様書候補

- `@RoomBridgeForXbyElectron/docs/spec.md`
- `@RoomBridgeForXbyElectron/README.md`
- `@RoomBridgeForXbyElectron/docs/rakuten-affiliate-feature-spec.md`
- `@RoomBridgeForXbyElectron/docs/manual-posting-feature-spec.md`
- `@RoomBridgeForXbyElectron/docs/ai-generation-feature-spec.md`
- `@RoomBridgeForXbyElectron/docs/x-posting-safety-rules.md`

## 4. 実装確認の入口

- `@RoomBridgeForXbyElectron/main.js`
- `@RoomBridgeForXbyElectron/src/`
- `@RoomBridgeForXbyElectron/package.json`

## 5. 注意事項

- 既存仕様書の詳細修正は後続で個別に行う。
- X投稿、自動化、予約投稿、重複判定、楽天アフィリエイト連携は承認対象とする。
- X投稿、自動化、複数アカウント運用、凍結・制限検知に関する作業では、`@RoomBridgeForXbyElectron/docs/x-posting-safety-rules.md` を必ず参照する。
- Xの制限、検知、凍結、rate limit、表示制限を回避するための処理は実装しない。

## 6. 変更完了時の必須フロー

RoomBridgeForX のコード変更を完了する場合、担当AIは原則として以下の順序で処理する。

1. バージョンを上げる。
   - `@RoomBridgeForXbyElectron/package.json`
   - `@RoomBridgeForXbyElectron/package-lock.json`
   - 初期表示など固定バージョン表記があるファイル
2. 仕様書をコードから読み直して更新する。
   - 主対象: `@RoomBridgeForXbyElectron/docs/spec.md`
   - 影響がある場合: 個別仕様書も更新する。
3. Gitで差分を確認し、関連変更をコミットする。
4. ビルドする。
   - `npm run build`
   - 生成物: `@RoomBridgeForXbyElectron/dist/Room Bridge for X Setup <version>.exe`
5. 完了報告には、更新版数、コミットID、ビルド生成物、未コミット差分の有無を含める。
