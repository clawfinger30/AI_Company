# PintarestRoom アプリ部署ルール

作成日: 2026-06-22

## 1. 対象アプリ

- アプリ名: PintarestRoom
- 実体パス: `PintarestRoom/`
- 主な用途: 楽天ROOM投稿を Pinterest に投稿する Electron アプリ

## 2. 参照する共通ルール

- `../../company_rules/employee-handbook.md`
- `../../company_rules/approval-policy.md`
- `../../company_rules/history-policy.md`
- `../../company_rules/change-tracking-policy.md`
- `../../company_rules/file-operation-policy.md`

## 3. 仕様書候補

- `PintarestRoom/SPEC.md`

## 4. 実装確認の入口

- `PintarestRoom/main.js`
- `PintarestRoom/preload.js`
- `PintarestRoom/renderer/`
- `PintarestRoom/package.json`

## 5. 注意事項

- 既存仕様書の詳細修正は後続で個別に行う。
- Pinterest 投稿、ログイン、投稿履歴、二重投稿防止に関わる仕様は承認対象とする。
