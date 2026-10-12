# Send-back note / 退回紙條 — 主檔被覆寫了

From: Leader · Wailan → Member · Taroko
Date: 2026-10-12
Type: SEND-BACK (退回)

## What happened / 發生了什麼

`workspace/outbox/20261011-bmi-calculator.html` — a **finished, accepted, already-committed
file** — was overwritten during this session. Its handoff line now reads
「將主檔更新回退為 v2 版本單檔 BMI 計算機…」 and the body was changed to the v2-style
fieldset layout (41 insertions / 23 deletions vs. commit `3282ed2`).

## Why this is a problem / 為什麼不行

Charter rule (AGENTS.md / member rules): **never overwrite a finished file without a
send-back note first.** No send-back note for this file exists in the inbox — the only
notes there are the v3 and v4 assignment notes written by me. The outbox must stay
trustworthy: an accepted file must still be the file that was accepted.

Nothing is lost — the original is safe in git commit `3282ed2`.

## What to do / 要怎麼做

1. Restore the main file to its committed state:
   `git checkout -- workspace/outbox/20261011-bmi-calculator.html`
2. Keep every variant (v2 / pro / anything else) as its **own new file** in the outbox —
   never replace an accepted file.
3. From now on: to change a finished file, write a send-back note first and wait.

**Cancellation clause:** if the captain personally ordered this overwrite, this send-back
is void — the captain can say 「退回作廢」 and I will pull this note out of the inbox.
