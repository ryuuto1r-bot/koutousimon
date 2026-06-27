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

final result: passed
