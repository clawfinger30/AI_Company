---
tracking_id: TRACK-20260713-130916
app: HitoriOyakataMemo
app_path: AndoroAPP/HitoriOyakataMemo/
ai_employee: spec-memory-ai
work_type: spec
status: pending
created_at: 2026-07-13T13:09:16+09:00
updated_at: 2026-07-13T13:31:00+09:00
source_conversation_id: current-chat
source_request_summary: 古い未完タスクを整理し、作業記録UX再設計をv0.6として順序と仕様齟齬を検証する
version_before: 0.5.28+61
version_after: unchanged
version_files:
  - AndoroAPP/HitoriOyakataMemo/pubspec.yaml
  - AndoroAPP/HitoriOyakataMemo/lib/core/app_info.dart
version_change_required: false
version_change_reason: 今回は仕様書・タスク整理のみでアプリ実装とビルド版数は変更しないため
git:
  repo_path: C:/App_Make/AndoroAPP/HitoriOyakataMemo
  branch: main
  commit_before: 285a1f172d932a4283018a8cd4c4b501ea4dbd7f
  commit_after: pending
  status_before: modified
approval:
  required: true
  reason: v0.6では画面構成、請求履歴、DB変更候補、課金接続候補を扱うため実装前承認が必要
---

# v0.6 作業記録UX再設計へのタスク再整理

## 変更概要

古い未完タスクを、現在の中心価値である「毎日の作業記録を最短3タップで完了し、月末の請求書PDF作成をラクにすること」に合わせて再整理する。

v0.5.29〜v0.5.34として仮整理されていた項目は、画面構成と作業入力思想が大きく変わるため、v0.6系へ変更する。

## 変更案

| 種別 | 対象 | 変更内容 | 理由 |
|---|---|---|---|
| change | TASKS.md / ROADMAP.md | v0.5.29〜v0.5.34をv0.6.0〜v0.6.5へ変更 | 作業記録UX再設計は単なる継続パッチではなく大きな導線変更のため |
| change | TASKS.md / ROADMAP.md | 公開前情報更新をv0.6.6へ移動 | v0.6で画面構成が変わるため、スクリーンショットやPlay Console情報は変更後に確認する必要がある |
| change | TASKS.md / ROADMAP.md | Billing、実サービスCSV検証、PDF保存/フォーマット選択をv0.7へ分離 | v0.6の中心課題から外れ、外部依存または請求書出力強化に属するため |
| change | SPEC.md | 前回と同じで即保存時、非課税設定なら`tax_mode = non_taxable`とする | 未確定だった保存ルールを明確化するため |
| change | SPEC.md | `invoice_histories.status`は`issued`/`canceled`に限定し、再請求は関連IDで表す | 「再請求済み」をDB状態にすると状態遷移が複雑化するため |
| change | TASKS.md | Pendingを「後でやる」「検討中」「v2.0以降 Web版・Laravel同期」に分解 | 性質の違うタスクを混在させないため |
| change | TASKS.md | 画面用語整理をv0.6.0へ移動 | 作業タブ再設計に直結する確定方針のため |
| change | ROADMAP.md | Web版・Laravel同期をv2.0以降へ変更 | TASKSとの表記を揃えるため |
| change | TASKS.md / ROADMAP.md | v0.6.6のスクリーンショット項目を新画面基準へ変更 | v0.6で画面構成が変わるため |
| change | ROADMAP.md | v1.0のデータセーフティを「申告内容の最終確認」に変更 | v0.6.6のPlay Console入力と役割を分けるため |

## 承認境界

- v0.6.0〜v0.6.2のUI導線変更は、既存作業入力画面を残す前提で実装可能。
- v0.6.4の`usual_works`テーブル追加はDB変更になるため、実装前承認が必要。
- v0.6.5の請求取消・再請求整合性は請求履歴とDB変更候補を含むため、実装前承認が必要。
- v0.7のGoogle Play Billing、実サービスCSV検証、PDF端末保存は外部連携・公開動作・Android権限に影響するため、実装前承認が必要。

## 検証予定

- v0.5.29〜v0.5.34表記が主要ドキュメントに残っていないことを`rg`で確認する。
- 未確定だった`tax_mode`保存方針がSPEC/TASKSで一致していることを確認する。
- `invoice_histories.status`が`issued`/`canceled`に整理されていることを確認する。
- Markdown差分の空白エラーを`git diff --check`で確認する。
