# Task note / 任務紙條 — BMI calculator v3: bilingual zh-TW + English

From: Leader · Wailan → Member · Taroko
Date: 2026-10-11
Mode: manual relay

## What to do / 做什麼

Upgrade the BMI calculator to a **bilingual version (v3)**: Traditional Chinese
(Taiwan) **and** English, switched by a language-toggle button.

- Base your work on the finished v2: `workspace/outbox/20261011-bmi-calculator.html`
  (read it and reuse its logic — but **do not modify that file**).
- **New file** (v2 stays untouched): build the whole thing fresh as v3.
- Follow the language-toggle pattern already used in `workspace/shared/campus-picker.html`:
  a single button that swaps every visible string between the two languages.
- **Default language on load = zh-TW** (same strings as v2). The toggle button reads
  `English` in zh-TW mode; after switching to English it reads `中文`.
- The toggle button must be always visible (put it in the header, like campus-picker).
- Switching language must also update: `<html lang>` (`zh-TW` ⇄ `en`) and the
  document `<title>`.
- If a result or an error is on screen when the user toggles, **re-render that same
  result/error in the new language** (keep the values in memory; do not clear them).

## Everything that stays the same / 不變的部分

All v2 behaviour and wording carries over unchanged, just bilingual:

- Formula `BMI = 體重(kg) ÷ 身高(m)²`, 1 decimal place; WHO cut-offs
  (<18.5 / 18.5–24.9 / 25.0–29.9 / ≥30.0).
- Validation ranges: height 50–300 cm, weight 10–300 kg; empty / non-numeric → error,
  no BMI shown.
- Healthy weight range line, 清除 / Clear button, Enter-to-submit, `aria-live`.
- One self-contained `.html`, no CDN, works offline.

## Exact strings for both languages / 雙語對照字串

| UI element | zh-TW (default) | English |
|---|---|---|
| Title | `BMI 計算機` | `BMI Calculator` |
| Toggle button | `English` | `中文` |
| Height label | `身高（公分）` | `Height (cm)` |
| Weight label | `體重（公斤）` | `Weight (kg)` |
| Calculate button | `計算` | `Calculate` |
| Clear button | `清除` | `Clear` |
| Result | `您的 BMI 為 {數值}` | `Your BMI is {value}` |
| 過輕 | `體位：過輕` | `Category: Underweight` |
| 正常 | `體位：正常` | `Category: Normal` |
| 過重 | `體位：過重` | `Category: Overweight` |
| 肥胖 | `體位：肥胖` | `Category: Obese` |
| Healthy range | `此身高的健康體重範圍：{min} ～ {max} 公斤` | `Healthy weight range for this height: {min} – {max} kg` |
| Error: empty | `請輸入身高與體重。` | `Please enter your height and weight.` |
| Error: invalid | `請輸入正確的數字（50–300 公分的身高、10–300 公斤的體重）。` | `Please enter valid numbers (height 50–300 cm, weight 10–300 kg).` |
| Disclaimer | `本工具僅供參考，不能取代專業醫療建議。` | `This tool is for reference only and is not a substitute for professional medical advice.` |
| Placeholder (height) | `例如：170` | `e.g. 170` |
| Placeholder (weight) | `例如：65` | `e.g. 65` |

## What format / 什麼格式

- One self-contained `.html` file, save as a **new file**:
  `workspace/outbox/20261011-bmi-calculator-v3.html`
- First line = one handoff line as an HTML comment:
  `<!-- handoff: what I did / what to watch / ready to use or not -->`
- Keep the v2 look (`campus-picker.html` palette, `"Microsoft JhengHei"` in the
  font stack). The English strings must not break the layout on mobile.

## What "done" looks like / 怎樣算做完

1. Page loads in zh-TW — every visible string matches the zh-TW column above.
2. Click the toggle → all visible strings switch to the English column, button now
   reads `中文`, and `<html lang="en">`.
3. The four test cases give the same numbers in **both** languages:
   170/65 → 22.5 正常／Normal; 160/40 → 15.6 過輕／Underweight;
   180/90 → 27.8 過重／Overweight; 165/100 → 36.7 肥胖／Obese.
4. Trigger an error, then toggle → the same error message reappears in the other language.
5. Calculate, then toggle → the result reappears in the other language with the same BMI value.
6. Nothing sent to the network, nothing stored; `workspace/outbox/20261011-bmi-calculator.html`
   (v2) is byte-for-byte unchanged.
7. File saved as `workspace/outbox/20261011-bmi-calculator-v3.html` with the
   handoff comment on line 1.
