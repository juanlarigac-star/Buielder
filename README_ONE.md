# 🧠 FlashLearn

A lightweight, local-first **flashcard study app** inspired by Anki — built for exam preparation with active recall and difficulty-based prioritization.

No build step, no backend, no account. Just open `index.html` in your browser.

![Tech](https://img.shields.io/badge/React-18-61dafb?logo=react&logoColor=white)
![Tech](https://img.shields.io/badge/TailwindCSS-3-38bdf8?logo=tailwindcss&logoColor=white)
![Tech](https://img.shields.io/badge/Storage-localStorage-orange)
![License](https://img.shields.io/badge/license-MIT-green)

---

## ✨ Features

- 📚 **Decks & cards** — organize your study material by subject, topic, or exam
- 🃏 **Study mode** — flip-card animation, reveal answer, rate as Easy / Medium / Hard
- 🎯 **Smart prioritization** — Hard cards appear first, then new, medium, and easy
- 📊 **Progress tracking** — per-deck stats, difficulty breakdown, and topic-level analytics
- 🔍 **Search & filters** — find cards by keyword, topic, or difficulty
- 📥 **JSON import** — bulk-load decks from a JSON file (great for sharing study sets)
- 💾 **Local-first** — everything is saved in your browser's `localStorage`; nothing leaves your machine
- 🎨 **Clean UI** — responsive, accessible, and keyboard-friendly

---

## 🚀 Getting Started

### Option 1 — Just open the file
1. Download or clone this repo
2. Double-click `index.html`
3. Done. Your browser opens the app.

> ⚠ All data lives in `localStorage` tied to the file's origin. If you always open the app the same way, your decks persist forever.

### Option 2 — Serve it locally (optional)
If you'd rather use `http://localhost`:
```bash
# Python
python -m http.server 5173
# or Node
npx serve .
```
Then visit `http://localhost:5173`.

---

## 📥 Importing Decks from JSON

Click **Import** on the home screen and either upload a `.json` file or paste JSON directly.

A ready-to-use example is included: **[`sample-decks.json`](sample-decks.json)** — 7 decks with 50+ flashcards on **Software Metrics** (measurement fundamentals, GQM, empirical studies, size metrics, function points, quality metrics, agile estimation).

### JSON format
```json
[
  {
    "deckName": "My Deck",
    "deckDescription": "Optional description",
    "cards": [
      {
        "question": "What is...?",
        "answer": "It is...",
        "topic": "Optional topic"
      }
    ]
  }
]
```

| Field | Required | Notes |
|---|---|---|
| `deckName` | ✅ | Title of the deck |
| `deckDescription` | ❌ | Short description |
| `cards` | ✅ | Array of card objects |
| `cards[].question` | ✅ | Front of the card |
| `cards[].answer` | ✅ | Back of the card |
| `cards[].topic` | ❌ | Tag/category for filtering |

The app validates the JSON live and shows a preview before importing.

---

## 🎮 How to Use

1. **Create a deck** (or import one) — name it after your exam/subject.
2. **Add flashcards** — question, answer, and optionally a topic.
3. **Hit "Study Now"** — the card flips when you tap *Reveal Answer*.
4. **Rate yourself**: Easy / Medium / Hard. Hard cards float to the top of future sessions.
5. **Check Progress** — see how much you've reviewed, what's still weak, and your breakdown by topic.

---

## 🧮 Study Algorithm

A simple priority-based queue (no spaced repetition yet — see roadmap):

| Difficulty | Priority |
|---|---|
| 🔴 Hard | 4 |
| 🔵 New (unreviewed) | 3 |
| 🟡 Medium | 2 |
| 🟢 Easy | 1 |

At session start, cards are sorted by priority (with random tie-breaking) so the cards you struggle with reappear first.

---

## 🏗️ Tech Stack

| Layer | Tech |
|---|---|
| UI | **React 18** (loaded via CDN, no build) |
| Styling | **Tailwind CSS** (Play CDN) |
| JSX | **Babel Standalone** (runtime transpilation) |
| Storage | **`localStorage`** |
| Runtime | Any modern browser |

Everything is in a single `index.html` file — easy to read, hack, and deploy.

---

## 📂 Project Structure

```
flashcard-app/
├── index.html          ← The entire app (React + Tailwind + Babel)
├── sample-decks.json   ← Example deck pack you can import
└── README.md
```

---

## 🛣️ Roadmap

Ideas for future versions:
- [ ] Export decks to JSON
- [ ] Spaced repetition with review dates (SM-2 algorithm)
- [ ] Dark mode
- [ ] Image/code/formula support in cards
- [ ] CSV import
- [ ] Daily study streak / reminders
- [ ] AI-generated cards from notes
- [ ] PWA / desktop (Tauri) build

---

## 📄 License

MIT — do whatever you want with it. If it helps you ace your exam, that's enough thanks.

---

> Built as a personal study tool for exam prep. Local-first, dependency-free, and unapologetically simple.
