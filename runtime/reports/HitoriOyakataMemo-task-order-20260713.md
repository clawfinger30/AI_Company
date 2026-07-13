---
tracking_id: TRACK-20260713-154859
app: HitoriOyakataMemo
app_path: AndoroAPP/HitoriOyakataMemo/
ai_employee: Codex
work_type: docs
status: applied
created_at: 2026-07-13T15:48:59+09:00
updated_at: 2026-07-13T15:48:59+09:00
source_request_summary: v0.6.0の残タスクを移行して完了扱いにし、以後はバージョンの若い順に進める運用をAI社員ルールへ明記する
version_before: 0.6.1+69
version_after: 0.6.1+69
version_change_required: false
version_change_reason: コードや配布物ではなく、タスク運用とドキュメント整理のため
---

# HitoriOyakataMemo タスク順序運用ルール追加

## 内容

v0.6.0の残タスクに後続バージョンの作業が混在していたため、未実装部分を後続バージョンへ移行し、v0.6.0内に未完了チェックを残さない運用へ整理した。

今後は、`TASKS.md` と `ROADMAP.md` のバージョンが若い順に処理する。後続バージョンへ進む前に、現在バージョンのタスクは完了または後続版へ移行済みであることを確認する。

## 変更ファイル

| 種別 | ファイル | 変更内容 | 理由 |
| --- | --- | --- | --- |
| change | `AGENTS.md` | バージョン順タスク運用を追記 | 全AI作業の入口で同じ運用を確認できるようにする |
| change | `00_ai_company/company_rules/employee-handbook.md` | タスクは若いバージョン順に処理し、未完了を残して次へ進まない規則を追加 | AI社員共通ルールへ反映するため |
| change | `00_ai_company/app_departments/HitoriOyakataMemo/app-rules.md` | HitoriOyakataMemoのTASKS/ROADMAP運用を追加 | アプリ固有の運用として明記するため |
| change | `AndoroAPP/HitoriOyakataMemo/TASKS.md` | v0.6.0残タスクを完了または後続版へ移行 | v0.6.0に未完了チェックを残さないため |
| change | `AndoroAPP/HitoriOyakataMemo/ROADMAP.md` | v0.6.0残項目を完了、後続タスクを追記 | ロードマップとTASKSの状態を一致させるため |

## Git

```yaml
git:
  repo_path: C:/App_Make/AndoroAPP/HitoriOyakataMemo
  branch: main
  commit_before: 7d071d0
  commit_after: 6d95cbc
  status_before: clean
  remote: https://github.com/clawfinger30/oyakata_memo.git
```

`00_ai_company` と `AGENTS.md` はアプリGitリポジトリ外のため、このアプリリポジトリのコミットには含まれない。

## 検証

- v0.6.0節に未完了チェックが残っていないことを確認した。
- `git diff --check` を実行し、問題がないことを確認した。
- アプリリポジトリの差分が `TASKS.md` / `ROADMAP.md` に限定されていることを確認した。
- アプリリポジトリの変更は `6d95cbc` として `origin/main` へPush済み。
