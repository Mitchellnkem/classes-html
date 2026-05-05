# ChatGPT Clone — Frontend UI

A production-quality frontend clone of the ChatGPT interface built with **pure HTML5, CSS3, and Vanilla JavaScript** — no frameworks, no build tools, no dependencies.

---

## 📁 Project Structure

```
chatgpt-clone/
├── index.html          # App shell, semantic HTML structure
├── css/
│   └── styles.css      # All styling — tokens, layout, components, animations
├── js/
│   └── app.js          # All logic — state, storage, render, events
├── assets/
│   └── icons/          # Reserved for any future icon assets
└── README.md
```

---

## 🚀 Quick Start

No build step needed. Just open `index.html` in any modern browser:

```bash
# Option 1 — double-click index.html
# Option 2 — serve locally (recommended for localStorage to work fully)
npx serve .
# or
python -m http.server 8080
```

Then visit `http://localhost:8080`

---

## ✨ Features

### Sidebar
- Fixed sidebar with **New Chat** button
- Scrollable chat history list
- Active chat highlighted
- **Inline rename** — click the pencil icon or use the context menu
- **Delete chat** — with confirmation prompt
- Collapses into a drawer on mobile with backdrop overlay

### Chat Area
- Clean message bubbles — user (right-aligned box) vs AI (left with avatar)
- Auto-scroll to latest message
- **Typewriter animation** for AI responses
- **Typing indicator** (three bouncing dots) while AI "thinks"
- Copy button on AI messages
- Basic Markdown formatting: `**bold**`, `*italic*`, `` `inline code` ``, code blocks

### Input Section
- Auto-resizing textarea (grows up to 200px)
- Send button (disabled when empty)
- **Enter** to send, **Shift+Enter** for newline
- Glowing focus ring on the input wrapper

### Empty State
- Welcome screen with GPT logo
- 4 suggestion cards that auto-fill and send when clicked

### Storage
- All chats and messages persisted to **localStorage**
- Survives page refresh, tab close, and browser restart
- Theme preference also saved

### Theme
- **Dark mode** (default) / **Light mode** toggle in sidebar footer
- Smooth CSS transitions between themes

---

## 🎨 Design Decisions

| Token | Value |
|---|---|
| Font (UI) | Sora (Google Fonts) |
| Font (AI mono) | DM Mono |
| Accent color | `#10a37f` (OpenAI green) |
| Sidebar width | `260px` |
| Max chat width | `768px` |
| Border radius | `6px / 12px / 16px / 24px` |

CSS custom properties (`var(--*)`) drive the entire theming system — switching from dark to light is a single `data-theme` attribute change on `<html>`.

---

## 🧠 Architecture Notes

```
State (single JS object)
  └── chats[]          → array of chat sessions
  └── activeChatId     → which chat is shown
  └── isTyping         → prevents double-sends

Storage helpers
  └── loadChats()      → localStorage → state
  └── saveChats()      → state → localStorage

Render functions (state → DOM)
  └── renderChatList()
  └── renderMessages()
  └── renderAIMessageTypewriter()
  └── renderTypingIndicator()

Event listeners
  └── input, keydown, click — all registered in initEventListeners()
```

---

## 🛣️ Potential Enhancements

- [ ] Real AI integration (Anthropic / OpenAI API)
- [ ] Search through chat history
- [ ] Export chat as Markdown / PDF
- [ ] Message editing
- [ ] Syntax highlighting in code blocks (Prism.js)
- [ ] PWA / offline support

---

## 🧑‍💻 Author

Built by **Mitchell** as a frontend learning project.  
Stack: HTML5 · CSS3 · Vanilla JavaScript · LocalStorage
