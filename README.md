# Study Mode Hub — Calm, Focused, Snack-worthy Breaks

A single-file web app that makes studying feel human. Clean landing page up front, then a playful app with **Book**, **Film**, **Article**, and **Essay** modes; a friendly **5-minute snack-break timer**; **Dark Mode**; **autosave**; and **ISBN cover lookup**.

> **License:** This project is distributed under a **Use-Only Software License (Access-Only)**.  
> You may **use** it from the licensor’s original source, but **copying, redistribution, self-hosting, modification, or reverse engineering are prohibited**. See [License](#-license).

---

## ✨ What’s inside

- **Landing page best practices**
  - Clear headline + primary CTAs above the fold
  - Benefit-led sections
  - Lightweight social proof
  - Focused, responsive layout
- **Study modes**
  - **Book**: Title, Author, ISBN, Chapter count → tap a chapter chip to complete → **5-minute break**
  - **Film**: Title, Director, Runtime → record a session → break
  - **Article**: Title, Author, Page count → break
  - **Essay**: Title, Topic, Target word count → break
- **Cover by ISBN**
  - Tries **Open Library Covers API** first (no key)
  - Falls back to **Google Books** public endpoint (no key) if needed
  - Live preview while typing; persisted with your book data
- **Calm UI & UX**
  - Dark/Light toggle (remembers your choice)
  - Autosave via `localStorage`
  - Friendly **toast** notifications (no pop-up `alert()`s)
  - Accessible labels, roles, and focus management
  - Single file: **`index.html`** (HTML + CSS + JS)

---

## 🚀 Quick start

1. Save the file as **`index.html`** (the provided single-file page).
2. Double-click to open in any modern browser.

> **Note:** The app can fetch covers from the public web (Open Library / Google Books). If you need fully offline behavior, see [Offline / No-Network](#-offline--no-network).

---

## 🧭 How to use

### 1) Pick a mode
Use the buttons: **Book**, **Film**, **Article**, or **Essay**.

### 2) Enter details
- **Book**: Title, Author, **ISBN (10 or 13)**, Chapters  
  → As you type an ISBN, the app tries to fetch a cover image.
- **Film**: Title, Director, Runtime (minutes)
- **Article**: Title, Author, Number of pages
- **Essay**: Title, Topic, Target word count

### 3) Track progress + take breaks
- In **Book** mode, tap a **chapter chip** to mark it complete.  
  Each completion starts a **5:00** break with a circular countdown.
- Film/Article/Essay start the break when you record a session.

### 4) Dark mode & autosave
- Click **🌙 / ☀️** to toggle.  
- The app saves:
  - Theme preference
  - Book details + completed chapters + cover URL
  - Last entered fields in Film/Article/Essay

---

## 🔒 Privacy

- Data is stored **only in your browser** via **`localStorage`**:
  - Keys:  
    - `smh_theme`  
    - `smh_book` (title, author, isbn, chapters, `done` array, `coverUrl`)  
    - `smh_last_inputs` (recent Film/Article/Essay inputs)
- No analytics, cookies, or external tracking.
- **Clearing data:**  
  - Browser DevTools → Application/Storage → `localStorage` → remove keys above  
  - Or clear site data for the page.

---

## 🧩 Customization (owner only)

Open `index.html` and adjust:

- **Break length:**  
  In the script, set `const totalSeconds = 5 * 60;`
- **Colors & radii:**  
  Edit the CSS variables in `:root` (e.g., `--brand`, `--brand-2`, `--radius-lg`)
- **Text copy:**  
  Update hero, benefits, and testimonial strings inline
- **Landing page sections:**  
  Add/remove cards in “Why it works” or quotes

> Reminder: Under the **Use-Only** license, others may not copy or publish modified versions without your permission.

---

## 🌐 Cover lookup (APIs & behavior)

- **Primary:** Open Library Covers API  
  Pattern: `https://covers.openlibrary.org/b/isbn/<ISBN>-L.jpg`  
  (No API key; simple image URL)
- **Fallback:** Google Books public endpoint  
  Query: `https://www.googleapis.com/books/v1/volumes?q=isbn:<ISBN>`

**How it works in the app**
1. When a valid ISBN (10 or 13 characters, digits or trailing X) is detected, we try **Open Library**.
2. If the Open Library image doesn’t exist, we query **Google Books** and use the thumbnail (if present).
3. The chosen `coverUrl` is saved alongside the book in `localStorage` and displayed:
   - **Preview** on the Book form
   - **Small cover** on the chapter progress card

**Notes**
- Both endpoints are public and typically support browser use without CORS issues.
- Images and metadata availability vary by ISBN; not all books will have a cover.
- If your environment blocks external requests, see the offline section below.

---

## 📦 File structure

```
index.html     # All-in-one page (HTML, CSS, JS)
README.md      # You are here
LICENSE        # Use-Only Software License (Access-Only)
```

---

## 🧪 Troubleshooting

- **No cover shows up**
  - Check that the ISBN is 10 or 13 characters (`0–9` or `X` for ISBN-10 check digit).
  - Some ISBNs simply don’t have covers in Open Library/Google Books.
- **Cover shows in the form but not in progress**
  - The app persists `coverUrl` after a successful lookup. Try clicking **Start Book Session** again if you changed ISBN.
- **Data didn’t persist**
  - Ensure your browser allows `localStorage` for file URLs or serve the file locally (e.g., `python3 -m http.server 8080`).
- **Dark mode toggle label seems wrong on first load**
  - The script syncs the label on init; a hard refresh usually resolves mismatched UI caches.

---

## 📴 Offline / No-Network

To run without any external requests (no cover lookups):

1. Keep using the app normally; only the cover fetch calls go out.
2. If you want to **disable network lookups**:
   - Remove or comment out these functions and their calls:
     - `resolveCoverURL`, `openLibraryCoverURL`, `fetchGoogleBooksCover`, `imageExists`, `updateCoverPreview`
   - Or guard them with a flag:
     ```js
     const COVER_LOOKUP_ENABLED = false;
     if (COVER_LOOKUP_ENABLED) {
       // call updateCoverPreview(...) and resolveCoverURL(...)
     }
     ```
3. You can also host your own cover images and assign `coverUrl` manually in code.

---

## 🔐 License

**Use-Only Software License (Access-Only)**  
Copyright (c) 2025 <Your Name>. All rights reserved.

You are granted a limited right to **access and use** the software solely from the licensor’s original source. **Copying, redistribution, self-hosting, modification, or reverse engineering are prohibited.** See `LICENSE` for full terms.

**Required header** at the top of `index.html`:

```html
<!--
SPDX-License-Identifier: LicenseRef-UseOnly
Copyright (c) 2025 <Your Name>. All rights reserved.
Licensed for access-only use from the Licensor’s source. Copying, redistribution,
self-hosting, modification, or reverse engineering are prohibited. See LICENSE.
-->
```

---

## 🚀 Deploy (owner only)

- **Static hosting**: Any static host works (GitHub Pages, Netlify, Vercel, S3, etc.).
- **Access control**: Consider private or access-controlled hosting if you want to deter copying.
- Keep proprietary notices intact (header + footer).
- If someone reposts your code, you can file a **DMCA takedown** referencing your copyright and license.

---

## 🙏 Acknowledgments

- **Open Library Covers API** — public cover images where available  
- **Google Books** — fallback thumbnails when Open Library has none

---

## 🗒️ Changelog

### 2025-11-02
- Added **ISBN cover lookup** with Open Library → Google Books fallback
- Replaced `alert()` messages with **toast notifications**
- Refined landing page (benefits, social proof, CTAs)
- Improved accessibility (labels, roles, focus, aria-live)
- Preserved **Dark Mode** + **autosave** + **snack timer**
