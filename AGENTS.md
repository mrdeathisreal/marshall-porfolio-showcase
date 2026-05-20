# AGENTS.md

Hướng dẫn cho AI coding agent (Claude Code, Cursor, Codex) khi làm việc trên project này.

## Project

**Portfolio cá nhân của Marshall Ng Hoang Huy** — đây là tài sản nghề nghiệp quan trọng nhất, được dùng để xin việc Sales/BD/GTM. Live: https://marshall-porfolio.web.app

**Tone & content critical**: Site này KHÔNG được phép trông giống AI-generated. Recruiter dùng AI-tells làm tín hiệu loại CV. Fewer ornaments, less marketing-speak, conversational copy. Editorial-print style.

## Tech Stack

- **Frontend**: Single-file HTML + CSS + JS (không bundler, không framework)
- **Hosting**: Firebase Hosting (project `marshall-porfolio` aka `marshall-ng-portfolio`)
- **Fonts**: Newsreader serif (display) + Inter (body) + JetBrains Mono (code)
- **i18n**: dictionary `const I18N` trong `index.html`, 4 ngôn ngữ EN/VI/zh-TW/zh-CN
- **Chat widget**: `chat-widget.js` — separate file, drop-in floating chat
- **AI chat backend**: Cloudflare Worker (đã pivot từ Firebase Functions vì user không muốn add card)
- **Deploy**: Auto on push to `main` via GitHub Actions

## File Structure

```
marshall-porfolio/
├── index.html                       ← toàn bộ site (HTML + CSS + JS + i18n dictionary)
├── cv.html                          ← CV web version
├── chat-widget.js                   ← floating chat (WITHHELD trong showcase repo)
├── marshall.jpg                     ← photo (top-right hero)
├── Marshall_Nguyen_CV_2026.pdf      ← download CV button target
├── firebase.json                    ← Firebase hosting config
├── deploy.sh                        ← deploy script
├── vercel.json                      ← Vercel config (backup hosting)
├── .firebaserc                      ← Firebase project alias
└── README.md
```

## Repo Pattern — PRIVATE source + PUBLIC showcase

- **Private**: `mrdeathisreal/marshall-porfolio` (this repo — full source)
- **Public**: `mrdeathisreal/marshall-porfolio-showcase` (auto-synced, `chat-widget.js` WITHHELD)
- Sync: GitHub Actions on every push to `main` (SSH deploy keys)
- License: **All Rights Reserved** (no MIT/Apache trên showcase)

## Commands

```bash
# Xem local (khuyến nghị dùng server cho font load chuẩn)
python3 -m http.server 8000        # rồi mở http://localhost:8000

# Deploy
./deploy.sh                         # hoặc: firebase deploy --only hosting
git push origin main                # tự deploy qua GitHub Actions
```

## Conventions

### Edit content
- Toàn bộ chữ trên site nằm trong dictionary `const I18N = { ... }` ở cuối `index.html`
- Đổi nội dung: tìm key (vd `hero.title_html`), sửa trong **CẢ 4 ngôn ngữ**
- Key có hậu tố `_html` → render HTML (cho phép `<strong>`, `<em>`, `<span>`)
- Key không có hậu tố → render plain text (auto escape)

### Edit numbers
- Stats trong "Proof of Impact" (vd 1150+, 5+) là hardcode trong `<!-- IMPACT -->` block
- Tìm class `stat-num` để sửa số
- Label dưới mỗi số đổi qua I18N (vd `stat.clients.label`)

### Photo & CV
- Đổi ảnh: đè file `marshall.jpg` (giữ tên)
- Đổi CV PDF: đè file `Marshall_Nguyen_CV_2026.pdf` (giữ tên)

### Typography rules (no AI tells)
- KHÔNG dùng em-dash bừa (`—`) trong câu tiếng Việt
- KHÔNG dùng cụm "leveraging", "synergize", "ecosystem", "in the realm of"
- Câu ngắn, dứt khoát. Số liệu cụ thể > tính từ
- "Driven", "passionate", "results-oriented" → CẤM, đây là AI red flags
- Verb chính chuẩn xác > adjective màu mè

## Gotchas

1. **chat-widget.js không có trong showcase repo** — nếu edit feature liên quan chat, sửa trong private repo, GitHub Actions sẽ tự sync (trừ file đó)
2. **AI chat đang pivot sang Cloudflare Worker** — Firebase Functions ở `~/Library/Mobile Documents/com~apple~CloudDocs/marshall-business/firebase-functions/` là BACKUP. Endpoint Worker đợi user deploy
3. **Sửa text bằng tay** — đừng dùng AI để generate copy. Marshall tự viết, AI chỉ refactor/fix
4. **Real social handles** (commit `91ab531`):
   - LinkedIn: `marshall-ng-64a157381`
   - Facebook: `hoang.huy.479254`
   - LINE: `marshallmarshall1308`
   - Zalo: `0909 326 188`
   - GitHub: `mrdeathisreal`
   - Instagram: `mrdeathisreal`
5. **Education timeline** đã correct: FTU transfer 2021–2023 (KHÔNG phải tốt nghiệp), MCU BSc 2023–2025, MCU MBA Sept 2025–Feb 2026 paused
6. **Job hiện tại**: Unimicron (Guishan, Taoyuan) production operator probation, May 2026 – present
7. **CV format**: crimson `#862633` accents, white bg, photo top-right, definition-list skills, margins 18/16/16mm

## Khi user yêu cầu thêm tính năng

1. KHÔNG generate marketing copy — hỏi Marshall viết tay
2. Giữ single-file architecture (HTML + CSS + JS in `index.html`)
3. Mọi text mới phải có 4 bản dịch EN/VI/zh-TW/zh-CN trong I18N dict
4. Test local trước khi commit: `python3 -m http.server 8000`
5. Commit message tiếng Anh, ngắn gọn, không dùng "✨" hay emoji

## Why this project matters

Marshall đang ở Unimicron Taiwan làm operator (rank thấp). Portfolio là leverage duy nhất để escape sang Sales/BD. **Mọi quyết định tone/content phải sharp như vũ khí, không phải template.**
