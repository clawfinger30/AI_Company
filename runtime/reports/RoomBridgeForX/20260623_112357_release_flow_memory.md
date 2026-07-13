# RoomBridgeForX リリース手順記憶レポート

作成日時: 2026-06-23 11:23:57 JST

## 対象

- アプリ: RoomBridgeForX
- 実体パス: `@RoomBridgeForXbyElectron/`
- 変更版数: `2.2.18`

## 記憶させた手順

RoomBridgeForX のコード変更を完了する場合、担当AIは以下の順で進める。

1. バージョンを上げる。
2. 仕様書をコードから読み直して更新する。
3. Gitで差分確認とコミットを行う。
4. `npm run build` を実行する。
5. 完了報告に版数、コミットID、生成物、未コミット差分の有無を含める。

## 更新ファイル

- `00_ai_company/app_departments/RoomBridgeForX/app-rules.md`
- `00_ai_company/app_departments/RoomBridgeForX/employees/spec-memory-ai.md`
- `@RoomBridgeForXbyElectron/docs/spec.md`

## 注記

`00_ai_company/` はGit管理外のため、AI社員ルールはファイル保存で反映した。アプリ本体のGitコミットは `@RoomBridgeForXbyElectron/` リポジトリで行う。
