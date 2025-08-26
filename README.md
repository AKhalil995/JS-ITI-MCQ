# JavaScript MCQ Exam — README

A single-file, self-contained web page that renders a large bank of JavaScript multiple-choice questions, lets students answer them, shows which are correct/incorrect on submit, and computes a final score.

---

## ✨ Features

* **100+ MCQs** covering variables, scope, hoisting, arrays, regex, DOM, events, OOP (ES5/ES6), modules, promises/async, etc.
* **Instant feedback**: after **Submit**, each question is marked ✅/❌ and an explanation (if provided) can be shown.
* **Final score**: total points shown at the end.
* **Zero dependencies**: plain HTML/CSS/JS—works offline.
* **One file deploy**: drop the file on any static host (GitHub Pages, Netlify Drop, Vercel/Cloudflare Pages).

---

## 📦 What’s in this project?

* `index.html` — the entire app (HTML + CSS + JS in one file).

---

## ▶️ Run locally

1. Download `index.html` to your computer.
2. Double-click it to open in your browser **or** right-click → **Open With…** → your browser.

   * Works in any modern browser (Chrome, Edge, Firefox, Safari).
   * Make sure JavaScript is enabled.

---

## 🧠 Using the exam page

1. **Answer questions** by selecting the radio option (one answer per MCQ).
2. Click **Submit** to:

   * Lock answers (optional—depends on the generated file’s logic),
   * Mark each question **correct/incorrect**,
   * Show **per-question feedback** (if included),
   * Display the **final score** (e.g., `78 / 100`).
3. Use **Reset** (if included) to clear selections and try again.

---

## 🛠️ Customizing questions

> The generated file is self-contained. Your copy will have one of these two patterns for questions. Open the file in a code editor and look for either **(A) HTML blocks** or **(B) a JavaScript data array**.

### (A) If your file uses **HTML blocks** for questions

You’ll see repeating markup like:

```html
<section class="mcq" data-points="1" data-id="Q1" data-answer="B">
  <h3>1. Which declaration is block-scoped?</h3>
  <label><input type="radio" name="Q1" value="A"> var</label>
  <label><input type="radio" name="Q1" value="B"> let</label>
  <label><input type="radio" name="Q1" value="C"> Function parameter</label>
  <label><input type="radio" name="Q1" value="D"> with</label>
  <div class="explain">Explanation here…</div>
</section>
```

To add a new question:

1. **Copy** one `<section class="mcq">…</section>`.
2. Update:

   * `data-id` → a unique ID (e.g., `Q101`)
   * `data-answer` → the correct option letter (`A`–`D`)
   * `data-points` → points for this MCQ (default `1`)
   * Question text and option labels
3. Save—no build step needed.

### (B) If your file uses a **JavaScript array** for questions

You’ll see something like:

```js
const QUESTIONS = [
  {
    id: "Q1",
    text: "Which declaration is block-scoped?",
    choices: ["var","let","Function parameter","with"],
    correct: "B",
    points: 1,
    explain: "Only let/const are block-scoped."
  },
  // …
];
```

To add a new question:

1. Append a new object to `QUESTIONS`.
2. Keep `id`, `text`, `choices` (A–D), `correct` (`"A"`–`"D"`), and optional `points`/`explain`.
3. Save.

> If you want to change the **scoring**, search for the final score calculation (often something like `total += q.points`) and adjust.

---

## 🎨 Styling

Inside the same HTML file you’ll find a `<style>` block. Common tweaks:

* Spacing/layout: `.mcq`, `.choices`, `.result`, `.score`
* Correct/incorrect highlights: e.g., `.is-correct`, `.is-wrong`
* Buttons: `.btn`, `.btn-primary`, `.btn-secondary`

Change CSS there to adjust colors/spacing.

---

## 🧪 Testing checklist

* [ ] Page opens in a modern browser without console errors.
* [ ] Selecting answers works for every question.
* [ ] **Submit** marks answers and shows a final score.
* [ ] Points add up to the expected total.
* [ ] Wrong answers show the correct mark/feedback (if implemented).
* [ ] Reset (if present) clears everything.
* [ ] Page works offline (no external dependencies).
* [ ] On the hosting platform, all assets load (paths are relative like `./`).

---

## ❓Troubleshooting

* **Nothing happens on Submit**

  * Ensure JavaScript is enabled.
  * Open DevTools → **Console** for errors (e.g., typos in `data-answer` or duplicate `name` attributes).
* **Score looks wrong**

  * Check each `data-points` (HTML) or `points` field (JS array).
  * Make sure each MCQ has exactly one correct letter (`A`–`D`) and that radio `name` matches the `id`.
* **Styles missing**

  * Make sure you didn’t delete the `<style>` block.
* **Hosting shows a 404**

  * For GitHub Pages, ensure the file is named `index.html` if you expect it at the repo root.
  * Paths must be **relative** (e.g., `./script.js`, not `C:\…` or `file:///…`).

---

## 📚 How this works (high level)

* The page renders MCQs either from **static HTML blocks** or by **generating them from a JS array**.
* On submit:

  * The script loops all questions,
  * Reads the selected radio value,
  * Compares with the correct answer,
  * Adds/removes CSS classes (green/red),
  * Tallies the total points and prints a summary.

No build tools, no frameworks—just DOM APIs.

---

## 🧾 License

Use freely for study/teaching. If you republish the exact question set publicly, please include attribution to your course/instructor requirements if applicable.

---

## 🤝 Contributing

* Found a typo or want to add questions?
  Edit `js_mcq_exam.html` and share your updated copy, or push a PR if you’re using a Git repo.
