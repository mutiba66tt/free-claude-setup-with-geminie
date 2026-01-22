# Claude Code + Gemini Full Setup (Windows Guide)

This guide helps you set up Claude Code with Gemini models using `claude-code` and `claude-code-router`.

---

## Step 0 — Check Node.js Version

Open PowerShell and run:

```powershell
node --version
```
If Node.js version is less than 18, install it from:
```powershell
https://nodejs.org
```
🔥 STEP 1 — GET GOOGLE API KEY

Open: https://aistudio.google.com
Click → Get API Key
Click → Create API Key
Key copy kar len (example):
```powershell
AIzaSy........
```
🔥 STEP 2 — INSTALL REQUIRED TOOLS
PowerShell (Run as Administrator):
```powershell
npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router
```
🔥 STEP 3 — CREATE CONFIG FOLDERS
PowerShell (normal mode):
```powershell
mkdir $HOME/.claude-code-router
mkdir $HOME/.claude
```
🔥 STEP 4 — CREATE CONFIG.JSON (WINDOWS VERSION)
Windows me cat << EOF work nahi karta, isliye Notepad method use hoga.

Run:
```powershell
notepad $HOME/.claude-code-router/config.json
```
Notepad open hoga → isme ye exact JSON paste karein:
```powershell
{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "gemini",
      "api_base_url": "https://generativelanguage.googleapis.com/v1beta/models/",
      "api_key": "$GOOGLE_API_KEY",
      "models": [
        "gemini-2.5-flash",
        "gemini-2.0-flash"
      ],
      "transformer": {
        "use": ["gemini"]
      }
    }
  ],
  "Router": {
    "default": "gemini,gemini-2.5-flash",
    "background": "gemini,gemini-2.5-flash",
    "think": "gemini,gemini-2.5-flash",
    "longContext": "gemini,gemini-2.5-flash",
    "longContextThreshold": 60000
  }
}
```
✔ Save
✔ Close
🔥 STEP 5 — SET YOUR API KEY (WINDOWS METHOD)
PowerShell (Run as Admin):
```powershell
[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'YOUR_KEY_HERE', 'User')
```
Replace:
```powershell
YOUR_KEY_HERE
```
With your actual Google API Key.

Example:
```powershell
[System.Environment]::SetEnvironmentVariable('GOOGLE_API_KEY', 'AIzaSyXXXXX...', 'User')
```
⚠️ IMPORTANT
PowerShell close karen → new PowerShell open → check:
```powershell
echo $env:GOOGLE_API_KEY
```powershell
Agar value show ho jaye → Perfect! 🔥

🔥 STEP 6 — VERIFY EVERYTHING
Run:
```powershell
claude --version
ccr version
echo $env:GOOGLE_API_KEY
```
Agar sab commands ka output aa jaye → ✔ Setup success

🔥 STEP 7 — DAILY WORKFLOW
Terminal 1:
```powershell
ccr start
```
Wait until you see:

✔ Service started successfully
Terminal 2:
```powershell
cd your-project-folder ## vs code or cursor ky 2nd terminal my
ccr code
```
OR:
```powershell
eval "$(ccr activate)"
claude
```
🔥 VERIFICATION TEST
Terminal:
```powershell
ccr code
```
Then type:
```powershell
hi
```
Agar Claude reply kare →
🎉 Congratulations! FREE CLAUDE CODE + GEMINI WORKING! 🚀💯



