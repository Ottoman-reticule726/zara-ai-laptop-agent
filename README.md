<div align="center">

# Zara — Control Your Windows Laptop From Your Phone

**An AI agent that runs on your PC and takes orders from Discord — by text or by voice, in English or Urdu.**

Send a message from anywhere. Zara takes a screenshot, runs the command, opens the app,
fixes the Wi-Fi, sends the file — then replies with the result and a picture of your screen.

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white)](https://python.org)
[![Platform](https://img.shields.io/badge/Windows-10%20%7C%2011-0078D6?logo=windows&logoColor=white)](#requirements)
[![Developed by Tanzeel](https://img.shields.io/badge/Developed%20by-Tanzeel-6C3EF5)](https://github.com/tanzeeldevAi)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#contributing)

</div>

---

## What is this?

Zara is a **remote laptop assistant**. She lives on your Windows PC and listens to a private
Discord channel that only *you* can talk to.

You are outside. Your laptop is at home. You send:

> *"screenshot bhejo aur batao laptop kaisa chal raha hai"*

…and a few seconds later you get a picture of your screen and a spoken reply in Urdu.

She is not a chatbot with a fixed menu. She is an **AI agent** — a brain (Claude) plus **38 tools**
(screenshot, shell, files, mouse, keyboard, apps, Wi-Fi). She decides which tools to use and
chains them together on her own.

```
Your phone  ──►  Discord  ──►  Your laptop  ──►  Claude (brain)  ──►  Tools
     ▲                                                                   │
     └──────────  text · screenshots · voice reply  ◄───────────────────┘
```

---

## What she can do

| | |
|---|---|
| 📸 **See your screen** | Takes screenshots — and actually *reads* them to decide what to do next |
| 💻 **Run anything** | Any PowerShell command, install software, check logs, run builds |
| 📁 **Files** | Read, write, search, and send files to your phone |
| 🖱️ **Use apps like a human** | Opens apps, focuses windows, clicks, types, pastes long text instantly |
| 💬 **WhatsApp** | Opens a chat and sends a message for you |
| 🎙️ **Voice in** | Send a voice note in **English or Urdu** — she understands it |
| 🔊 **Voice out** | Replies in a natural female voice, in the same language you used |
| 🩺 **System health** | CPU, RAM, disk, battery, biggest processes — and frees RAM when asked |
| 📶 **Fixes its own Wi-Fi** | Detects the charger coming back after a power cut and reconnects by itself |
| ♻️ **Never dies** | Auto-starts at login, a watchdog restarts her within 3 minutes if she stops |

---

## Requirements

Before you start, make sure you have:

- **Windows 10 or 11** — this does not run on Mac or Linux
- **[Python 3.10+](https://python.org/downloads)** — while installing, tick **"Add Python to PATH"**
- **A Claude subscription** (Claude Pro/Max) **or** an [Anthropic API key](https://console.anthropic.com)
- **A Discord account** (free)

> Zara can run on your **existing Claude subscription** through the Claude Code CLI — no
> separate per-token API bill. An API key also works if you prefer.

---

## Install — step by step

It takes about **10 minutes**. You do not need to write any code.

### Step 1 — Download

```bash
git clone https://github.com/tanzeeldevAi/zara-ai-laptop-agent.git
```

No git? Click the green **Code** button above → **Download ZIP** → unzip it somewhere like `D:\zara`.

### Step 2 — Create your Discord bot

1. Open <https://discord.com/developers/applications>
2. Click **New Application** → name it `Zara` → **Create**
3. In the left menu click **Bot**
4. Scroll down to **Privileged Gateway Intents** and turn **ON** → **MESSAGE CONTENT INTENT** → **Save Changes**

   > ⚠️ **Do not skip this.** Without it, Zara appears online but cannot read a single message.
   > This is the #1 reason people get stuck.

5. Click **Reset Token** → **Copy**. This is your **bot token** — keep it private.

### Step 3 — Make a server and invite her

A Discord bot can only be messaged if you share a server with it.

1. In the Discord app, click **+** on the left → **Create My Own** → **For me and my friends** → name it `Laptop`
2. Back in the developer portal: **OAuth2** → **URL Generator**
3. Under **Scopes**, tick **`bot`**
4. Under **Bot Permissions**, tick: **Send Messages**, **Attach Files**, **Read Message History**, **Embed Links**
5. Copy the generated URL at the bottom, open it in your browser, pick your **Laptop** server → **Authorize**

### Step 4 — Get your Discord user ID

This is the security lock: **only this ID can command your laptop.** Everyone else is refused.

1. Discord → **Settings** → **Advanced** → turn on **Developer Mode**
2. Right-click **your own name** in the bottom-left corner
3. Click **Copy User ID**

### Step 5 — Install

Double-click **`install.bat`**

It creates a virtual environment, installs everything, and opens `.env` in Notepad.
Fill in the two lines:

```ini
DISCORD_BOT_TOKEN=paste_your_bot_token_here
DISCORD_ALLOWED_USER_IDS=paste_your_user_id_here
```

Save the file and close it.

### Step 6 — Start her

Double-click **`START_ZARA.bat`**

Now open Discord on your phone, go to your **Laptop** server, and send:

```
/help
```

Then try:

```
screenshot my screen
```

**That's it — you're running.** 🎉

---

## Optional extras

### Make voice replies fast (free)

Voice notes are transcribed on your CPU by default, which takes ~13 seconds. With a free
[Groq](https://console.groq.com) key it drops to about **1 second**, and Urdu accuracy improves a lot.

1. Get a free key at <https://console.groq.com> → **API Keys** → **Create API Key**
2. Double-click **`SET_GROQ_KEY.bat`** and paste it

### Make her voice sound human

By default Zara uses free Microsoft neural voices — clear, but a little flat. For a realistic
voice with actual emotion (`[warmly]`, `[laughs]`, `[sighs]`), add an
[ElevenLabs](https://elevenlabs.io) key:

1. Double-click **`SET_VOICE_KEY.bat`** and paste your key
2. Check what your plan supports:
   ```bash
   .venv\Scripts\python.exe check_voice.py
   ```

If ElevenLabs is unavailable or out of credits, she silently falls back to the free voices —
nothing breaks.

### Keep her running forever

Double-click **`INSTALL_AUTOSTART.bat`** → click **Yes** on the Windows prompt.

From then on she starts at login, restarts herself within 3 minutes if she ever stops, and
reconnects on her own when the internet comes back — then messages you *"back online"*.

For surviving a full power cut while you're away, read **[AUTOSTART-NOTES.txt](AUTOSTART-NOTES.txt)**.

---

## Commands

| Command | What it does |
|---|---|
| `/help` | Show help |
| `/new` | Forget the conversation and start fresh |
| `/stop` | Cancel whatever she is doing |
| `/shot` | Instant screenshot |
| `/status` | Instant system health |
| `/voice on` · `off` · `auto` | Control voice replies |

Everything else is just plain English or Urdu:

> *"open chrome and go to gmail, then screenshot it"*
> *"what's eating my RAM? close the worst one"*
> *"find every invoice PDF in Documents from this year and send me the biggest"*
> *"WhatsApp par Ali ko bhejo: main 10 minute mein aa raha hoon"*
> *"pull the latest changes in D:\my-project, run the tests, show me any failures"*

---

## Security

This tool gives an AI real control of your computer, so the design is deliberately strict:

- **Only your Discord user ID** can issue commands. Everyone else is refused and logged — even
  people inside your own server.
- **Your `.env` file holds the keys to your machine.** Never commit it, never share it, never open
  it while screen-sharing. It is already in `.gitignore`.
- **Everything she reads is treated as data, not orders.** A web page, document or chat message
  that says *"delete everything"* will not be obeyed — she shows it to you instead.
- **She will not type your passwords or card numbers** into forms.
- Set `CONFIRM_RISKY=true` in `.env` to make destructive actions (delete, shutdown, registry,
  format) ask you for a **Run it / Cancel** confirmation first.

> Use this on a computer you own. You are responsible for what you ask it to do.

---

## Troubleshooting

<details>
<summary><b>She shows online but never replies</b></summary>

**MESSAGE CONTENT INTENT** is off. Go back to Step 2.4. This causes 9 out of 10 problems.
</details>

<details>
<summary><b>"You are not authorised to control this machine"</b></summary>

Your `DISCORD_ALLOWED_USER_IDS` is wrong. Redo Step 4 — make sure you copied *your* user ID,
not the bot's application ID.
</details>

<details>
<summary><b>Nothing happens when I run install.bat</b></summary>

Python isn't installed, or "Add Python to PATH" wasn't ticked during install. Reinstall Python
and tick that box.
</details>

<details>
<summary><b>I can't find the bot to message it</b></summary>

You haven't invited it to a server yet — do Step 3. A bot can't be DMed unless you share a server.
</details>

<details>
<summary><b>Voice notes are ignored</b></summary>

The first voice note downloads a speech model (~0.5 GB) once, so it's slow the first time.
After that it's fast. Add a Groq key to make it about 1 second.
</details>

<details>
<summary><b>She stops in the middle of a long job</b></summary>

Raise `MAX_ITERATIONS` in `.env` (default 400). Every click, wait and screenshot counts as one
step, so very long jobs can hit the ceiling. She also auto-continues 3 times before pausing.
</details>

---

## How it works

- **Discord** is the transport — no open ports, no port forwarding, no tunnel, no static IP.
  Your laptop connects outward, so it works behind any router.
- **Claude** is the brain, via the [Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk/overview),
  running on your existing subscription.
- **Tools** are small Python functions exposed to the model as an in-process MCP server.
  The model picks which to call.
- **Speech to text**: [faster-whisper](https://github.com/SYSTRAN/faster-whisper) locally, or Groq's
  `whisper-large-v3` in the cloud.
- **Text to speech**: [edge-tts](https://github.com/rany2/edge-tts) free, or ElevenLabs for
  emotional voices.

Want to add your own ability? Drop a function in `agent/tools/`, decorate it with `@tool(...)`,
and Zara can use it immediately.

---

## Contributing

Issues and pull requests are welcome — especially new tools, better Urdu voice support, and
Linux/Mac ports.

## License

[MIT](LICENSE) — free to use, change and share. If it helps you, a ⭐ on the repo is appreciated.

---

<div align="center">

**Built by [@tanzeeldevAi](https://github.com/tanzeeldevAi)**

*AI agent · personal AI assistant · remote PC control · control laptop from phone · Discord bot
Python · Windows automation · Claude AI agent · computer use agent · voice assistant · Urdu voice
assistant · speech to text · text to speech · LLM agent · self-hosted AI assistant*

</div>
