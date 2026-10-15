---
name: lana
description: Turn any topic into a 10-question multiple-choice Kahoot quiz (four answers each, one correct). First propose the quiz in chat and wait for approval, then create ONE draft kahoot in the user's Kahoot account. Never host, share or publish it. Use when the user says "lana", asks for a Kahoot / quiz about a topic, or wants to repeat the quiz-to-Kahoot flow.
---

# lana: topic to draft Kahoot

Talk in plain language, and reply in the language the user wrote in.

## Step 1: Propose the quiz (no tools)

From the topic the user gives, write a quiz in chat:

- A short title.
- Exactly **10 questions**, each with exactly **4 answers (A–D)** and **exactly one correct**. Mark it with ✅.
- Make the wrong answers believable. Mix easy and harder questions and keep a logical order.
- Kahoot limits: each question is at most 120 characters and each answer at most 75. Keep within them.
- If the topic is about people or relationships (for example "how to make someone love me"), frame it around healthy behavior: respect, listening, trust, honesty. Never use manipulation or control as a correct answer. Add one kind sentence about this framing if it fits.

End by asking the user to approve or ask for changes. **Stop and wait.** Don't create anything until the user clearly approves ("yes", "approved" or the same in their language). If they ask for changes, revise and ask again.

## Step 2: Create one draft Kahoot (after approval only)

1. Load the Kahoot tools in one ToolSearch call: `create_or_update_kahoot` and `get_kahoot_editor_url` (from the Kahoot connector).
2. Call `create_or_update_kahoot` **once**, without a `uuid` so it makes a new kahoot:
   - `title` and a short `description`
   - `language` matching the quiz language (for example `English`)
   - `cover_image_query`: a short English photo search
   - `questions`: 10 items of `type: "quiz"`, each with 4 `choices` and exactly one `correct: true`, plus a distinct, specific English `image_query` per question (never repeat a query)
3. Call `get_kahoot_editor_url` with the returned `uuid`.

## Hard rules

- Create **exactly one** kahoot per approved quiz. Don't make duplicates or test copies.
- **Never host, share, publish, assign or send** the kahoot, and don't change its visibility. It stays a private draft.
- Don't call `preview_kahoot` right after creating it, because the create tool already shows a preview.

## Step 3: Report

Tell the user, in plain language:
- The draft was created and was not hosted, shared or published.
- Kahoot shuffles the answer order, but the correct answers stay the same.
- Each question has an automatic photo from Unsplash and a 20-second timer by default.
- The editor link, so they can review or change it and host it themselves when ready.
