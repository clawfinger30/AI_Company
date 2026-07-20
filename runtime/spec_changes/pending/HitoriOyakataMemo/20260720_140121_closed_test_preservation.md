---
tracking_id: TRACK-20260720-140121
app: HitoriOyakataMemo
app_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
ai_employee: spec-memory-ai
work_type: spec
status: applied
created_at: 2026-07-20T14:01:21+09:00
updated_at: 2026-07-20T14:04:00+09:00
source_conversation_id: unavailable
source_request_summary: 現在のクローズドテストに影響を及ぼさない条件で次の課金テストタスクへ進める。
version_before: 0.7.1+81
version_after: 0.7.1+81
version_files: []
version_change_required: false
version_change_reason: 今回は配信保護条件とタスク・手順書の変更のみで、アプリコードは変更しない。
git:
  repo_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
  branch: main
  commit_before: 588a697
  commit_after: dc254ed
  status_before: clean
  status_after: task and release procedure documents updated; committed and pushed
  remote: origin/main
approval:
  required: true
  reason: Google Playのテストトラック、課金テスト、公開状態に関係するため。
  requested_at: 2026-07-20T14:01:21+09:00
  approved_by: user
  approved_at: 2026-07-20
---

# 現在のクローズドテスト保護条件

## Play Console読み取り確認

2026-07-20にPlay Consoleのダッシュボードを読み取り確認した。

- 製品版: 非アクティブ
- クローズドテスト: 有効
- クローズドテストのオプトイン: 12人
- 継続日数: 11日連続
- 本番アクセス申請: まだ無効

## 確定した運用条件

- 現在のクローズドテストのリリース、テスター、オプトインURL、公開状態を変更しない。
- v0.7.2の課金テスト用AABを既存クローズドテストへ追加・置換しない。
- 課金テスト用トラックを作成・公開する場合は、対象トラックを明示し、Googleアカウントを確認してから行う。
- ライセンステスター登録、テスト購入、解約・期限切れ確認は、既存クローズドテストの継続条件と分離して記録する。
- 今回はPlay Consoleへの書き込み操作を行っていない。

## 変更ファイル

| 種別 | ファイル | 変更内容 |
|---|---|---|
| change | `TASKS.md` | v0.7.2にクローズドテスト保護条件を追加 |
| change | `ROADMAP.md` | v0.7.2に配信状態を変更しない確認項目を追加 |
| change | `docs/play/BUILD_COMMANDS.md` | 既存クローズドテストへ無断アップロードしない手順へ変更 |
| add | 本ファイル | Play Console読み取り結果と運用境界を記録 |

## 次のブロッカー

課金テストは、ライセンステスターとして登録するGoogleアカウントと、使用する別トラックの指定が必要である。アカウント未確定のままPlay Consoleへの登録・公開操作は行わない。

## 検証

- Play Consoleダッシュボードを読み取り、クローズドテストが有効、12人、11日連続であることを確認した。
- Play Consoleへの書き込み操作を行っていない。
- アプリリポジトリのコード・バージョン・AABは変更していない。
