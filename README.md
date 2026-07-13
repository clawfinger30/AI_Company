# 00_ai_company

`00_ai_company` は、`C:\App_Make` 配下で働く汎用 AI 社員の本社ルール置き場です。

`00_ai_company` の現行仕様は [`SPEC.md`](SPEC.md) を参照してください。

各 AI 社員は、作業前に以下を確認します。

1. 全社共通ルール
2. 自分の職種ルール
3. 対象アプリ部署のルール
4. 対象アプリ専属 AI 社員のルール
5. 対象アプリの既存仕様書と実装コード

## 重点管理アプリ

重点管理対象は、`registry/apps.md` の正式名と別名で照合します。

- RakuteRoom
- HitoriOyakataMemo
- RoomBridgeForX
- PintarestRoom
- Oyakata

## ディレクトリ

```text
00_ai_company/
├─ company_rules/       # 全AI社員共通の規則
├─ ai_employees/        # AI社員の職種別ルール
├─ app_departments/     # 各アプリ部署の規約
├─ templates/           # 仕様書・変更案のテンプレート
├─ registry/            # 管理対象アプリとAI社員一覧
└─ runtime/             # 会話ログ、変更案、レポート、トリガ記録
```

## 基本方針

- 仕様書は、会話、実装、運用判断を後から追える状態で更新する。
- 追加、変更、削除の根拠には会話 ID、日時、対象ファイルを残す。
- 変更追跡は `company_rules/change-tracking-policy.md` に従い、追加日、更新日、バージョン、Git、検証、生成物を残す。
- AI は削除を直接実行しない。削除候補は `deprecated` または `archive` として提案する。
- 各アプリの詳細仕様書修正は、各アプリ部署のルールに従って個別に行う。
- コード作成時は `company_rules/employee-handbook.md` の「コード作成時の基本方針」に従い、機械的な完了判定、複数解釈の確認、ついで改善禁止、検証報告、同一エラー2回制限、完了前レビュー、進捗・確信度・残リスク報告を必須とする。
