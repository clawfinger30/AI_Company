# AttendanceApp アプリ部署ルール

作成日: 2026-06-22

## 1. 対象アプリ

- アプリ名: AttendanceApp
- 実体パス: `AttendanceApp/`
- 主な用途: 勤怠管理、休暇管理、月次集計

## 2. 参照する共通ルール

- `../../company_rules/employee-handbook.md`
- `../../company_rules/approval-policy.md`
- `../../company_rules/history-policy.md`
- `../../company_rules/change-tracking-policy.md`
- `../../company_rules/file-operation-policy.md`

## 3. 仕様書候補

- `AttendanceApp/Readme/README.md`
- `AttendanceApp/Readme/*.md`
- `AttendanceApp/update_plan/*.md`
- `docs/monthly_aggregation_spec.md`

## 4. 実装確認の入口

- `AttendanceApp/Code.js`
- `AttendanceApp/*.js`
- `AttendanceApp/*.html`
- `AttendanceApp/appsscript.json`

## 5. 注意事項

- 既存仕様書の詳細修正は後続で個別に行う。
- 勤怠集計、休暇、承認、通知、Google カレンダー連携、月次確定は承認対象とする。
