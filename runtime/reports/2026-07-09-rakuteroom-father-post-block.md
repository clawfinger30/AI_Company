---
tracking_id: TRACK-20260709-183409
app: RakuteRoom
app_path: "@RakuteRoom/"
ai_employee: Codex
work_type: code
status: applied
created_at: 2026-07-09T18:34:09+09:00
updated_at: 2026-07-09T18:38:00+09:00
source_request_summary: "Account 父 cannot post after noon; investigate errors and fix post candidate/count behavior."
version_before: 2.3.33
version_after: 2.3.33
version_change_required: false
version_change_reason: "User did not request version/build for this bug-fix turn."
git:
  repo_path: "C:/App_Make/@RakuteRoom"
  branch: master
  commit_before: 9a852039e9420f0f819f945315925d31f491fda0
  commit_after: uncommitted
  status_after: "M main.js; M renderer/renderer.js; M runner/webviewRunner.js"
approval:
  required: true
  reason: "Post history/account/duplicate candidate behavior is touched by the fix."
  approved_by: "User request in current conversation"
  approved_at: 2026-07-09T18:34:09+09:00
---

# RakuteRoom father account post block investigation

## Findings

- `C:/Users/home/AppData/Roaming/RakuteRoom-父/logs/default/post-2026-07-09.log` shows no post success after 2026-07-09 12:26:19.
- After 12:30, the same log contains 116 duplicate skip lines, 774 load error lines (`ERR_FAILED` or `ERR_ABORTED`), and 10 `Object has been destroyed` lines.
- `history/default/posts.jsonl` contains 17 records with `posted_at` on 2026-07-09; the last is 12:26:19.
- `logs/post-history-2026-07-09.txt` contains one text-history post record at 12:26:19. This mismatch is why history-source-specific daily counts are needed.

## Changes

| Type | File | Summary | Reason |
| --- | --- | --- | --- |
| change | `main.js` | Daily count now prefers the active profile JSONL source when available. | Avoid cross-profile/global text log counts. |
| change | `renderer/renderer.js` | Daily count date/source/profile handling and clearer count reset logging. | Fix stale date/count behavior. |
| change | `runner/webviewRunner.js` | Active profile is applied to post history/log manager; duplicate skipped candidates are excluded from the current plan; destroyed webview stops the run; post progress logs separate posted/excluded/unprocessed; exhausted candidate-list cache is cleared so the next run can fetch fresh candidates. | Prevent the father account from retrying the same duplicate/broken candidate list and producing misleading logs. |

## Verification

| Command | Result | Note |
| --- | --- | --- |
| `node --check main.js` | pass | Syntax check. |
| `node --check renderer/renderer.js` | pass | Syntax check. |
| `node --check runner/webviewRunner.js` | pass | Syntax check. |
| `git diff --check -- main.js renderer/renderer.js runner/webviewRunner.js` | pass | Whitespace/conflict marker check. |

## Build

- Skipped. Version/build was not requested for this turn.

## Remaining Risk

- Live Rakuten ROOM posting was not executed from Codex, so the next actual confirmation must be from an app run with account `父`.
