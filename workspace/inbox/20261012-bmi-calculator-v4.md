# Task note / 任務紙條 — BMI calculator v4: more detail, better UI, more actions

From: Leader · Wailan → **Leader (self-assigned, auto mode — captain ordered "do it yourself")**
Date: 2026-10-12
Mode: auto (assignment note kept for history/replay)

## What to do / 做什麼

Upgrade v3 (`workspace/outbox/20261011-bmi-calculator-v3.html`) into **v4** —
bilingual zh-TW ⇄ English, all v3 behaviour preserved, plus three kinds of improvement:

**A. More details**
1. **WHO category reference table** always on the page
   (過輕／正常／過重／肥胖 with BMI ranges); the user's current category row is
   highlighted after a calculation, highlight removed on 清除.
2. **Weight-to-normal line** under the result:
   underweight → how many kg to **gain**; overweight/obese → how many kg to **lose**;
   normal → "already within range".
3. **Session history** (last 10, newest first): time · height · weight · BMI · category.
   In memory only — **no `localStorage`, no network** (keeps the "nothing stored" rule).

**B. More actions**
4. **複製結果 / Copy result** — copies a one-line summary in the current language;
   shows `已複製` / `Copied` for 2 s; graceful failure message if the clipboard is blocked.
   Disabled until a result exists.
5. **清除紀錄 / Clear history** — empties the history; disabled when empty.
6. **Click a history row** → refills the inputs and recalculates (reuse a past entry).

**C. Better UI**
7. Colour-coded category badge on the result (underweight = blue, normal = sea-green,
   overweight = amber, obese = coral), inside the existing palette.
8. Fieldset-card layout for input / table / history; mobile-readable; height field
   focused on load.
9. `html.js` progressive-enhancement: a small "needs JavaScript" warning is shown
   only if the script never runs.

## What format / 什麼格式

- One self-contained `.html`, no CDN, offline; save as **new file**:
  `workspace/outbox/20261012-bmi-calculator-v4.html` (v3 stays byte-for-byte unchanged)
- Line 1 = `<!-- handoff: ... -->` handoff comment.
- Same palette / `"Microsoft JhengHei"` stack as v3 and `campus-picker.html`.

## New bilingual strings / 新增雙語字串

| UI element | zh-TW (default) | English |
|---|---|---|
| Table legend | `體位對照表（WHO）` | `BMI categories (WHO)` |
| Table headers | `BMI 範圍` / `體位` | `BMI range` / `Category` |
| Row ranges | `18.5 以下` / `18.5 – 24.9` / `25.0 – 29.9` / `30.0 以上` | `Below 18.5` / `18.5 – 24.9` / `25.0 – 29.9` / `30.0 and above` |
| Δ gain | `需增加約 {x} 公斤，才能到達正常體重範圍。` | `Gain about {x} kg to reach the normal weight range.` |
| Δ lose | `需減少約 {x} 公斤，才能到達正常體重範圍。` | `Lose about {x} kg to reach the normal weight range.` |
| Δ in-range | `已在正常體重範圍內。` | `You are within the normal weight range.` |
| History legend | `本次紀錄（僅保留在瀏覽器記憶體）` | `This session (kept in memory only)` |
| History empty | `尚無紀錄。` | `No entries yet.` |
| History row | `{HH:MM}｜{h} cm｜{w} kg｜BMI {bmi}｜{體位}` | `{HH:MM} · {h} cm · {w} kg · BMI {bmi} · {Category}` |
| Clear history | `清除紀錄` | `Clear history` |
| Copy button | `複製結果` | `Copy result` |
| Copied | `已複製` | `Copied` |
| Copy failed | `複製失敗，請手動選取文字。` | `Copy failed — please select the text manually.` |
| Reuse row (tooltip) | `套用這組數值` | `Reuse these values` |
| No-JS warning | `此頁面需要啟用 JavaScript 才能計算。` | `This page needs JavaScript enabled to calculate.` |

All v3 strings (labels, buttons, result, errors, disclaimer, hints, legend) carry over unchanged.

## What "done" looks like / 怎樣算做完

1. **All 7 v3 done-criteria still pass** (bilingual toggle, `<html lang>`+title switch,
   state re-render, 4 test cases, validation, offline, handoff line).
2. Table shows correct WHO ranges; after 170/65 the 正常 row is highlighted;
   清除 removes the highlight.
3. Weight-to-normal maths: `160/40` → 需增加約 **7.4** 公斤;
   `165/100` → 需減少約 **32.2** 公斤; `170/65` → 已在正常體重範圍內.
4. Each calculation appends a history row (newest first, max 10);
   Clear history empties it; clicking a row refills inputs and recalculates.
5. Copy puts `BMI 計算機｜170 cm・65 kg・BMI 22.5・正常` on the clipboard in zh-TW
   (English variant when in English); feedback text shown, no crash on `file://`.
6. Toggling language switches **every** new string (table, Δ line, history categories,
   buttons, feedback) and keeps results/history/values.
7. No `localStorage`, no network, nothing stored; v3 file unchanged (git-verified).
8. File at `workspace/outbox/20261012-bmi-calculator-v4.html`, handoff comment on line 1,
   opens by double-click with no console errors.
