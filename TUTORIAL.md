# Tutorial — a microphone for apps that don't have one

> **Version française :** [`TUTORIEL.fr.md`](TUTORIEL.fr.md).

## 1. What is it?

A **small voice-input module** added to an Electron chat app that has no microphone button.
You speak; the module transcribes your voice and inserts the text into the composer — as if
you had typed it.

It is not a separate app, not a server, not an account. It is **one lightweight JavaScript
file** (about 66 KB) added to the app's UI, plus a patcher to install it and roll back.

## 2. What is it for?

| Situation | What it adds |
|---|---|
| The app has no mic button | a mic button next to the send arrow |
| You want to dictate a long message | record → transcribe → insert |
| You want to send without clicking | auto-send when recording ends |
| You attach a file | the mic stays anchored; text and file go together |
| The agent is already working | the message is queued (when the app supports it) |
| You resize the window | the mic follows, to the right or above the arrow |

## 3. How it works

```
mic click → record (MediaRecorder)
          → stop
          → send audio to Gemini (API key)
          → transcribed text
          → insert into the composer
          → auto-send (optional)
```

Everything runs **inside the app**, in the UI. No intermediary server, no telemetry, no
account. The Gemini key stays in the app's local storage (`localStorage`) and is sent only to
Google for transcription.

## 4. Requirements

| Need | Detail |
|---|---|
| **A free Gemini API key** | created in Google AI Studio; the only external dependency |
| **An Internet connection** | to reach Gemini |
| **The target app** | Reasonix Studio 2.40.0 (current), AionUi 2.2.2, Open Cowork |
| **Nothing else** | no Node, no Python, no build, no account |

The module is **self-contained and light**: one JS file + one `<script>` tag. It adds no
dependency to the app.

## 5. Install (Reasonix Studio)

1. Close or leave Reasonix Studio open — the patcher never closes it.
2. Recommended: run `PREPARER-SAUVEGARDE-MIC-REASONIX.bat` — creates and verifies
   `index.html.bak` + `.sha256` **without modifying the app**.
3. Run `INSTALLER-MIC-REASONIX.bat`.
4. Reload (`Ctrl+R`) or relaunch the app.
5. The mic appears next to the send arrow.

For other apps the method is the same; only the installation type changes (plain folder or
asar). See [`docs/METHODOLOGY.md`](docs/METHODOLOGY.md) and
[`docs/SUPPORTED-APPS.md`](docs/SUPPORTED-APPS.md).

## 6. Get the Gemini key

1. Go to **Google AI Studio** (`https://aistudio.google.com/apikey`).
2. Create an API key (the free tier is enough for personal use).
3. Copy the key (`AIza…`).
4. In the app: **right-click the mic** → paste the key → **Save**.
5. Click **Test the Gemini key**. The panel must confirm the key is valid and the model
   answers.

The key is stored locally. Never put it in a Git repository, a screenshot or a public message.

## 7. Use it

| Gesture | Effect |
|---|---|
| **Click** the mic | starts recording; the icon becomes “stop” |
| **Click** again | stops, transcribes, inserts the text |
| **Right-click** | opens settings (key, model, language, options) |
| **Auto-send** | sends the message when transcription ends |
| **Send keyword** | if enabled, a trailing keyword (e.g. “send”) triggers sending |
| **Attachment** | attach the file first, then dictate; text and file go together |
| **Agent busy** | the message is queued when the app supports it |

## 8. Settings

| Setting | Role |
|---|---|
| Gemini key | required for transcription |
| Model | Gemini model used for transcription |
| Language | dictation language (French by default) |
| Auto-insert | insert text without confirmation |
| Auto-send | send after insertion |
| Send keyword | send only if the text contains the keyword |

## 9. Rollback / update

| Situation | Action |
|---|---|
| Problem after patching | `RESTAURER-MIC-REASONIX.bat` |
| App no longer starts | close it, run `RESTAURER-MIC-REASONIX.bat`, relaunch |
| App update | `PREPARER-SAUVEGARDE...` then `REAPPLIQUER-MIC-REASONIX.bat` |
| Check state | `VERIFIER-MIC-REASONIX.bat` (read-only) |

The backup and its checksum are kept; rollback works even if the app no longer starts.

## 10. Troubleshooting

| Symptom | Check |
|---|---|
| No mic | page not reloaded; script tag missing; JS error in the console |
| “No Gemini API key” | key not saved; right-click → Save → Test |
| Key rejected | wrong key, quota, or model unavailable; test again |
| Nothing inserted | composer not found; check selectors (inspection) |
| Mic misplaced | send selector changed; see `docs/METHODOLOGY.md` |
| Message not sent | send button disabled (upload/render); the module retries ~2 s |
| Agent is working | the app may interject or queue depending on its state |
| After an app update | reapply the patch (the UI folder was replaced) |

## 11. Windows / local variant

The transcription backend is **replaceable**. Today: Gemini. Tomorrow, to remove the key
and/or the Internet:

| Backend | Advantage | Constraint |
|---|---|---|
| Gemini (current) | quality, languages, no install | key + Internet |
| Windows `System.Speech` | local, no key | needs a small host-side helper (PowerShell/.NET) and IPC; language/quality vary |
| `Windows.Media.SpeechRecognition` | local, WinRT | Node/UWP bridge, language packs, more complex |
| Local Whisper | high quality | heavy model, CPU/GPU, install |

The key point: **the module keeps recording, insertion and sending**; only `transcribe()`
changes. The method and anchoring stay the same. The Windows variant is **not implemented in
v1**; it needs a bridge on the app side (the renderer is sandboxed and cannot spawn a
process). It is a documented option, not a promise.

## 12. Other apps

| App | UI | Patch | Repo |
|---|---|---|---|
| Reasonix Studio 2.40.0 | `frontend-next\dist` | copy + script tag | this repo |
| AionUi 2.2.2 | `app.asar` | asar repack | `AiTron-Voice-Input` |
| Open Cowork | Electron | same module | `AiTron-Voice-Input` (base) |

The 8-step method is the same: locate controls, determine packaging, adapt storage and
preload, anchor, verify, keep a rollback, document.

## 13. Privacy and security

- No telemetry, no intermediary server.
- Audio goes directly to Google Gemini with **your** key.
- The key is in the app's local storage; it is not in this repository.
- The module does not read conversations; it only touches the composer and send button.
- **Unofficial** project, provided as is, without warranty; see `LICENSE`.
