# Application scope

**Status:** Approved by the user on 2026-10-18.

> **Change control:** This approved document must not be changed without the user's explicit authorization. This restriction includes requirements, examples, wording, formatting, and navigation. Technical design or implementation work does not authorize scope edits. Discuss proposed changes with the user before applying them; an explicit request to change specific content authorizes only those requested changes.

## Navigation

- [Product and release scope](#product-and-release-scope)
    - [Product goal](#product-goal)
    - [Release boundaries](#release-boundaries)
    - [Outside the first release](#outside-the-first-release)
    - [Design approach](#design-approach)
- [Setup and main controls](#setup-and-main-controls)
- [Translation](#translation)
    - [Required response content](#required-response-content)
    - [Meanings and clarification](#meanings-and-clarification)
    - [Synonyms and practice targets](#synonyms-and-practice-targets)
- [Personal vocabulary](#personal-vocabulary)
    - [Saved entries](#saved-entries)
    - [Saving and duplicate handling](#saving-and-duplicate-handling)
    - [Manual additions and validation](#manual-additions-and-validation)
    - [Editing and deletion](#editing-and-deletion)
    - [Completion and restart](#completion-and-restart)
- [Practice exercises](#practice-exercises)
    - [Five-step sequence](#five-step-sequence)
    - [Meaning coverage and sentence counts](#meaning-coverage-and-sentence-counts)
- [Answer checking](#answer-checking)
    - [Correct and incorrect answers](#correct-and-incorrect-answers)
    - [Incomplete answers](#incomplete-answers)
    - [Uncertainty, failures, and rechecks](#uncertainty-failures-and-rechecks)
- [Scheduling and reminder controls](#scheduling-and-reminder-controls)
    - [Daily notification](#daily-notification)
    - [Calendar and intervals](#calendar-and-intervals)
    - [Delays and retries](#delays-and-retries)
    - [Pause and postponement](#pause-and-postponement)
- [Practice sessions](#practice-sessions)
    - [Session flow and queue](#session-flow-and-queue)
    - [Session size and exercise counting](#session-size-and-exercise-counting)
    - [Continuity and interruptions](#continuity-and-interruptions)
- [Examples](#examples)
    - [Czech word explanation](#czech-word-explanation)
    - [Russian phrase translation](#russian-phrase-translation)
    - [Saving and practicing borec](#saving-and-practicing-borec)
    - [Related expression group](#related-expression-group)
    - [Daily practice invitation](#daily-practice-invitation)
- [Acceptance scenarios](#acceptance-scenarios)
- [Final scope review](#final-scope-review)

## Product and release scope

### Product goal

Create an AI-supported Telegram bot that helps learners learn Czech and advance their Czech language skills. Use Russian for translations and explanations.

The core learning flow is:

~~~text
Translate or add vocabulary manually
                 |
       Confirm and save an entry
                 |
       Practice the entry when due
                 |
          Receive feedback
                 |
    Advance / restart / complete
~~~

### Release boundaries

| Area | Agreed scope |
| --- | --- |
| Interface | Telegram bot, private chats only. |
| Access | Invitation only. Uninvited users cannot access learning functionality. |
| Learning language | Czech. |
| Translations and explanations | Russian. |
| Input and output | Text only: individual words, phrases, and short sentences in Czech or Russian. |
| AI responsibilities | Translation, usage explanations and examples, vocabulary validation, exercise generation, and answer checking. |
| Personal learning data | Separate vocabulary, settings, sessions, and progress for each user. |

### Outside the first release

- Voice messages, audio, images, and document processing.
- Group chats, additional languages, and long-text translation.
- Conversation practice and other learning modes beyond the vocabulary exercises defined here.
- A separate limit or waiting list controlling how many newly saved entries begin practice each day.

### Design approach

Define functionality and the learning experience before choosing technical architecture, programming languages, or frameworks. Develop the scope through step-by-step discussion with the user.

Distinguish confirmed requirements from ideas and open questions. Suggested features become requirements only after agreement with the user.

## Setup and main controls

During initial setup, ask the invited user for their:

- Timezone.
- Daily notification time.
- Preferred session size, initially **10 exercises**.

Provide the main actions **Translate**, **My vocabulary**, **Practice**, and **Settings**, with Russian user-facing labels and explanations.

Users can start practice manually, pause and resume learning, and delete their saved vocabulary and settings after confirmation. The behavior of these actions is defined in the sections below.

## Translation

The bot translates individual words, phrases, and short sentences in both directions: **Czech → Russian** and **Russian → Czech**.

### Required response content

Every completed translation response must include:

1. The main translation, with distinct meanings or related contextual equivalents labelled separately when applicable.
2. A brief explanation in Russian.
3. **At least two Czech usage examples overall**, each with a Russian translation, and at least one example illustrating every distinct meaning or contextual equivalent included in the response.

Optional information must not replace these mandatory parts. Parts of speech help shape explanations and exercises but do not determine how meanings are grouped or saved.

### Meanings and clarification

| Situation | Required behavior |
| --- | --- |
| An isolated Czech expression has several meanings. | Present its relevant common meanings as separately labelled groups within one translation. |
| Several Russian equivalents describe the same Czech usage. | Keep those equivalents in one meaning group. |
| Context identifies a particular usage. | Explain that usage clearly. Ask for clarification if it cannot be determined reliably. |
| Russian input represents unrelated concepts, such as «лук». | Clarify the intended concept before producing the completed Czech translation. |
| A Russian concept has related Czech equivalents for different contexts, such as «билет». | The equivalents may be presented and saved together as a confirmed group, with each context labelled separately. |
| A request contains several items and it is unclear what to save. | Clarify which item or related group should be saved. |

**“All meanings” means the meanings presented and confirmed in the translation**, rather than an exhaustive dictionary entry. The included meanings must be clear before saving. Additional meanings can be added later through vocabulary management.

### Synonyms and practice targets

Present Czech synonyms and other alternatives with explanations of their differences in meaning and usage.

Choose **one main Czech expression as the practice target by default**. Alternatives remain reference information unless the user explicitly saves them as separate targets or includes them in a related expression group.

For example, a translation of «красивый» may explain **krásný**, **hezký**, **pěkný**, and **nádherný**. Showing the alternatives does not automatically require the learner to practice all four.

## Personal vocabulary

Users can view, search, add, edit, and delete saved vocabulary.

### Saved entries

**One saved entry** represents either:

- One Czech expression with its confirmed meanings.
- A confirmed group of related Czech expressions.

Each entry has **one shared five-step sequence, schedule, and progress status**.

| Saved entry | Learning content | Progress |
| --- | --- | --- |
| kolej | общежитие; рельс | One shared five-step sequence |
| билет | vstupenka; jízdenka; letenka; zkušební otázka; průkazka | One shared five-step sequence |

Each entry contains:

| Content | Purpose |
| --- | --- |
| Czech expression or related expression group | Identifies the vocabulary being learned, with a display label such as «билет» where needed. |
| Separately labelled meanings or contexts | Includes Russian equivalents, explanations, and Czech examples with Russian translations. |
| Practice targets and accepted alternatives | Identifies the Czech expressions required or explicitly accepted for each context. |
| Optional reference alternatives | Explains related Czech expressions and their nuances without automatically making them practice targets. |
| Shared practice status, step, and schedule | Tracks the entry as a whole. Meanings do not have independent schedules. |

Meaning groups and contextual equivalents retain their labels so they are not treated as interchangeable.

### Saving and duplicate handling

Vocabulary can be saved after a translation or added manually.

When saving a translation, save **all confirmed meaning groups or related contextual equivalents together** in one entry, preserving their labels and explanations. “Save this” refers to the most recent clearly identified translation or confirmed group; ask for clarification if the reference is ambiguous.

| Save request | Result |
| --- | --- |
| The same expression or group and its meanings are already saved. | Inform the user. Do not create a duplicate or reset progress. |
| An existing expression or group has newly encountered meanings or contextual equivalents. | Show the proposed additions and ask for confirmation before merging them into the existing entry. |
| The user confirms new meanings or practice targets. | Restart the shared sequence, with step 1 due the following day. This also applies to completed entries. |

### Manual additions and validation

For manually added vocabulary, generate missing translations and examples and show the completed entry for confirmation before saving.

Explicitly validate manual additions and changes to Czech expressions, Russian translations, meaning/context groups, and examples for linguistic correctness and consistency.

If an addition or edit appears incorrect:

1. Explain the concern in Russian and suggest a correction.
2. Let the user accept the correction, revise the entry, cancel, or **explicitly apply their original version despite the concern**.
3. Preserve the user's confirmed content; do not silently replace it.

AI validation must not block a user-confirmed specialized, unfamiliar, or newly coined meaning. Practice uses the confirmed meanings and targets. A previous validation concern alone must not make all answers for that entry incorrect; ask for clarification if an answer cannot be evaluated reliably.

### Editing and deletion

| Change | Effect on practice |
| --- | --- |
| Add, remove, or change a meaning or practice target. | After confirmation, restart the whole entry at step 1, due the following day, including previously completed entries. |
| Edit an example or correct formatting. | Preserve progress. |
| Delete an entry. | Require confirmation and remove its pending exercises as well. |

### Completion and restart

After a correct answer to step 5, mark the entry as **“practice completed”** and stop automatic exercises for it. Keep the entry searchable.

Completion means finishing this sequence; it does not prove permanent mastery. The user can manually restart a completed entry at step 1, due the following day.

## Practice exercises

### Five-step sequence

Every entry follows the same five exercise types.

| Step | Translation task | Czech sentence task |
| --- | --- | --- |
| 1 | Give Russian equivalents covering every saved meaning or contextual equivalent of the Czech expression(s). | None. |
| 2 | Recall the saved Czech expression(s) from Russian prompts covering every saved meaning or context. | None. |
| 3 | Translate the Czech expression(s) into Russian, covering all saved meanings. | **One sentence** covering at least one required meaning or expression. |
| 4 | Recall the Czech expression(s) from Russian meaning/context prompts covering all saved meanings or contexts. | **One sentence** covering at least one required meaning or expression. |
| 5 | Recall the Czech expression(s) from Russian meaning/context prompts covering all saved meanings or contexts. | **Two sentences** covering all required meanings or expressions across the pair. |

### Meaning coverage and sentence counts

Every exercise explicitly states the meanings or contexts and the number of answers or sentences required. Use enough context to identify the intended usage, especially for sentence tasks.

- **Translation tasks cover all saved meanings or contextual equivalents at every step.**
- **Sentence tasks in steps 3 and 4 cover at least one required meaning or expression.**
- **The sentence task in step 5 covers all required meanings or expressions across two sentences.**
- Do not increase the sentence counts of **1, 1, and 2** because an entry contains more meanings or expressions.
- A sentence can include several required expressions or demonstrate several meanings of one expression through separate uses.
- In step 5, the user may distribute the required content freely between the two sentences. Each sentence need not cover every meaning on its own.
- One appropriate accepted alternative is sufficient for a context. The learner need not list every synonymous Russian equivalent or use every accepted alternative within a context.

## Answer checking

The bot checks translations and Czech sentences, explains mistakes in Russian, and provides corrected translations or sentences.

### Correct and incorrect answers

| Answer characteristic | Evaluation |
| --- | --- |
| A valid translation or sentence formulation matching the required meaning/context. | Accept without requiring the entry's exact Russian wording or every synonym. |
| A required Czech target, its appropriate grammatical form, or an explicitly accepted alternative for that context. | Accept if used correctly and naturally. |
| A reference-only synonym used instead of a required target in a sentence task. | Does not demonstrate use of the required target. |
| A meaning or context different from the one required by the task. | Does not satisfy that requirement. |
| An incorrect translation or incorrect use of a practiced expression. | Incorrect. |
| A spelling error, including a typo or missing/incorrect Czech diacritics. | Incorrect; do not silently normalize or accept it. |
| An unrelated grammar mistake. | Correct it with an explanation without resetting solely for that grammar mistake. Strict spelling and diacritics rules still apply. |
| “I don't know” or a request to reveal the answer. | An unsuccessful attempt, triggering the reset rule. |

Advance only when **the entire active step succeeds**. An incorrect required answer resets **the whole entry** to step 1 for the following day, including grouped meanings or expressions, and clears that attempt's partial completion.

### Incomplete answers

If a required answer or sentence is missing, ask the user to complete the answer before grading the full exercise.

When meaning or expression coverage is incomplete, ask for a revision **within the same sentence count**, rather than additional sentences. Apply the coverage requirements for that step: all meanings in translation tasks, at least one in the sentence tasks of steps 3–4, and all required meanings across the two sentences of step 5.

### Uncertainty, failures, and rechecks

- If an answer cannot be interpreted reliably, ask for clarification instead of automatically treating uncertainty as an incorrect answer.
- A processing failure leaves progress and the exercise unchanged. Allow the user to retry.
- The user can request a recheck of the last evaluation. If the evaluation changes, correct the resulting progress and schedule as well.

## Scheduling and reminder controls

Users configure their timezone and **one daily notification time shared by all vocabulary**. Exercise prompts are delivered within practice sessions.

### Daily notification

- Send one automatic invitation at the configured daily time **if vocabulary is due**.
- Do not send an invitation when nothing is due or a separate automatic notification for each entry.
- Changing the notification time or timezone must not produce a second automatic invitation that day.
- Missed notifications must not be delivered as a burst later.

### Calendar and intervals

Use **calendar days in the user's selected timezone**, not elapsed 24-hour intervals.

| Step | Initial due day after saving | Interval after the previous successful step |
| --- | --- | --- |
| 1 | 1 | Due the day after saving. |
| 2 | 2 | 1 calendar day. |
| 3 | 4 | 2 calendar days. |
| 4 | 7 | 3 calendar days. |
| 5 | 10 | 3 calendar days. |

The initial dates assume every step is completed correctly on its scheduled day. Measure later intervals from the **actual date of the correct answer**.

Saving shortly before midnight may produce a short first interval. Only one step may be active per entry; later steps wait for all required parts of the active step to succeed.

### Delays and retries

| Situation | Scheduling behavior |
| --- | --- |
| An exercise is unanswered. | Keep it pending in the next day's queue, subject to session size and queue order. Do not skip it, mark it incorrect, advance progress, or send a separate automatic notification. |
| A step is completed later than planned. | Shift the remaining steps by that delay, preserving the intervals of 1, 2, 3, and 3 days between successful steps. |
| An exercise is beyond the planned session size. | Keep it pending. The user may continue that day; otherwise, it remains in the next day's queue without progress advancing. |
| An answer is incorrect. | Reset the whole entry to step 1 for tomorrow. Later steps follow the same intervals after successful answers. |

**Delay example:** Step 1 is due on day 1 but completed correctly on day 3. The remaining steps move to days **4, 6, 9, and 12**.

### Pause and postponement

| Action | Behavior |
| --- | --- |
| Pause learning. | Stop automatic notifications and freeze practice schedules until resumed. Preserve progress and remaining intervals so the pause itself does not create more overdue work. |
| Postpone an individual exercise. | Move its eligibility to tomorrow without changing its step; later steps shift accordingly. |
| Postpone today's invitation. | Leave practice available to start manually. The next automatic invitation is tomorrow; do not send another automatic notification that day. |
| Stop a session. | Preserve completed work and leave unfinished exercises pending, as described under [Continuity and interruptions](#continuity-and-interruptions). |

## Practice sessions

### Session flow and queue

The bot groups due entries into a session. It does not automatically send a separate message for each entry.

1. The user starts from the daily invitation or the **Practice** action. Manual practice is available before the notification time and uses only due entries.
2. The bot presents one entry's active step at a time. Its parts may be presented sequentially.
3. The user answers and receives feedback before proceeding to the next exercise.
4. After the planned session, offer **«Продолжить»** if more vocabulary is due.
5. If the user does not start or finish, unfinished exercises remain pending for the following day, preserving their progress.

Practice the **oldest overdue entries first**, using outstanding due dates. Deferring an exercise does not erase how long it has been waiting. Do not bring forward vocabulary that is not yet due to fill a session.

### Session size and exercise counting

The user configures the maximum number of exercises in a planned session; the default is **10**.

**One active step for one saved entry counts as one exercise**, even when it contains several meanings, expressions, questions, or sentences. Ten exercises therefore means up to ten entry steps, not ten individual questions.

This is a planned session size, not a notification limit or a strict daily exercise cap. The user can continue with more due entries that day. Actual effort varies with entry size.

Users can save unlimited vocabulary, and newly saved entries begin practice the following day. There is no separate daily admission limit. Session size bounds the initial session rather than the total backlog, which may grow.

Each entry advances independently when its entire step succeeds. Queue and session delays shift its later steps according to [Delays and retries](#delays-and-retries).

### Continuity and interruptions

- Allow **only one active session per user**. An old notification opens the current session rather than creating another.
- **Block translation requests during an active session.** Explain in Russian that the user must finish or stop the session first. Do not grade a clearly identified translation request as an exercise answer.
- Stopping preserves completed answers, including successful parts of an unfinished step. Partial completion does not advance the step or schedule its successor.
- After stopping, the user can translate and later resume practice.
- A session interrupted overnight resumes with pending work and completed answers preserved.
- Repeating an answer must not advance an exercise twice.

## Examples

These examples illustrate the rules above. Optional reference information does not automatically become a confirmed meaning or required practice target.

### Czech word explanation

This example practices the conversational meaning group of **borec**. The sports reference is background, rather than an additional confirmed practice meaning.

**User request:**

> Что означает слово «borec»?

**Bot response:**

> В современном чешском языке слово **borec** (особенно в разговорной речи) означает «молодец», «красавчик», «крутой парень» или «профи».
>
> Оно используется для выражения восхищения человеком, который отлично с чем-то справился, совершил смелый поступок или является мастером своего дела (хотя изначально и в спортивном контексте это слово переводится как «борец»).
>
> **Примеры использования:**
>
> «Pavel je borec, opravil mi auto za pět minut.»  
> Перевод: Павел просто красавчик (профи), починил мне машину за пять минут.
>
> «To je ale borec!»  
> Перевод: Ну он и крутой чувак! (Вот это молодец!)

### Russian phrase translation

**User request:**

> Как сказать по-чешски «я очень устал»?

**Bot response:**

> **Jsem moc unavený.**
>
> Так можно сказать «я очень устал». Здесь использована форма мужского рода.
>
> **Примеры использования:**
>
> Promiň, dneska s vámi nepůjdu, jsem moc unavený.  
> (Извини, сегодня с вами не пойду, я очень устал.)
>
> Měl jsem v práci těžký den a jsem hrozně unavenej.  
> (У меня был тяжелый день на работе, и я жутко устал.)
>
> **Разные варианты слова «уставший»:**
>
> Если вы хотите разнообразить словарный запас, в чешском есть множество способов описать усталость (все слова приведены в мужском роде):
>
> - **Vyčerpaný** — истощенный, вымотанный. Используется, когда силы на исходе совсем (например, после марафона или тяжелой болезни).
> - **Utahaný** — умотанный. Отличное разговорное слово для состояния после долгого рабочего дня.
> - **Hotový** — разговорный сленг. Буквально переводится как «готовый», означает состояние, когда человек остался совершенно без сил (Jsem úplně hotovej — Я полностью без сил).
> - **Zničený** — разбитый (буквально — «уничтоженный»). Часто используется после тяжелых физических нагрузок.
> - **K.O. (ká ó)** — популярное молодежное и разговорное выражение. Заимствовано из бокса (Jsem K.O. — Я в нокауте / валюсь с ног).

### Saving and practicing borec

The previous turn translated **borec**.

**User request:**

> Сохрани это слово в базу данных.

**Bot action:** Save the confirmed conversational meaning group as one entry.

**Bot response:**

> Слово сохранено. Повторения запланированы на 1-й, 2-й, 4-й, 7-й и 10-й день. Задания появятся в ежедневной тренировке; при задержках даты следующих повторений сдвинутся.

Assuming correct answers on the scheduled days:

| Step | Day after saving | Exercise prompt |
| --- | --- | --- |
| 1 | 1 | Напоминание 1: Переведи слово «borec». |
| 2 | 2 | Напоминание 2: Как будет по-чешски слово «молодец» или «красавчик»? |
| 3 | 4 | Напоминание 3: Переведи слово «borec» на русский. Составь одно предложение на чешском со словом «borec». |
| 4 | 7 | Напоминание 4: Как будет по-чешски слово «молодец» или «красавчик»? Составь одно предложение на чешском с сохранённым чешским словом. |
| 5 | 10 | Напоминание 5: Как будет по-чешски слово «молодец» или «красавчик»? Составь два предложения на чешском с сохранённым чешским словом. |

An incorrect required answer at any step resets the entry according to [Correct and incorrect answers](#correct-and-incorrect-answers).

### Related expression group

The user confirms the following **билет** group:

| Context | Czech target or accepted alternatives |
| --- | --- |
| Event ticket | vstupenka |
| Ground-transport ticket | jízdenka |
| Airline ticket | letenka |
| Examination question | zkušební otázka |
| Identification document | průkaz / průkazka |

**Step 5 sentence task, alongside its translation task:**

> Составь два предложения на чешском, используя изученные варианты слова «билет» для всех пяти контекстов: мероприятие, наземный транспорт, самолёт, экзамен и удостоверение. Распредели их между предложениями как тебе удобно.

The user can combine examination, ground-transport, and identification contexts in the first sentence, and event and airline contexts in the second. One appropriate accepted expression from **průkaz / průkazka** is sufficient.

In steps **3 and 4**, the one-sentence task covers **at least one** required meaning or expression; its translation task still covers all saved meanings or contexts.

### Daily practice invitation

> На сегодня запланировано 12 заданий. Начнём тренировку?
>
> **[Начать] [Отложить]**

## Acceptance scenarios

| Scenario | Expected behavior |
| --- | --- |
| A valid alternative translation matches a required meaning. | Accept if spelling and all exercise requirements are satisfied; advance once only after the whole step succeeds. |
| The user saves kolej with «общежитие» and «рельс». | Create one entry with separate meaning labels and one shared sequence. |
| The user requests a Czech translation of «лук». | Clarify the unrelated concepts before supplying the completed translation. |
| The user confirms the related expressions in the билет group. | Save one shared sequence rather than automatically splitting it into separate entries. |
| A translation task covers several meanings. | Require appropriate equivalents for every required meaning, not every synonym. Ask for missing parts before grading. An incorrect required answer resets the entire entry. |
| A five-context group reaches step 3 or 4. | Require one sentence covering at least one required meaning or expression; retain full coverage in the translation task. |
| A five-context group reaches step 5. | Require all contexts across two sentences without increasing the sentence count. |
| An entry includes reference-only synonyms or accepted contextual alternatives. | Do not automatically require reference-only synonyms; one accepted alternative is sufficient for its context. |
| The user resaves existing meanings. | Preserve progress without a duplicate. |
| The user confirms a new meaning for an existing entry. | Merge it and restart the shared sequence, including if the entry was completed. |
| An answer contains a typo or missing Czech diacritic. | Reset the entry to step 1 for tomorrow. |
| Completion of a step is delayed by two days. | Shift the remaining steps by two days. |
| Thirty entries are due. | Send one daily invitation and plan ten exercises by default, with optional continuation. |
| A session is interrupted. | Preserve completed answers and pending work. |
| A multi-part exercise is interrupted. | Preserve successful parts without advancing the step. Clear that attempt's partial completion if it resets. |
| A grouped entry has a multi-part active step. | Count the entire step as one exercise toward session size. |
| AI validation questions a manual addition or edit. | Explain and suggest a fix; allow explicit retention of the original and use the confirmed content in practice. |
| An entry is edited or deleted. | Update pending practice according to the editing and deletion rules. |
| Processing fails. | Preserve progress; never count it as a learner mistake. |
| A translation request arrives during practice. | Require finishing or stopping the session first; do not grade the request as an answer. |
| Step 5 is completed correctly. | Stop automatic practice for the entry until a manual restart. |

## Final scope review

The user approved this scope on 2026-10-18. It is the agreed product baseline for subsequent technical design. Future changes require the user's explicit authorization under the change-control rule at the top of this document.

Technical architecture, programming languages, and frameworks are outside this document.
