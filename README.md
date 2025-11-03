# Study Mode Hub — Calm & Fun

A single-file HTML app that makes studying feel human: gentle visuals, snack-worthy breaks, and flexible modes for **Book**, **Film**, **Article**, and **Essay**. Includes a smooth **Dark Mode** and **auto-save** (localStorage) so your session survives a reload.

> **License:** This project is distributed under a **Use-Only Software License (Access-Only)**.  
> You may **use** it from the licensor’s original source, but **copying, redistribution, self-hosting, modification, or reverse engineering are prohibited**. See [License](LICENSE.md).

---

## ✨ Features

- **Modes:** Book (chapters with tap-to-complete), Film, Article, Essay  
- **Snack Break Timer:** Friendly circular countdown (default 5 minutes)  
- **Dark Mode:** One-click toggle, remembers your choice  
- **Auto-Save:** Persists book info, completed chapters, and last inputs for other modes via `localStorage`  
- **Responsive & Calm UI:** Pastel gradients, roomy spacing, better proportions on phone/desktop

---

## 📦 Quick Start

1. Save the file as `studymodes.html`.
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari).  
   No build tools or server required.

Optional:
- Double-click to open, or drag into a browser window.
- If you do run a local server, any static server works (e.g., `python3 -m http.server 8080`) — **but redistribution/self-hosting by others is not permitted** (see license).

---

## 🧭 Using the App

### Modes
- **Book:** Enter Title, Author, ISBN, Chapter count → tap chapter chips to mark done.  
  Each completion triggers a **5-minute break**.
- **Film:** Enter Title/Director/Runtime → when you finish, start your break.
- **Article:** Enter Title/Author/Page count → break when done.
- **Essay:** Enter Title/Topic/Target word count → take a break after milestones.

### Breaks
- Big, friendly circular timer with time remaining (default 5:00).
- Click **“I’m ready now”** to end early.

### Theme & Persistence
- Toggle **Dark/Light** in the header.  
- Book details + completed chapters are saved.  
- Last entered fields for film/article/essay are saved too.

---

## 🔒 Privacy

- The app stores minimal data **only in your browser** via `localStorage`:
  - Book: title, author, ISBN, chapter count, which chapters are completed
  - Last inputs for Film/Article/Essay
  - Theme preference
- No analytics, no external requests, no cookies.

To clear data: open DevTools → Application/Storage → `localStorage` → remove keys starting with `smh_`, or clear site data.

---

## 🛠 Customization

Open `studymodes.html` and adjust:

- **Break length:** Change `totalSeconds = 5 * 60;` in the `<script>`.
- **Colors & Radii:** Tweak CSS variables at the top (`--brand`, `--brand-2`, `--radius-lg`, etc.).
- **Copy text / prompts:** Search for `alert(` or text in headers/subheaders.

> If you plan to publish a customized version, you must obtain **written permission** from the copyright holder (see license).

---

## 📁 File Structure

