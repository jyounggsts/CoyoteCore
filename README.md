# CoyoteCore

**CoyoteCore** is a single-file, self-contained **employee portal** and **IT command center** for small-to-medium organizations. It features:

- Live employee roster
- Fleet/device management (computers, phones, iPads, etc.)
- Software license tracking
- Incident reports & LOA (Leave of Absence)
- Office supply/inventory catalog
- Powerful offline-first Knowledge Base + AI chatbot (KBC)
- IT utilities (password generator, QR codes, bulk tools, etc.)

Everything runs **100% in the browser** using localStorage (and IndexedDB for larger KB documents). No server required for core functionality.

## Features

### Core Portal
- Responsive dark-themed dashboard with cards for employees, devices, and stats
- Searchable roster with filters (department, role, status)
- Device enrollment status, ABM (Apple Business Manager), MDM tracking
- License seat tracking and alerts
- Incident reporting and LOA overlays

### KBC — Built-in AI Assistant
- **Offline-first**: Answers roster, device, license, inventory, and abbreviation questions instantly using pre-built logic
- **Knowledge Base**: Upload PDFs/DOCX documents for contextual answers
- **Optional Ollama integration**: Connect to a local LLM for advanced chat (runs fully on your machine)
- Smart follow-ups, voice input, conversation history, and related doc suggestions

### IT Utilities
- Password generator
- QR code generator (WiFi, contacts, etc.)
- Bulk vCard/contact packs
- Fleet age/upgrade analysis
- Many more tools

## Quick Start

1. Save the provided `CoyoteCore.html` file to your computer.
2. Open it in any modern browser (Chrome/Edge recommended).
3. (Optional but recommended) Place a `logo.png` file next to it for branding.
4. Start using the portal — data is saved locally in your browser.

## Organization Setup

CoyoteCore pulls configuration from your existing **Roster Manager** localStorage data (if present). To fully customize:

### 1. Basic Org Info
Open the browser console (F12) and run:

```js
localStorage.setItem('rosterManager.v1.orgConfig', JSON.stringify({
  orgName: "Your Company Name",
  portalTitle: "Your Company",
  portalSuffix: "Employee Portal",
  setupComplete: true
}));
```

Refresh the page. The title and branding will update.

### 2. Theme & Branding
The app automatically respects your existing `rosterTheme`, `rosterGlowSettings`, and custom themes. Accent color defaults to `#7da44e` (coyote green).

Place a `logo.png` (ideally 200x200px or larger) in the same folder as the HTML file.

### 3. Add Employees & Data
Use your existing Roster Manager import/export or manually populate via the UI (data persists in localStorage).

### 4. Knowledge Base (for KBC)
- Open the chatbot (floating coyote icon)
- Go to Settings → Upload PDFs or DOCX files
- They become searchable by the assistant

### 5. Optional: Connect Local AI (Ollama)
1. Install [Ollama](https://ollama.com/download)
2. Run in terminal: `ollama pull llama3.2` (or your preferred model)
3. In CoyoteCore chatbot → Click "Connect to Ollama"
4. (Windows CORS fix if needed):  
   ```powershell
   $env:OLLAMA_ORIGINS="*"; ollama serve
   ```

## Project Structure (Single File)

- `CoyoteCore.html` — Complete app (HTML + CSS + JS)
- `logo.png` (optional) — Branding logo

## Data Storage

All data is stored **locally in your browser**:
- `localStorage` — Roster, config, settings, chat history
- `IndexedDB` — Knowledge Base document content

**Backup tip**: Export chat history or roster data regularly.

## Keyboard Shortcuts

- `Esc` — Close chatbot or go back
- `Enter` — Send message in chat
- Chat supports voice input (microphone icon)

## Extending / Customizing

- Edit the JavaScript directly in the HTML file
- Modify CSS variables in `:root` for theming
- Extend the KBC offline engine (`kbcDataQueryEngine`, roster keywords, etc.)

---

**Made for IT teams who want a powerful, private, offline-first portal.**

Enjoy CoyoteCore! 🐺
