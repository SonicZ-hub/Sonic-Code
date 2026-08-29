# SONIC CODE

**choice of mobile coders**

AI full-stack website & app builder CLI with live preview links and AI image generation — runs entirely on your **mobile phone**.

---

## Run on Mobile (Termux for Android)

### 1. Install Termux
Get Termux from **F-Droid**: https://f-droid.org/en/packages/com.termux/
(The Play Store version is outdated — use F-Droid.)

### 2. Set up Node.js
```bash
pkg update && pkg upgrade -y
pkg install nodejs git -y
node -v   # must be 18 or higher
```

### 3. Get Sonic Code
```bash
# unzip the source
pkg install unzip -y
unzip sonic-code.zip
cd sonic-code
```

### 4. Install dependencies
```bash
npm install
```

### 5. Add your API keys
```bash
cp .env.example .env
nano .env
```
Fill in:

| Key | Where to get it |
|---|---|
| `OPENROUTER_API_KEY` | https://openrouter.ai/keys |
| `NVIDIA_API_KEY` | https://build.nvidia.com |
| `PUTER_AUTH_TOKEN` | https://puter.com/dashboard → **Create token** |

Set `AI_PROVIDER=openrouter` or `AI_PROVIDER=nvidia`.
(If you skip this step, Sonic Code will ask you for the keys on first run.)

### 6. Start Sonic Code
```bash
npm start
```

### 7. Use the menu
```
  Full Stack Website   → describe it, get files + live preview link (https://xxx.puter.site)
  Full Stack App       → same, app-style UI
  Chat with AI         → talk to your OpenRouter/NVIDIA model
  Photo Generator      → text → image via Puter AI (saved to ./images/)
```

Generated projects are saved in `./projects/<name>/` and deployed to Puter hosting automatically — the preview link prints at the end.

---

## Files
```
sonic-code/
├── bin/sonic-code.js   # CLI entry
├── src/
│   ├── index.js        # startup
│   ├── banner.js       # yellow SONIC CODE banner
│   ├── menu.js         # main menu
│   ├── config.js       # API key setup (.env)
│   ├── ai.js           # OpenRouter / NVIDIA chat API
│   ├── build.js        # full-stack generator + deploy
│   ├── chat.js         # chat with AI
│   ├── imagegen.js     # Puter image generation
│   ├── prompts.js      # code-gen prompts
│   └── puter.js        # Puter hosting + txt2img
├── package.json
├── .env.example
└── README.md
```

## Requirements
- Android phone with Termux (or any Node.js 18+ environment)
- OpenRouter **or** NVIDIA API key (for AI building/chat)
- Puter auth token (for preview links & image generation)
