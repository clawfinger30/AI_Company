# HitoriOyakataMemo アプリ部署ルール

作成日: 2026-07-09

## 1. 対象アプリ

- アプリ名: HitoriOyakataMemo
- 表示名: 現場メモ日報
- 実体パス: `AndoroAPP/HitoriOyakataMemo/`
- 主な技術: Flutter、Dart、Android、SQLite、PDF、CSV、Google Play
- 主な用途: 個人事業主・応援作業者・電気工事士向けの作業記録、月別集計、請求書PDF作成

## 2. 参照する共通ルール

- `../../company_rules/employee-handbook.md`
- `../../company_rules/approval-policy.md`
- `../../company_rules/history-policy.md`
- `../../company_rules/change-tracking-policy.md`
- `../../company_rules/file-operation-policy.md`

## 3. 仕様書候補

- `AndoroAPP/HitoriOyakataMemo/SPEC.md`
- `AndoroAPP/HitoriOyakataMemo/TASKS.md`
- `AndoroAPP/HitoriOyakataMemo/ROADMAP.md`
- `AndoroAPP/HitoriOyakataMemo/README.md`
- `AndoroAPP/HitoriOyakataMemo/docs/play/*.md`

## 4. 実装確認の入口

- `AndoroAPP/HitoriOyakataMemo/lib/main.dart`
- `AndoroAPP/HitoriOyakataMemo/lib/data/database/app_database.dart`
- `AndoroAPP/HitoriOyakataMemo/lib/domain/`
- `AndoroAPP/HitoriOyakataMemo/lib/presentation/`
- `AndoroAPP/HitoriOyakataMemo/test/`
- `AndoroAPP/HitoriOyakataMemo/pubspec.yaml`
- `AndoroAPP/HitoriOyakataMemo/android/app/build.gradle`

## 5. 注意事項

- ユーザー向け用語は、プロジェクト内 `SPEC.md` の用語方針を優先する。
- 中心価値は「毎日の作業記録を最短3タップで完了し、月末の請求書PDF作成をラクにすること」とする。
- Google Play公開前提のため、パッケージ名、バージョンコード、プライバシーポリシー、データセーフティ、内部テスト導線の変更は承認対象とする。
- SQLiteスキーマ変更、DB復元、請求済みステータス変更、PDF/CSV出力、課金・プレミアム制御は承認対象とする。
- 既存の未コミット差分はユーザー作業の可能性があるため、作業前に `git status --short` を確認する。

## 6. TASKS / ROADMAP 運用

- 実装は `TASKS.md` と `ROADMAP.md` のバージョンが若い順に進める。
- 先のバージョンへ進む前に、現在のバージョン節に未完了チェックが残っていないことを確認する。
- 現在のバージョンで扱わないタスクは、移行先バージョンを明記して後続節へ移す。
- 移行したタスクは、元のバージョン節では「後続版へ移行済み」として完了扱いにし、未完了チェックを残さない。
- 親タスクに現在版の作業と後続版の作業が混ざっている場合は、親タスクを分解してから実装する。
- v0.6以降の作業記録UX再設計では、v0.6.0、v0.6.1、v0.6.2の順に完了または移行を確認してから次へ進む。
