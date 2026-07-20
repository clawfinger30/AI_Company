---
tracking_id: TRACK-20260720-134839
app: HitoriOyakataMemo
app_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
ai_employee: spec-memory-ai
work_type: spec
status: applied
created_at: 2026-07-20T13:48:39+09:00
updated_at: 2026-07-20T13:52:00+09:00
source_conversation_id: unavailable
source_request_summary: Play Consoleで有効化した基本プランID monthly-1 と受取口座の確認待ち状態をアプリ仕様、実装、公開タスクへ反映する。
version_before: 0.7.0+80
version_after: 0.7.1+81
version_files:
  - AndoroAPP/HitoriOyakataMemo/pubspec.yaml
  - AndoroAPP/HitoriOyakataMemo/lib/core/constants/app_info.dart
version_change_required: true
version_change_reason: Play Consoleの実設定との同期と公開版の手動プレミアム権利隔離を行うため。
git:
  repo_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
  branch: main
  commit_before: 4db394710d13bb24ea8800f6698667304a72bd10
  commit_after: 588a697
  status_before: clean
  status_after: implementation verified; committed and pushed
  remote: origin/main
approval:
  required: true
  reason: Google Play Billingの商品識別子、公開版の権利判定、販売者支払設定に関係するため。
  requested_at: 2026-07-20T08:33:52+09:00
  approved_by: user
  approved_at: 2026-07-20
---

# Google Play基本プラン実ID同期と手動プレミアム隔離

## 確定したPlay Console設定

| 項目 | 確定値 |
|---|---|
| 定期購入商品ID | `premium_monthly_android` |
| 基本プランID | `monthly-1` |
| 更新周期 | 1か月ごとの自動更新 |
| 販売地域 | 日本 |
| 価格 | 月額500円 |
| 無料体験 | 初期公開ではなし |
| 基本プラン状態 | 有効 |
| 受取口座 | 登録済み、確認待ち |

当初予定していた基本プランID`monthly`は履歴としてだけ残し、アプリが商品を取得するときはPlay Consoleで有効化された実ID`monthly-1`を使用する。

## 権利判定の変更

- release版では、旧SQLiteキー`premium_active`を有料権利として使用しない。
- release版の有料権利は、Google Playの購入結果と最終確認から3日以内の確認済みキャッシュだけを根拠にする。
- debug版の手動切替は`DebugPremiumOverrideRepository`へ分離する。
- release用`ENABLE_INTERNAL_TEST_PREMIUM`と「内部テスト用プレミアム切替」を廃止する。
- 内部テストとクローズドテストも、ライセンステスターのGoogle Playテスト購入を使用する。

## 受取口座

受取口座は登録済みだが、Play Console表示は「確認待ち」である。確認完了とは扱わず、解除確認、税務情報、公開販売者情報、問い合わせ先の最終確認をv0.7.3へ移行する。

## 変更ファイル

| 種別 | ファイル | 変更内容 |
|---|---|---|
| change | `TASKS.md` / `ROADMAP.md` / `SPEC.md` | 実ID、移行先、公開前確認を同期 |
| change | `pubspec.yaml` / `lib/core/constants/app_info.dart` | `0.7.1+81`へ更新 |
| change | `lib/core/constants/premium_product_config.dart` | 基本プランIDを`monthly-1`へ変更 |
| add | `lib/domain/repositories/debug_premium_override_repository.dart` | debug専用手動権利の分離 |
| change | Premium Repository、起動処理、プレミアム画面 | release版から手動権利変更経路を除外 |
| change | Billing・画面・SQLiteテスト | 実IDと権利分離を自動確認 |
| change | `docs/play/BUILD_COMMANDS.md`ほか | 課金テストと本番で同じreleaseビルドを使用する手順へ更新 |

## 検証結果

- `flutter analyze --no-pub`: 問題なし。
- `flutter test --no-pub --concurrency=1`: 157件成功。
- release APK: applicationId=`hitori.oyakata.memo`、versionName=`0.7.1`、versionCode=`81`。
- release Manifest: `com.android.vending.BILLING`を確認。
- release AAB/APKビルド: 成功。
- AAB署名: 検証成功。
- 標準AABと配布名2ファイルのSHA-256: 一致。
- release APK/AAB内にrelease用手動切替フラグとテスト切替文言が含まれないことを確認。
- DBスキーマ変更なし。既存SQLiteデータは削除・初期化しない。

## 次工程

v0.7.2でライセンステスターを登録し、Play配布版で購入、復元、解約、期限切れ、旧内部テスト版からの上書きを確認する。
