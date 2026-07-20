---
tracking_id: TRACK-20260720-142154
app: HitoriOyakataMemo
app_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
ai_employee: spec-memory-ai
work_type: docs
status: applied
created_at: 2026-07-20T14:21:54+09:00
updated_at: 2026-07-20T14:25:00+09:00
source_conversation_id: unavailable
source_request_summary: クローズドテストの14日条件達成を待ち、製品版アクセス申請後に別トラックで課金テストを行う順番へタスク予定を修正する。
version_before: 0.7.1+81
version_after: 0.7.1+81
version_files: []
version_change_required: false
version_change_reason: タスク順序とPlay Console運用予定の文書変更のみで、アプリコードは変更しない。
git:
  repo_path: C:\App_Make\AndoroAPP\HitoriOyakataMemo
  branch: main
  commit_before: dc254edc0f476ba4d27dce2163188082b2dd9797
  commit_after: e3935c7
  status_before: clean
  status_after: schedule documents updated; committed and pushed
  tag: none
  remote: origin/main
approval:
  required: true
  reason: Google Playクローズドテスト、製品版アクセス申請、課金テストの実施順に関係するため。
  requested_at: 2026-07-20T14:21:54+09:00
  approved_by: user
  approved_at: 2026-07-20
---

# クローズドテスト完了後に課金テストを行う予定へ変更

## 変更種別

`change`

## 確定した実施順序

1. 2026年7月23日頃まで現在のクローズドテストへ変更を加えず待つ。
2. 日付だけで判断せず、Play Consoleで12人以上・14日間連続の条件達成を確認する。
3. クローズドテストトラックを停止・削除せず、製品版アクセス申請を提出する。
4. 申請提出後、既存クローズドテストとは別の課金テスト用トラックでBillingテストを行う。
5. 課金テスト済みの公開候補AABを確定する。
6. v0.7.3で製品版アクセスの審査結果と公開情報を確認する。

## 運用境界

- 現在のクローズドテストは2026年7月20日時点で有効、12人、11日連続である。
- 「クローズドテスト終了」は14日条件を満たす意味とし、トラックの停止・削除は行わない。
- 課金テスト用AABを現在のクローズドテストへ追加・置換しない。
- 課金テスト用トラックの作成・公開とライセンステスター登録は、14日条件達成と製品版アクセス申請後に行う。

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 | 根拠 |
|---|---|---|---|---|
| change | `TASKS.md` | v0.7.2内の実施順序、開始条件、製品版アクセス申請、課金テストを再配置 | クローズドテスト条件を保護するため | ユーザー指示 |
| change | `ROADMAP.md` | 12人・14日確認と製品版アクセス申請をv0.7.2へ前倒し | バージョン順と実施順を一致させるため | ユーザー指示 |
| change | `docs/play/BUILD_COMMANDS.md` | 課金テスト開始を条件達成・申請後と明記 | 誤って既存クローズドテストへAABを登録しないため | ユーザー指示 |
| add | 本ファイル | 予定変更と運用境界を記録 | 変更追跡のため | AI社員ルール |

## 検証

- `TASKS.md`で製品版アクセス申請が課金テストより前に並んでいることを確認する。
- `ROADMAP.md`で12人・14日確認と申請の移行先がv0.7.2になっていることを確認する。
- `rg`で旧表記「クローズドテスト終了」と重複した未完了申請タスクが残っていないことを確認する。
- `git diff --check`を実行する。
- コード、バージョン、AAB、Play Console設定は変更しない。

## ビルド生成物

今回の作業では生成しない。文書変更のみのため。

## 残課題

- Play Consoleの12人・14日達成表示は2026年7月23日頃に再確認する。
- 製品版アクセス申請文面は達成後に最終確認する。
- 課金テスト用Googleアカウントと別トラックは、申請提出後に確定する。
