# Persistent project memory

Read this document at the start of future work on this project. Keep it updated with confirmed decisions, important constraints, and the next discussion point. Do not record speculative features as accepted requirements.

## Approved scope — mandatory change restriction

- The user approved `docs/app_scope.md` on 2026-10-18.
- **Do not modify the approved scope without the user's explicit authorization**, including changes to functionality, examples, wording, formatting, or navigation.
- Technical design, implementation, reviews, inferred improvements, or discovered inconsistencies do not authorize scope edits. Explain any proposed change in chat and obtain explicit agreement before applying it.
- An explicit user request to change specific scope content authorizes those requested edits only; do not ask again for authorization already given.
- Do not remove or relax this restriction without the user's explicit agreement. Keep implementation and future design aligned with the approved scope.

## Project

- Working directory/project name: JazykAI.
- Product: An AI-supported Telegram bot for learning and improving foreign language skills.
- Initial learning language: Czech.
- Translation and explanation language: Russian.

## Collaboration preferences

- The user wants to describe desired app behavior step by step through discussion.
- Start with a high-level functionality scope and learning experience.
- Do not focus on architecture, programming languages, or frameworks at this stage.
- Do not invent or implement features before they have been discussed and agreed.
- When editing the user's feature descriptions, improve formatting and wording without changing any logic.
- Keep the scope logically grouped and maintain the navigation links for every section when reorganizing it.

## Documents

- `docs/app_scope.md`: The approved product scope and source of truth for agreed functionality; changes require explicit user authorization.
- `agent.md`: Persistent project memory, requested explicitly by the user; kept at the project root.

## Current state

- Initial documents created on 2026-10-12.
- On 2026-10-18, the user supplied two feature descriptions, now recorded in `docs/app_scope.md`: an advanced Czech/Russian translator with supporting information and examples, and a word/phrase database with practice reminders.
- Saved vocabulary follows five practice steps, initially on days 1, 2, 4, 7, and 10. Retries can add attempts. An incorrect answer resets progress to reminder 1 for the following day.
- First release: invitation-only private Telegram chats; separate vocabulary/settings/progress per user; text-only Czech/Russian words, phrases, and short sentences. Voice, images, documents, group chats, long texts, other languages, and conversation practice are outside scope.
- Completed translations require labelled meanings/contextual equivalents, brief Russian explanations, and at least two Czech examples overall with Russian translations, with at least one example per distinct meaning or context. Parts of speech tailor content but do not determine saving/grouping.
- Approved grouping: one entry can be one Czech expression with several confirmed meanings (kolej → общежитие; рельс), or a confirmed group of related Czech expressions (the user's билет example). All meanings/targets share one sequence and schedule. "All meanings" means the meanings presented and confirmed, not an exhaustive dictionary.
- Unrelated Russian concepts (лук) require clarification; related contextual equivalents can be grouped. Czech synonyms are labelled reference alternatives by default; they become required targets only when explicitly saved as targets or included in a related group.
- The five exercise types are mandatory. Translation tasks cover all saved meanings/contextual equivalents. Steps 3–5 require one, one, and two Czech sentences respectively; never increase counts for larger entries. The user explicitly clarified that the sentence tasks in steps 3–4 cover at least one required meaning/expression; step 5 covers all required meanings/expressions across the pair. One accepted alternative per context is sufficient; do not require every synonym.
- Grading is strict about spelling and Czech diacritics: typos and missing/incorrect diacritics trigger reset. Sentence tasks must use required targets, their grammatical forms, or explicitly accepted contextual alternatives. Correct unrelated grammar without reset. Ask for missing parts before grading; incomplete coverage must be revised within the same sentence count. Any incorrect required answer resets the whole entry and clears that attempt's partial completion.
- Uncertain interpretation calls for clarification; processing failures preserve progress. A user can request rechecking the last evaluation, with progress/schedule corrected if needed. Revealing an answer or saying "I don't know" counts as an unsuccessful attempt.
- Validate manual entries and edits, suggest fixes, but let the user explicitly apply their original content despite AI concerns. Practice uses confirmed meanings/targets. Merge new meanings into existing entries after confirmation; adding/removing/changing meanings or targets resets the whole entry, including completed entries. Duplicate saves preserve progress. Example/formatting edits preserve progress; deletion removes pending exercises after confirmation.
- After successful step 5, mark practice completed and stop automatic exercises. Keep the entry searchable; manual restart is supported.
- Reminder timing: one configured daily notification time for all vocabulary, with a timezone. Only one step per saved entry is active. Delays shift later steps, preserving intervals of 1, 2, 3, and 3 days between successful steps.
- Approved daily practice flow (scope sections "Scheduling and reminder controls" and "Practice sessions"): one notification opens a session; exercises are presented sequentially with feedback. Session size is configurable, with optional continuation for more due entries. This replaces the earlier daily reminder limit; it is not a strict daily exercise cap.
- Session counting: one entry's active step counts as one exercise even if multi-part. Preserve successful parts across interruptions, but advance only when the entire step succeeds. Session effort can vary with entry size.
- Oldest overdue vocabulary is practiced first. Unanswered or unfinished exercises remain pending in the next day's queue without separate automatic notifications or changes to progress. Session limits can defer them; per-word schedules shift accordingly.
- Approved calendar behavior: local calendar days, first exercise tomorrow; no second daily invitation after time/timezone changes, no burst of missed notifications, and no invitation when nothing is due. Pausing freezes learning schedules and notifications; exercise postponement moves eligibility to tomorrow. Invitation postponement allows manual practice later without another automatic notification that day.
- Default planned session size is 10. Unlimited saving and no separate new-word admission limit in this release; backlog growth is possible.
- Only one session per user. Block translation requests during an active session until the user finishes or stops it, without grading those requests as answers. Preserve work overnight, resume current sessions from old buttons, and never advance twice for repeated answers.
- Setup asks timezone, daily time, and session size. Main controls: Translate, My vocabulary, Practice, Settings, with Russian labels. Manual practice of due entries and deletion of vocabulary/settings are included.
- All agreed grouping, fixed sentence-count, grading, merge, and session-counting changes are incorporated in `docs/app_scope.md`, with acceptance scenarios. The user approved the whole scope on 2026-10-18 and explicitly prohibited further changes without agreement. Technical design has not started; begin it when requested.
- The scope has been reorganized into product boundaries, setup, translation, vocabulary, exercises, grading, scheduling, sessions, examples, and acceptance scenarios, with linked navigation. The reformat preserved behavior; conflicting older sentence-coverage wording was aligned with the user's explicit clarification above.
