---
tracking_id: TRACK-20260710-104849
app: RakuteRoom
app_path: "@RakuteRoom/"
ai_employee: Codex
work_type: code
status: applied
created_at: 2026-07-10T10:48:49+09:00
updated_at: 2026-07-10T10:48:49+09:00
source_request_summary: "日付が変わったタイミングでキャッシュをクリアして問題ないか。影響がないならクリアしたい。"
version_before: 2.3.34
version_after: 2.3.34
version_change_required: false
version_change_reason: "User asked whether to add daily cache clear; no version/build/commit requested in this turn."
git:
  repo_path: "C:/App_Make/@RakuteRoom"
  branch: master
  commit_before: 22aed7593b6895c6d23ec09c077c5a58ae98096b
  commit_after: uncommitted
  status_after: "M main.js; M renderer/renderer.js"
approval:
  required: true
  reason: "Local cache directories are deleted automatically once per day."
  approved_by: "User request"
  approved_at: 2026-07-10T10:48:49+09:00
---

# RakuteRoom Daily Cache Clear

## Decision

- Daily cache clearing is acceptable when limited to browser cache directories.
- Settings, login-related storage, post history, logs, `Local Storage`, `IndexedDB`, and `Network` are not targeted.
- `Shared Dictionary` was removed from the deletion list because it is commonly locked while Chromium/Electron is running.

## Changes

| Type | File | Summary |
| --- | --- | --- |
| change | `renderer/renderer.js` | Added one-per-day cache clear at post start and when date change is detected during the post loop. |
| change | `main.js` | Removed `Shared Dictionary` from the all-account cache deletion target list to avoid locked-file errors. |

## Verification

| Command | Result |
| --- | --- |
| Safe cache deletion command for target cache directories | partial pass, deletion succeeded but running Electron/Chromium recreated some `Cache` / `Code Cache` directories |
| `node --check main.js` | pass |
| `node --check preload.js` | pass |
| `node --check renderer/renderer.js` | pass |
| `node --check runner/webviewRunner.js` | pass |
| `git diff --check -- main.js renderer/renderer.js` | pass |

## Final State

- App repo has uncommitted changes in `main.js` and `renderer/renderer.js`.
- Some cache directories can be recreated immediately while the app/Electron process is active. Full on-disk zero state requires clearing while the app is stopped.
- Build and version bump were not run because they were not requested in this turn.
