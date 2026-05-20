# Marshall Nguyễn — Portfolio

> Personal portfolio site for **Marshall Nguyễn Hoàng Huy** —
> editorial-style hand-crafted design, custom typography, dark mode,
> CV download, and a Gemini-powered Q&A widget about my work and
> background.

**🌐 Live:** https://marshall-porfolio.web.app

**📄 CV (PDF):** https://marshall-porfolio.web.app/Marshall_Nguyen_CV_2026.pdf

---

## What you're looking at

Most of the public-facing source is published in this repo so you can
read how it's built.

**🔒 One file is withheld** — [`chat-widget.js`](./chat-widget.js). The
file in this repo is a header-only stub describing what the full
implementation does (i18n in 4 languages, streaming Gemini proxy,
themable, dual-mode portfolio / BDS). The real widget is in the private
source repo. Without it, the chat bubble in `index.html` won't open;
everything else renders.

If you're evaluating this for a hiring decision and want to read the
omitted file, contact: **nhhuy130@gmail.com**.

---

> **⚠️ License**: All Rights Reserved — see [`LICENSE`](./LICENSE). No
> copy, redistribution, embedding, or derivative work. Quoting short
> snippets in reviews with attribution is fine.

---

## Files

| File                     | Purpose                                              |
| ------------------------ | ---------------------------------------------------- |
| `index.html`             | Main portfolio page — hero, career, skills, contact  |
| `cv.html`                | Standalone CV view (`/cv.html`)                      |
| `marshall.jpg`           | Photo used in the hero                               |
| `chat-widget.js`         | 🔒 withheld — see stub for description                |
| `firebase.json`          | Firebase Hosting config (rewrites, headers, caching) |
| `LICENSE` / `NOTICE`     | All Rights Reserved + attributions                   |

---

## Stack

- **HTML / CSS / vanilla JS** — handcrafted, no framework, no build step
- **Firebase Hosting** — auto-deploys from the private source repo on
  every push to `main`
- **Cloud Functions** (private repo) — proxy for the Gemini-backed Q&A
  endpoint
- **Editorial typography** — pairing tuned by hand to read as
  hand-crafted, not as an AI-template

---

## What's on the live site

- **Editorial hero** with large-format type, photo, and intro
- **Career timeline** — Ming Chuan University grad, Foreign Trade
  University grad, 4 languages (Vietnamese · English · Chinese · Russian)
- **Skills + tools** — programmatic chart of competencies
- **Selected work** — case studies linking to other deployed projects
- **Gemini-powered "Ask about Marshall"** — proxy-backed widget; the
  prompt + glue is the withheld file
- **Contact + lead form** — email, Zalo, Instagram, form intake
- **CV download** — kept up to date alongside the live site

---

## Why some code is withheld

The portfolio is part personal CV, part product showcase. The chat
widget is the most reusable piece — withholding it stops trivial copy.
The rest of the layout, typography, and content is published so the
craftsmanship is reviewable.

---

Built and maintained by **Marshall Nguyễn Hoàng Huy**
([@mrdeathisreal](https://github.com/mrdeathisreal)).
