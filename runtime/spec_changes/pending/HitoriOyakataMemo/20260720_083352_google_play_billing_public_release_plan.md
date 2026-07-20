---
tracking_id: TRACK-20260720-083352
app: HitoriOyakataMemo
app_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
ai_employee: spec-memory-ai
work_type: spec
status: pending
created_at: 2026-07-20T08:33:52+09:00
updated_at: 2026-07-20T08:33:52+09:00
source_conversation_id: unavailable
source_request_summary: クローズドテスト終了前に、有料プラン実装、デバッグ用プレミアム除外、本番公開前タスクを洗い出して整理する。
version_before: 0.6.10+79
version_after: 0.7.x planned
version_files:
  - AndoroAPP/HitoriOyakataMemo/pubspec.yaml
  - AndoroAPP/HitoriOyakataMemo/lib/core/constants/app_info.dart
version_change_required: false
version_change_reason: 今回は実装前のタスク・仕様変更案整理のみ。コード実装時に0.7系へ更新する。
git:
  repo_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
  branch: main
  commit_before: 22553f3
  commit_after: unavailable
  status_before: v0.6.10+79の未コミットコード・文書差分あり
  status_after: task documents updated; code changes preserved
  remote: origin/main
approval:
  required: true
  reason: Google Play Billing、定期購入、プレミアム権利判定、公開申告に関係するため。
  requested_at: 2026-07-20T08:33:52+09:00
  approved_by: pending
  approved_at: pending
---

# Google Play Billing・本番公開タスク整理案

## 背景

- 前回クローズドテストAABは`0.5.28+61`。
- 現在の作業ツリーは`0.6.10+79`で、コードとTASKS/ROADMAPに未コミット差分がある。
- クローズドテスト終了見込みは2026年7月23日頃。
- 現在の本番権利判定候補はSQLiteの`app_preferences.premium_active`だが、これはdebug/内部テスト用の手動状態であり、本番課金権利として使用できない。
- release AABでも`ENABLE_INTERNAL_TEST_PREMIUM=true`を付けると手動切替を表示できるため、本番公開前に廃止・隔離が必要。

## 変更案

### 1. バージョン順

1. `v0.6.11`: `0.6.10+79`を基準版としてレビュー、検証、commit / pushする。
2. `v0.7.0`: 課金仕様とPlay Consoleの商品設定を確定し、Google Play Billingを実装する。
3. `v0.7.1`: 旧手動プレミアム権利を本番権利から隔離・移行する。
4. `v0.7.2`: ライセンステスターとPlay Billing Labで課金ライフサイクルを検証する。
5. `v0.7.3`: 製品版アクセス申請、公開文書、申告、素材、本番AABを確定する。
6. 会計CSV実サービス検証、PDF保存/フォーマット、SQLite自動バックアップは公開後の`v0.8`へ移す。

### 2. 初期課金商品

既存方針に合わせ、次を候補とする。

| 項目 | 候補 |
|---|---|
| 商品種別 | 自動更新の定期購入 |
| 商品ID | `premium_monthly_android` |
| 基本プランID | `monthly` |
| 日本価格 | 月額500円 |
| 無料体験 | 初期公開ではなし |
| Android外部決済誘導 | 初期公開では行わない |

商品IDと基本プランIDはPlay Consoleで有効化する前に人間承認を必要とする。

### 3. 本番権利判定

- 本番releaseはGoogle Playの有効な購入状態だけをプレミアム権利の根拠にする。
- 旧`premium_active=true`は本番権利として読まない。
- debug専用の手動切替は残してよいが、Google Play購入権利とは別状態にする。
- release用`ENABLE_INTERNAL_TEST_PREMIUM`は廃止し、内部/クローズドテストもライセンステスターのテスト購入を使う。
- 購入が`PENDING`の場合は権利を付与しない。
- 初回購入は検証後にacknowledgeする。
- 解約後は有効期限までは利用中、期限切れまたはアカウント一時停止では無料扱いにする。

### 4. クライアントのみでの初期実装リスク

既存設計はLaravel APIをv2.0以降としているため、v0.7は端末からGoogle Play購入状態を確認する構成が候補になる。
Google公式は購入検証、権利管理、RTDNを安全なバックエンドで行うことを強く推奨している。
クライアントのみで公開する場合、改変耐性、返金/取消の即時反映、正確な有効期限表示に限界がある。

このリスクを承認した場合のみ、v0.7はクライアント構成で進め、サーバー検証・RTDN・権利台帳をv2.0のLaravelタスクへ移す。

### 5. Data safety・公開文書

- Google Play Billingが直接処理し、アプリがアクセスしないカード番号等は、条件を満たせばアプリの収集として申告不要。
- 一方、アプリが受け取る購入状態や保存する購入履歴/トークンは、実装内容に応じてData safetyを再判定する。
- プライバシーポリシーとアプリ内の「課金を使用しない」「Billing接続予定」は公開前に更新する。
- ストア説明には無料範囲、月額料金、主な有料機能、自動更新を明確に書く。

## 承認待ち

1. 月額500円、自動更新、無料体験なしで初期公開するか。
2. 商品ID`premium_monthly_android`、基本プランID`monthly`で確定するか。
3. v0.7をクライアント権利判定で公開し、バックエンド検証をv2.0へ移すか。
4. 通信失敗時に直前確認済みのプレミアム権利を何日保持するか。
5. Play Consoleの猶予期間とアカウント一時停止期間をどう設定するか。

## 公式確認元

- Google Play Billing integration: https://developer.android.com/google/play/billing/integrate
- Google Play Billing testing: https://developer.android.com/google/play/billing/test
- Subscription lifecycle: https://developer.android.com/google/play/billing/lifecycle/subscriptions
- Billing security and backend verification: https://developer.android.com/google/play/billing/security
- Billing Library deprecation schedule: https://developer.android.com/google/play/billing/deprecation-faq
- Google Play subscriptions: https://support.google.com/googleplay/android-developer/answer/12154973
- Payments policy: https://support.google.com/googleplay/android-developer/answer/9858738
- Data safety form guidance: https://support.google.com/googleplay/android-developer/answer/10787469
- Production access testing requirements: https://support.google.com/googleplay/android-developer/answer/14151465

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 |
|---|---|---|---|
| change | `AndoroAPP/HitoriOyakataMemo/TASKS.md` | v0.6.11、v0.7.0〜v0.7.3、v0.8へ再編 | 課金と公開を優先順で実行するため |
| change | `AndoroAPP/HitoriOyakataMemo/ROADMAP.md` | 課金・公開ロードマップを同じ順番へ同期 | TASKSとの齟齬防止 |
| change | `AndoroAPP/HitoriOyakataMemo/SPEC.md` | PDF端末保存の予定版をv0.8.1へ更新 | 移行先の齟齬防止 |
| add | 本ファイル | 承認待ち仕様とリスクを記録 | 課金は承認対象のため |

## 検証

- `TASKS.md`と`ROADMAP.md`のバージョン順・見出し・未完了項目を機械確認する。
- `git diff --check`でMarkdown差分の空白エラーを確認する。
- コード変更、バージョン更新、ビルドは今回行わない。
