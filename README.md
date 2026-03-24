# John's Lexicon — Daily Vocabulary

A clean, mobile-friendly vocabulary archive with etymology, example sentences, and quizzes.

**Live URL:** `https://johnslexicon.github.io/daily/`
**Word Entry Tool:** `https://johnslexicon.github.io/daily/add.html`

---

## Setup (one-time, ~10 minutes)

### 1. Create your GitHub account
- Go to https://github.com and sign up
- **Username:** `johnslexicon`

### 2. Create a new repository
- Click **+** (top right) → **New repository**
- Repository name: `daily`
- Set to **Public**
- Check **"Add a README file"**
- Click **Create repository**

### 3. Upload the site files
- Click **Add file** → **Upload files**
- Drag in: `index.html`, `words.json`, `add.html`
- Click **Commit changes**

### 4. Enable GitHub Pages
- Go to **Settings** → **Pages** (left sidebar)
- Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- Click **Save**

Your site is live at `https://johnslexicon.github.io/daily/` within ~60 seconds.

---

## Daily Workflow

### Option A: Use the Word Entry Tool (recommended)
1. Open `https://johnslexicon.github.io/daily/add.html` on your phone
2. Fill in the word, part of speech, definitions, etymology, and sentence
3. For the quiz: copy the auto-generated prompt → paste into Claude → paste Claude's output back into the quiz fields
4. Tap "Generate JSON Entry" → copy the output
5. Go to `github.com/johnslexicon/daily` → open `words.json` → pencil icon → paste the block at the top (after `[`) → commit

### Option B: Edit words.json directly
1. Go to `github.com/johnslexicon/daily` → open `words.json` → pencil icon
2. Add a new entry at the top (see template below)
3. Commit

### Entry template:
```json
  {
    "date": "2026-03-25",
    "word": "new-word",
    "partOfSpeech": "noun",
    "definitions": [
      "First definition",
      "Second definition if applicable"
    ],
    "etymology": "From Latin *foreignterm* 'meaning', from *root* 'meaning'",
    "sentence": "Your example sentence here.",
    "quiz": {
      "correct": 0,
      "options": [
        "Sentence A — correct usage",
        "Sentence B — plausible but wrong",
        "Sentence C — plausible but wrong",
        "Sentence D — plausible but wrong"
      ]
    }
  },
```

---

## Formatting Rules

- **Definitions:** No trailing periods (they're fragments, not sentences)
- **Etymology:** No trailing period. Wrap Latin/Greek/foreign terms in `*asterisks*` for italics on the site. Format consistently like Merriam-Webster: language name in plain text, foreign terms in *italics*, English glosses in single quotes
- **Sentence:** Ends with appropriate punctuation. The vocabulary word is auto-bolded on the site
- **Quiz:** `"correct"` is the zero-indexed position of the correct answer in the `"options"` array (0 = first option). Quiz is optional — entries without it simply won't show the quiz button

---

## Auto-Publish (Preloading Future Words)

The site hides any word with a future date. Batch-load a week's worth with future dates, and each word appears automatically on its assigned day (midnight, visitor's local time).

---

## Files

- **index.html** — the site (all-serif typography, quiz UI, auto-publish)
- **words.json** — all word data (the only file you edit day-to-day)
- **add.html** — word entry tool with quiz prompt generator
