# Task note / 任務紙條 — BMI calculator app (zh-TW)

From: Leader · Wailan → Member · Taroko
Date: 2026-10-11
Mode: manual relay

## What to do / 做什麼

Build a **BMI calculator** as a single-file web app. The whole interface must be in
**Traditional Chinese, Taiwan usage (zh-TW)** — no English UI strings.

- User enters **height in centimetres** and **weight in kilograms**, presses a button,
  the app shows the BMI value and the body-size category.
- Formula: `BMI = 體重(kg) ÷ 身高(m)²`, shown to **1 decimal place**.
- Categories (WHO cut-offs), label in zh-TW:

  | BMI | 體位 |
  |---|---|
  | below 18.5 | 過輕 |
  | 18.5 – 24.9 | 正常 |
  | 25.0 – 29.9 | 過重 |
  | 30.0 and above | 肥胖 |

- Invalid input (empty, zero, negative, non-numeric, height > 300 cm or < 50 cm,
  weight > 300 kg or < 10 kg) → show a zh-TW error message and **do not** show a BMI.
- A small disclaimer line under the result: 本工具僅供參考，不能取代專業醫療建議。
- Optional bonus (only if the core is already correct): show the healthy weight range
  for the entered height, and a 清除 reset button.

## What format / 什麼格式

- **One self-contained `.html` file**: HTML + CSS + JS inline. No frameworks, no CDN,
  no images from the internet — must work offline, opened by double-clicking.
- Save it as a **new file**: `workspace/outbox/20261011-bmi-calculator.html`
  (never overwrite anything in `shared/`).
- First line of the file = one handoff line as an HTML comment:
  `<!-- handoff: what I did / what to watch / ready to use or not -->`
- `<html lang="zh-TW">`, `<meta charset="utf-8">`.
- Style: follow the look of `workspace/shared/campus-picker.html` (its colour palette,
  and a font stack that includes `"Microsoft JhengHei"`). Must be readable on mobile.
- Exact wording to use (zh-TW):
  - Title: `BMI 計算機`
  - Labels: `身高（公分）` / `體重（公斤）`
  - Button: `計算`
  - Result: `您的 BMI 為 {數值}` and `體位：{過輕／正常／過重／肥胖}`
  - Errors: `請輸入身高與體重。` / `請輸入正確的數字（50–300 公分的身高、10–300 公斤的體重）。`
  - Disclaimer: `本工具僅供參考，不能取代專業醫療建議。`

## What "done" looks like / 怎樣算做完

Open the file in a browser and all of these pass:

1. `170 cm / 65 kg` → `22.5` → 正常
2. `160 cm / 40 kg` → `15.6` → 過輕
3. `180 cm / 90 kg` → `27.8` → 過重
4. `165 cm / 100 kg` → `36.7` → 肥胖
5. Empty or non-numeric input → zh-TW error message, no BMI result shown.
6. Every visible string on the page is Traditional Chinese (Taiwan usage).
7. Nothing is sent to the network and nothing is stored — no personal data anywhere.
8. The file lives in `workspace/outbox/20261011-bmi-calculator.html` with the
   handoff comment on line 1.
