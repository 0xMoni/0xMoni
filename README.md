# Hey, I'm Moni 👋

Third-year CS student building across the stack — and sometimes below it. Some of my projects have paying users. One of them is a SQL query engine that outruns SQLite.

---

## 🏆 Highlights

- 💳 **20+ users and paying subscribers** on UniTrack, with live Razorpay billing
- ⚡ Built a query engine **5x faster than SQLite** on 1M-row analytical queries
- 🚀 5+ production apps shipped, deployed, and in real use
- 🌍 Apps used by students across colleges

---

## 🛠 Tech Stack

**Languages:**
C++ · Python · TypeScript · JavaScript · SQL

**Frontend:**
React Native (Expo) · Next.js · React · Tailwind CSS

**Backend & Database:**
Node.js · Firebase · Supabase (PostgreSQL) · MongoDB · MySQL · SQLite

**Systems & Data:**
NumPy · Query Optimization · Vectorized Execution · Performance Profiling

**AI:**
Gemini API · YOLO · OpenCV · MediaPipe

**Tools:**
Git · GitHub Actions · Docker · Vercel · Figma · Postman · Claude Code

---

## 📌 Projects

| Project | Description | Stack & Links |
|---------|-------------|---------------|
| **Quarry** | A SQL query engine written from scratch — hand-written lexer, recursive-descent parser, logical planner and vectorized executor over columnar storage. **Median 5x faster than SQLite** on 1M rows | Python · NumPy<br>💻 [Code](https://github.com/0xMoni/quarry) |
| **UniTrack** | Attendance SaaS with Razorpay billing, webhook verification and **20+ paying users** | React Native · Firebase · Gemini API<br>🌐 [Live](https://unitrack-web.vercel.app) · 💻 [Code](https://github.com/0xMoni/UniTrack-app) |
| **goIRL** | Discover hackathons and tech events on an interactive 3D map, aggregated from MLH, Lu.ma and Devfolio | Next.js · Supabase · MapLibre GL<br>🌐 [Live](https://goirl-tau.vercel.app) · 💻 [Code](https://github.com/0xMoni/goIRL) |
| **LitterLens** | Detects garbage from satellite imagery and notifies local authorities in **under 30 seconds** | React Native · YOLO · Firebase<br>💻 [Code](https://github.com/0xMoni/LitterLens) |

---

## ⚡ Deep Dive: Quarry

The first working version was **2.5x slower than SQLite** at `GROUP BY`, despite being 6x faster at everything else. Profiling found one line:

```
np.unique on 1,000,000 object strings : 655.7 ms
np.unique on 1,000,000 int64 values   :  21.2 ms
```

Grouping by a string column meant sorting a million Python string *objects* — every comparison round-tripping through the interpreter.

The fix was **dictionary encoding**, the same technique Parquet and Arrow use: store text as `int32` codes plus a dictionary of distinct values.

| | before | after |
|---|---:|---:|
| `GROUP BY` 1 key | 731 ms | **53 ms** |
| median vs SQLite | 0.4x | **5.0x** |

A **13.8x** improvement from changing how strings are stored, not how grouping works. All 68 tests — including 17 differential tests against SQLite — still passed afterwards, which is what made the rewrite safe to attempt.

[**Read the full writeup →**](https://github.com/0xMoni/quarry)

---

## 🛠 Currently Building

### CryptoPath

Making crypto easier for beginners.

Features:
- 📚 Bite-sized learning cards
- 📈 Paper trading with live market prices
- 💬 Jargon translator
- 🚫 No hype, no shilling — just learning

**Stack:** Next.js · TypeScript · Tailwind CSS

---

## 📊 GitHub Stats

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=0xMoni&show_icons=true&theme=transparent&hide_border=true&title_color=58a6ff&icon_color=58a6ff&text_color=c9d1d9)

---

## 🌐 Connect

- 🌍 **Portfolio:** https://monikumari.vercel.app
- 💼 **LinkedIn:** https://linkedin.com/in/moni-kumari
- 🧩 **LeetCode:** https://leetcode.com/u/monii_07
- 🐦 **Twitter/X:** https://twitter.com/monii_k07

---

> Most of my projects start because I get annoyed by a problem and decide to build the solution.
