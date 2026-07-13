# RakuteRoom アプリ部署ルール

作成日: 2026-06-22

## 1. 対象アプリ

- アプリ名: RakuteRoom
- 実体パス: `@RakuteRoom/`
- 主な用途: 楽天ROOM関連の投稿・履歴管理

## 2. 参照する共通ルール

- `../../company_rules/employee-handbook.md`
- `../../company_rules/approval-policy.md`
- `../../company_rules/history-policy.md`
- `../../company_rules/change-tracking-policy.md`
- `../../company_rules/file-operation-policy.md`

## 3. 仕様書候補

- `@RakuteRoom/docs/spec.md`
- `@RakuteRoom/README.md`
- `@RakuteRoom/README-MULTI-ACCOUNT.md`

## 4. 実装確認の入口

- `@RakuteRoom/main.js`
- `@RakuteRoom/preload.js`
- `@RakuteRoom/renderer/`
- `@RakuteRoom/runner/`
- `@RakuteRoom/package.json`

## 5. 注意事項

- 既存仕様書の詳細修正は後続で個別に行う。
- 投稿履歴、アカウント、削除、重複投稿に関わる仕様は承認対象とする。
