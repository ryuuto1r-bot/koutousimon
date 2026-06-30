# Design QA

- Source visual truth: `/Users/user/.codex/generated_images/019dcfce-c36b-7ac2-8b0c-780d9af829c3/call_GB84IfvvL7fFXP25naep8gSE.png`
- Implementation screenshot: `/tmp/koutousimon-oral-top-desktop.png`
- Mobile screenshot: `/tmp/koutousimon-oral-top-mobile.png`
- Comparison evidence: `/tmp/koutousimon-oral-top-comparison.png`
- Viewports: desktop `1440 x 900`, mobile `390 x 844`
- State: 数学・経済タブ、ローカル学習記録なし

## Full-View Comparison

The implementation follows the selected visual's hierarchy: a compact daily summary, three clear practice-entry rows, and a separate unmastered-question summary. The existing category controls, filters, and question-card format remain unchanged below the redesigned menu, as requested.

## Focused Region Comparison

The focused comparison covers the complete oral-exam menu and the start of the preserved question-card list. It confirms that the new menu reads as a compact launcher while the familiar study workflow remains directly below it.

## Findings

- No actionable P0, P1, or P2 findings remain.
- The concept's sample question list was intentionally not adopted because the user requested that the current question format remain unchanged.
- Weak and review practice buttons are disabled when no eligible questions exist, preventing empty practice sessions.
- Daily review and weakness metrics open their matching card lists directly; zero-count metrics are disabled.

## Required Fidelity Surfaces

- Typography: Clear hierarchy between the title, daily metrics, practice rows, and supporting counts.
- Spacing: Stable two-column desktop layout and single-column mobile stack with no horizontal overflow.
- Colors: Navy primary action, cyan progress, and semantic weak/review/mastery colors follow the selected direction.
- Controls: Each practice row has a single explicit start button with an accessible label.
- Existing content: Search, categories, filters, cards, answer reveal, and mastery actions remain intact.

## Patches Made

- Replaced only the oral-exam top menu with the selected compact dashboard.
- Added important, weak-only, and due-review four-question launchers.
- Added daily progress metrics and an S/A/B unmastered summary.
- Connected review and weakness metrics to their existing card filters.
- Shortened practice descriptions so they remain fully readable on mobile.
- Connected the unmastered summary to the existing unmastered-card filter.
- Preserved the existing question cards and study interactions.

## Verification

- Important practice launches the existing mock modal with `Question 1 / 4`.
- Unmastered summary switches to the existing unmastered-card view and can return to all cards.
- Marking one card for review enables the weakness metric; selecting it shows exactly that weak card.
- Existing question cards still expose their original answer-review controls.
- Desktop and mobile layouts have no horizontal overflow.
- Browser console contains no errors.
- Mock interviewer, interview-card practice, and oral-exam practice all include a previous-question action.
- Previous-question actions are disabled on the first question and reset answer, timer, and follow-up state when navigating back.
- The mock interviewer footer remains within the `390 x 844` mobile viewport with no horizontal overflow.
- Interview-guide mastery rows are actionable: memorized, shaky, review, and unchecked counts filter the card list to the selected status and scroll to the results.
- Selecting the same mastery row again or using `全て表示` restores the full guide list.
- Interview-guide mastery can switch between cumulative and per-day views without deleting cumulative progress.
- Daily guide status is stored by date, starts unchecked on dates without records, and remains available when returning to that date.
- The cumulative/daily selector and date input fit within the `390 x 844` mobile viewport with no horizontal overflow.
- Interview-guide cards now render in topic order with visible section headers: 志望動機・自己紹介, 九大・学科理解, ロボットアイデア甲子園, SENKAY・ビジコン, 仮想通貨ツール・個人ビジネス, 卒研・技術実装, 学生会・人物面, 経済理論・興味分野, 数学・統計の説明, その他メモ.
- All 90 guide cards are assigned to exactly one topic group with no duplicate or missing IDs, while existing card IDs remain unchanged for saved progress.
- Mobile guide view at `390 x 844` still has no horizontal overflow after adding topic headers and sequential display labels.
- Hidden interview-guide cards now show a rose `削除` action inside 資料管理; the action is persisted with `deletedGuideSections` and removes that card from the guide list, practice pool, and guide totals.
- The hidden-guide management banner now explicitly says users can either restore hidden cards or delete unnecessary ones.
- Restoring a hidden interview-guide card from 資料管理 now changes the action to `元の一覧へ戻す`, exits hidden-only mode, clears guide filters, and returns the restored card to the normal list immediately.
- Restoring a hidden oral-exam question from the hidden-only view now uses the same `元の一覧へ戻す` behavior and exits hidden-only mode after the modal closes.
- A one-time guide-data migration restores `大学進学後の進路`, `院の進学は考えているか`, and `高専で学んできたこと` from hidden interview-guide sections for existing synced users, then records `restore-guide-visible-2026-06-30` so later manual hiding still works.
- Interview-guide practice now shows a daily auto-generated 15-card set based on the selected date and current guide progress, prioritizing review, shaky, later, low-count, and recent cards while preserving the existing random mode as a secondary action.
- The daily guide-practice start button opens the 15-question practice modal, and the mock timer now renders as minute-second text such as `01:00` / `00:59`.
- Oral-exam practice now has a daily auto-generated 15-question set based on the selected date and current progress, prioritizing due, weak, unmastered, untouched, and important questions; oral mock buttons now mark questions as `review` or `mastered` before advancing.
- Oral-exam progress now has a top-level cumulative/daily mastery card; daily mode uses the selected date but calculates the percentage against all oral questions, while also showing how many were studied that day.

final result: passed
