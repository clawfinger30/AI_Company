# Oyakata アプリ部署ルール

作成日: 2026-07-09

## 1. 対象アプリ

- アプリ名: Oyakata
- 実体パス: `oyakata/`
- 主な技術: Laravel、PHP、Blade、Vite、SQLite/MariaDB、PDF、CSV、LINE連携
- 主な用途: 受注先、顧客、請求書、入金、LINE連携を扱う Web アプリ

## 2. 参照する共通ルール

- `../../company_rules/employee-handbook.md`
- `../../company_rules/approval-policy.md`
- `../../company_rules/history-policy.md`
- `../../company_rules/change-tracking-policy.md`
- `../../company_rules/file-operation-policy.md`

## 3. 仕様書候補

- `oyakata/README.md`
- `oyakata/docs/database-spec.md`
- `oyakata/USER_MANUAL.md`
- `oyakata/XSERVER_DEPLOY_README.md`

## 4. 実装確認の入口

- `oyakata/routes/web.php`
- `oyakata/routes/admin.php`
- `oyakata/routes/auth.php`
- `oyakata/app/Http/Controllers/`
- `oyakata/app/Models/`
- `oyakata/app/Services/`
- `oyakata/database/migrations/`
- `oyakata/resources/views/`
- `oyakata/composer.json`
- `oyakata/package.json`

## 5. 注意事項

- 受注、顧客、請求書、入金、税率、PDF出力、CSV入出力に関わる仕様は、既存データへの影響を確認してから扱う。
- 認証、2段階認証、管理者権限、会社スコープ、LINE連携、本番デプロイ、ライセンス・料金表示の変更は承認対象とする。
- DB migration、Seeder、バックアップSQL、既存データ補正コマンドを扱う場合は、実行前に対象環境とロールバック方法を確認待ちにする。
- 既存の未コミット差分はユーザー作業の可能性があるため、作業前に取得可能な範囲で状態を確認する。
