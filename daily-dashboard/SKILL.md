---
name: morning-dashboard
description: Generates a concise, thoughtful Personal Morning Dashboard delivered directly in Claude chat each morning. Use this skill whenever the user asks for their morning dashboard, morning briefing, daily brief, or morning update — or if they say anything like "give me my morning brief", "run the morning skill", or "what's my dashboard today". Also triggers if this is a scheduled 8:15 AM morning delivery. Always use this skill for morning daily briefings — do not generate ad-hoc without it.
---

# Personal Morning Dashboard Skill

Generates a daily personal morning dashboard for a man in his mid-40s navigating responsibility, purpose, family, and work. Delivered in Claude chat. Readable in under 5 minutes.

---

## Output Structure

Produce exactly four sections in order. Total word count: ~400–500 words. No filler, no fluff.

---

### 1. 🙏 Devotional (Tim Keller / Erwin McManus Style)

Write one paragraph (4–6 sentences) in the voice of Tim Keller or Erwin McManus — whichever voice fits the theme better that day.

**Requirements:**

- Audience: A man in his mid-40s navigating responsibility, purpose, family, and faith
- Tone: Grounded, honest, encouraging — never cliché, never abstract
- Must weave in a **subtle principle from Proverbs** (don't quote it directly — let it breathe as a concept)
- Goal: Frame the day with clarity, humility, and forward motion
- Vary the theme daily: some days are about leadership, some about rest, some about fatherhood, some about perseverance

---

### 2. 📖 Word of the Day

Choose one high-quality, genuinely useful word. Avoid obscure-for-obscure's-sake words. Prefer words that sharpen thinking or communication.

Format:
**Word**: [word]
**Pronunciation**: [IPA notation] — [plain-English phonetic spelling, e.g. "eh-KWAH-nih-mih-tee"] — and generate a small inline HTML audio widget (see Audio Pronunciation section below)
**Definition**: [clear, plain-language definition]
**Why it's useful**: [1 sentence on what gap it fills in thinking or speech]
**Work context**: [1 sentence example]
**Life context**: [1 sentence example]

#### Audio Pronunciation Widget

Deliver the pronunciation in **two ways**:

**1. Inline widget (primary)** — Use the `show_widget` tool to render an interactive HTML audio player directly in the Claude chat interface. This lets the user hear the word immediately without opening any file. Use this HTML template:

```html
<div
  style="font-family: Georgia, serif; max-width: 480px; margin: 0 auto; text-align: center; padding: 32px 24px; background: #fafaf8; border-radius: 12px; border: 1px solid #e8e4dc;"
>
  <h1 style="font-size: 2.5rem; margin-bottom: 4px; color: #1a1a1a;">[WORD]</h1>
  <p style="color: #888; font-size: 1.05rem; margin-bottom: 16px;">
    [IPA] · [phonetic]
  </p>
  <p style="font-size: 1.05rem; margin: 16px 0; color: #333; line-height: 1.5;">
    [definition]
  </p>
  <button
    onclick="speak()"
    style="font-size: 1rem; padding: 10px 28px; cursor: pointer; background: #2c2c2c; color: white; border: none; border-radius: 8px; margin-top: 8px;"
  >
    🔊 Hear it again
  </button>
  <script>
    function speak() {
      const u = new SpeechSynthesisUtterance("[WORD]");
      u.rate = 0.85;
      window.speechSynthesis.speak(u);
    }
    setTimeout(speak, 800);
  </script>
</div>
```

Call `show_widget` with `title: "word_of_the_day_[WORD]"` and one loading message like `"Loading today's word..."`.

**2. Saved HTML file (backup)** — Also save the same HTML file to:
`/Users/anthony/Sites/sicktastic/skill-issue/daily-dashboard/word-of-the-day/word-of-the-day.html`

Create the directory if it doesn't exist (`mkdir -p`). Include the file path in the Slack message so the user can open it in a browser if needed.

---

### 3. 🤖 AI Trends (Signal, Not Noise)

1–2 meaningful AI developments from the past 24–48 hours. Use web search to find the most current, credible information.

**Requirements:**

- Use web search to pull fresh, real news — no hallucinated stories
- Focus on: product launches, research breakthroughs, policy changes, or industry shifts
- Explain **why it matters** — implications for product teams, data professionals, or real-world applications
- No hype, no speculation, no filler
- Format: One short paragraph per item (2–3 sentences max)
  **Thumbnails:**
- For each AI trend item, call `image_search` with a short, specific query (e.g., the company name + product, or the core technology) to fetch a relevant thumbnail
- Display the image inline, just above or beside the story text, using the `image_search` tool's inline rendering
- Use `max_results: 3` and let the best image render — don't narrate the search, just show it naturally before the story text

---

### 4. 📰 Current Events (High-Signal Summary)

2–3 important stories from today. Use web search to find current news.

**Requirements:**

- Use web search — prioritize NYT, WSJ, NPR, Reuters, AP
- Each story: 1–2 sentences. What happened + **why it matters**
- Avoid entertainment, celebrity, or sports unless geopolitically significant
- Choose stories across different domains (e.g., economy, politics, world affairs)
  **Thumbnails:**
- For each current events story, call `image_search` with a tight, descriptive query (e.g., the location, event, or key figure involved) to fetch a relevant thumbnail
- Display the image inline just above the story text
- Use `max_results: 3` — keep it clean and don't narrate the search

---

## Delivery

After generating the dashboard content:

**Step 1 — Render the Word of the Day widget inline** using `show_widget` so the pronunciation plays directly in the Claude chat interface.

**Step 2 — Save the HTML file** to `/Users/anthony/Sites/sicktastic/skill-issue/daily-dashboard/word-of-the-day/word-of-the-day.html` as a backup (create the directory with `mkdir -p` if needed). Include the file path at the end of the dashboard, e.g.:

> 🔊 _Word audio saved → `/Users/anthony/Sites/sicktastic/skill-issue/daily-dashboard/word-of-the-day/word-of-the-day.html`_

**Formatting**:

- Use markdown formatting throughout
- Use emoji section headers as shown above
- Keep it scannable — short paragraphs, clear breaks between sections

---

## Scheduling via Claude Cowork

This skill is designed to run automatically every morning at **8:15 AM Central** via Claude Cowork's built-in scheduled tasks — no external tools like Zapier needed.

**One-time setup instructions (tell the user on first run):**

1. Open **Claude Desktop** and go to the **Cowork** tab
2. Click **Schedule** in the sidebar → **+ New Task**
3. Name it: `Morning Dashboard`
4. Paste this as the prompt:
   > _Run my morning dashboard skill. Generate today's devotional, word of the day with audio file, AI trends, and current events._
5. Set frequency: **Weekdays**, time: **8:15 AM**
6. Click **Save** — then hit **Run now** to verify it works
   **Important notes:**

- Cowork scheduled tasks require **Claude Desktop to be open and awake** at the scheduled time
- Results are saved in Cowork's session history so you can review any run
- Each run gets its own fresh session with access to web search and this skill

---

## Style Guidelines

- Tone across all sections: thoughtful, calm, intelligent
- Write like a trusted advisor who respects the reader's time
- No motivational-poster language
- The devotional should feel written, not generated
- The word should feel chosen, not random
- The news should feel curated, not scraped

---

## Tools Required

- `web_search` — for AI trends and current events (always search fresh, never use memory for news)
- `image_search` — to fetch relevant thumbnails for each AI trend and current events story
- `show_widget` — to render the Word of the Day audio player inline in Claude chat
- File system (bash / `create_file`) — to save the Word of the Day HTML file to `/Users/anthony/Sites/sicktastic/skill-issue/daily-dashboard/word-of-the-day/`

---

## Example Output Shape

```
🙏 *Devotional*

[4–6 sentence paragraph in Keller/McManus voice]

---

📖 *Word of the Day: [word]*

*Pronunciation*: /IPA/ · pho-NET-ic
*Definition*: ...
*Why it's useful*: ...
*Work*: ...
*Life*: ...
🔊 _[inline audio widget renders here in Claude chat]_
🔊 _Backup saved → `word-of-the-day.html`_

---

🤖 *AI Trends*

[thumbnail image for story 1]
**[Headline]** — [2–3 sentence summary with why it matters]

[thumbnail image for story 2]
**[Headline]** — [2–3 sentence summary with why it matters]

---

📰 *Current Events*

[thumbnail image]
• *[Story 1 headline]* — [1–2 sentences]

[thumbnail image]
• *[Story 2 headline]* — [1–2 sentences]

[thumbnail image]
• *[Story 3 headline]* — [1–2 sentences]
```
