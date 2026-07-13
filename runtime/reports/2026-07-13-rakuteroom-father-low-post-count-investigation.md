---
tracking_id: TRACK-20260713-082217
app: RakuteRoom
app_path: "@RakuteRoom/"
ai_employee: Codex
work_type: investigation
status: applied
created_at: 2026-07-13T08:22:17+09:00
updated_at: 2026-07-13T08:22:17+09:00
source_request_summary: "父アカウントだけ投稿件数などが少なすぎる気がする。他アカウントとジャンルは違うが原因を探す。"
version_before: 2.3.35
version_after: 2.3.35
version_change_required: false
version_change_reason: "Investigation only; no code or setting change requested."
git:
  repo_path: "C:/App_Make/@RakuteRoom"
  branch: master
  commit_before: 33511ba
  commit_after: 33511ba
  status_after: clean
approval:
  required: false
  reason: "Read-only log/config investigation. Secrets were not modified."
---

# RakuteRoom Father Account Low Post Count Investigation

## Findings

- Father profile current history is lower than the other active profiles:
  - `父`: 2026-07-10 64, 2026-07-11 97, 2026-07-12 56, 2026-07-13 2.
  - `母`: 2026-07-10 150, 2026-07-11 170, 2026-07-12 140, 2026-07-13 10.
  - `貴久`: 2026-07-10 120, 2026-07-11 157, 2026-07-12 131, 2026-07-13 7.
- On 2026-07-13, father spent much longer building the product list:
  - Father rebuilt the list from 07:10 and finished product selection at 07:58.
  - Mother finished product selection at 07:30.
  - Takahisa finished product selection at 07:35.
- Father product candidates were materially lower:
  - Father: duplicate removal 2678 -> 1339, exclusion filter 1339 -> 1316.
  - Mother: duplicate removal 4396 -> 2197, exclusion filter 2197 -> 2190.
  - Takahisa: duplicate removal 5678 -> 2839, exclusion filter 2839 -> 2828.
- Father selected broader low-yield genres and used top 2 shops per genre:
  - Father `POST_RANKING_SHOP_COUNT=2`, with 17 genre groups and 27 final shop names.
  - Mother/Takahisa `POST_RANKING_SHOP_COUNT=3`, with 11 genre groups and 27 final shop names.
  - Father included categories such as mobile communication, books, travel/tickets, services, PC/peripherals, and several categories where the top shops returned very few products.
- Father old carryover list continued at 07:00 before the rebuilt list:
  - It processed item 13/15 through 15/15, resulting in duplicate/load-failure skips, then rebuilt the product list.

## Conclusion

The father account's low count is not primarily caused by a posting-form failure in the provided logs. The main causes are:

1. Product-list creation starts later and takes longer for the father profile.
2. Father ranking genres generate fewer useful product candidates.
3. Father uses fewer ranking shops per genre (`2` vs `3`), while many selected genres are low-yield.
4. Carryover list processing at 07:00 consumed additional time before the new list started.

## Verification

| Check | Result |
| --- | --- |
| Profile history JSONL day counts | verified |
| 2026-07-13 post logs for father/mother/Takahisa | verified |
| 2026-07-13 freekeyword logs for father/mother/Takahisa | verified |
| Account config non-secret settings | verified |
| Code changes | none |

## Review

- No secrets were reported.
- No files under the app repository were changed.
- No live posting or settings modification was executed.
