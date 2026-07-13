---
tracking_id: TRACK-20260710-093229
app: RakuteRoom
app_path: "@RakuteRoom/"
ai_employee: Codex
work_type: code
status: applied
created_at: 2026-07-10T09:32:29+09:00
updated_at: 2026-07-10T09:32:29+09:00
source_request_summary: "Delete caches for each account and add cache deletion feature."
version_before: 2.3.33
version_after: 2.3.33
version_change_required: false
version_change_reason: "User requested cache deletion, feature addition, Git/build flow; no version bump was requested in this turn."
git:
  repo_path: "C:/App_Make/@RakuteRoom"
  branch: master
  commit_before: 91942fab6429434bb46814ba4ae86b032864d5ec
  commit_after: 1e2514fa07226ac6cc8b16e2bdf2d4267954cf5f
  status_after: clean
approval:
  required: true
  reason: "Deletes local cache directories for all RakuteRoom account folders."
  approved_by: "User request"
  approved_at: 2026-07-10T09:32:29+09:00
---

# RakuteRoom All Account Cache Clear

## Actual Cache Deletion

Deleted cache directories under these account folders:

- `rakuteroom`
- `RakuteRoom-__default__`
- `RakuteRoom-父`
- `rakuteroom-母`

Deleted directory names were limited to:

- `Cache`
- `Code Cache`
- `GPUCache`
- `DawnGraphiteCache`
- `DawnWebGPUCache`
- `blob_storage`
- `Shared Dictionary`
- `VideoDecodeStats`

Protected data not targeted: `config.json`, `history`, `logs`, `profiles`, `Local Storage`, `IndexedDB`, `Network`, API settings, and post history.

## Changes

| Type | File | Summary |
| --- | --- | --- |
| change | `main.js` | Added guarded all-account cache directory deletion and IPC handler `cache:clear-all-accounts`. |
| change | `preload.js` | Exposed `clearAllAccountCaches`. |
| change | `renderer/index.html` | Added `全アカウントキャッシュクリア` button. |
| change | `renderer/renderer.js` | Added confirmation, status display, and event binding for all-account cache clearing. |

## Verification

| Command | Result |
| --- | --- |
| Safe PowerShell removal of listed cache dirs | pass, no deletion errors |
| Cache target directory remaining check | pass, `0` remaining |
| `node --check main.js` | pass |
| `node --check preload.js` | pass |
| `node --check renderer/renderer.js` | pass |
| `git diff --check -- main.js preload.js renderer/renderer.js renderer/index.html` | pass |
| `git commit -m "Add all-account cache clearing"` | pass, commit `1e2514fa07226ac6cc8b16e2bdf2d4267954cf5f` |
| `npm run build` | pass |

## Build Artifact

| Path | Size | SHA256 |
| --- | ---: | --- |
| `C:/App_Make/@RakuteRoom/dist/RakuteRoom-2.3.33-x64.exe` | 84447900 bytes | `3F5BE31211728C2ECF3D7F1FE30B8C6DF2C59D02AE135BC09954FB97DE22096C` |

## Final State

- `C:/App_Make/@RakuteRoom` Git status: clean.
- No push was requested.
