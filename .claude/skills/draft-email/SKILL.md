---
name: draft-email
description: Rewrite a rough email draft in the style of the emails in emails/, then save the final version back to that folder. Use when the user wants to draft or rewrite an email to the client.
argument-hint: <rough draft>
---

# Draft email

Rough draft from the user:

$ARGUMENTS

If there is no draft above, ask the user to paste one and wait.

## Steps

1. Read every file in `emails/` and read `style-notes.md`.

2. Rewrite the rough draft so it reads like the emails in `emails/`.
   - Match their greeting, sign-off, length, sentence style and layout.
   - Follow every rule in `style-notes.md`.
   - Keep the facts exactly as the user gave them. Do not add dates, numbers or promises.
   - Plain text only. First line is `Subject: ...`, then a blank line, then the body.

3. Write the rewrite to `draft.txt` and show it to the user. Show only the email.

4. Ask: `Accept or decline?`

5. If they accept:
   - Ask: `Copy to clipboard? (y/n)`
   - If yes, run `pbcopy < draft.txt`.

6. If they decline:
   - Run `pbcopy < draft.txt` and tell them it is on their clipboard.
   - Ask them to edit it and paste their version back.
   - Wait for the paste, then compare it with `draft.txt`.
   - If they changed the style (wording, tone, greeting, sign-off, length, layout), add one or two short rules to the end of `style-notes.md` describing what they prefer. Skip any rule that is already there.
   - If they only changed facts, such as a date, name or price, add nothing.
   - Overwrite `draft.txt` with exactly what they pasted.

7. Save the final email. Find the highest number in `emails/`, add one, and move `draft.txt` to `emails/NNN.txt` (three digits, e.g. `004.txt`).

8. Tell the user the file name it was saved as, and any rules added to `style-notes.md`. Nothing else.
