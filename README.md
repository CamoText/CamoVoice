# CamoVoice User Guide

**Fully Private, Offline Speech-to-Text**

---

## Overview

CamoVoice is a desktop speech-to-text application designed with one core principle: **your voice stays on your device**. Unlike cloud-based transcription services, CamoVoice processes everything locally using bundled AI models — no internet connection required, no data leaves your computer, and absolutely zero telemetry.

### Privacy & Architecture

- **100% Offline**: All transcription happens on your machine using faster-whisper, which runs entirely locally
- **Zero Telemetry**: CamoVoice collects nothing. No usage analytics, no crash reports, no audio samples
- **No Cloud Dependencies**: Once installed, the app works without any network connection
- **Local Settings**: Your preferences are stored in a simple `settings.json` file on your device and auto-loaded at open
- **English Optimized**: Purpose-built for English transcription with maximum accuracy

This architecture makes CamoVoice ideal for transcribing sensitive notes, legal dictation, personal journals, or any audio where privacy matters.

---

## User Interface

CamoVoice features a high-contrast, dark-themed interface designed for simplicity and accessibility.

### Main Window Layout

```
┌─────────────────────────────────────────────────────────────┐
│  [Load Audio File]          🎙 Record Button          Status     │
│  [Settings]        "Click or hold spacebar"     🎤 Device   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│                   Transcription Output                      │
│                      (editable text)                        │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  [Copy Text] [▶ Play] [Save As]       [Undo Clear] [Clear]  │
├─────────────────────────────────────────────────────────────┤
│  [Input Audio: ████████░░] ← (appears during recording)     │
├─────────────────────────────────────────────────────────────┤
│  Text Size: ═══════●═══════    Mode: [Fast|Thinking]        │
└─────────────────────────────────────────────────────────────┘
```

### Recording Audio

There are two ways to record:

1. **Click the Microphone Button**: Click once to start, click again to stop
2. **Hold Spacebar**: Hold spacebar to record, release to stop (push-to-talk style)
   - A brief 200ms delay prevents accidental recordings from quick taps
   - If you're typing in the text area, spacebar works normally

During recording, the microphone button pulses and fills with the accent color. When you stop, transcription begins automatically.

### Transcription Animation

When CamoVoice is processing your audio, you'll see an animated "Transcribing..." status with cycling dots, and the text area border will pulse with the accent color. This provides clear visual feedback that your audio is being processed.

### Audio Level Indicator

While recording, CamoVoice displays a thin **Input Audio** meter below the action buttons that shows real-time audio levels:

- **Orange gradient bar**: Shows current audio input level
- **Yellow peak indicator**: Marks the highest audio peaks
- **Automatic display**: Appears when recording starts
- **Smart hiding**: Disappears 1.5 seconds after recording stops

This visual feedback confirms your microphone is working and picking up audio.

### Loading Audio Files

Click **Load Audio File** to transcribe existing audio files. CamoVoice supports:

- **WAV** — Any sample rate or bit depth
- **MP3** — Standard MP3 files

The app automatically resamples to the required 16kHz and converts stereo to mono. Files currently have a 60 MB (Fast mode) and 30 MB (Thinking mode) size limit to prevent freezing.

> **Note**: M4A/AAC files are not supported. Convert them to WAV or MP3 before loading.

---

## Transcription Output

The large text area displays your transcriptions. Each new recording or file appends to existing text, making it easy to build up longer documents.

### Working with Text

- **Edit freely**: Click into the text area to make corrections or additions
- **Copy Text**: Copies all text to your clipboard
- **▶ Play**: Reads the transcription aloud using text-to-speech (see Playback Voice below)
- **Save As**: Opens a save dialog with timestamp options (see below)
- **Undo Clear**: Restores the most recently cleared text (grayed out when nothing to undo)
- **Clear**: Removes all text and timestamps

### Undo Clear

If you accidentally clear your text, you have two options:
- Click the **Undo Clear** button (located to the left of Clear)
- Press **Ctrl+Z** (Windows) or **⌘Z** (macOS)

This restores both the text and any associated timestamps from the most recent clear action. The Undo Clear button is grayed out when there's nothing to restore.

### Save As Options

When you click **Save As** (or press **Ctrl+S** / **⌘S**), a dialog appears with options:

- **Include date at top of document**: Adds a header with the current date
- **Include timestamp after each transcription**: Adds a `[Recorded: DD-Mon-YYYY HH:MM:SS]` line after each transcription segment (e.g., `[Recorded: 09-Jan-2026 14:32:15]`)
- **Include edits to transcription**: Saves the text exactly as it appears in the app, including any spelling corrections or edits you've made. When this is enabled, timestamps are disabled since edited text may no longer match the original transcription segments.

#### Export Formats

CamoVoice supports three export formats:

| Format | Extension | Best For |
|--------|-----------|----------|
| **Text File** | `.txt` | Universal compatibility, email, plain text editors |
| **Word Document** | `.docx` | Professional documents, further editing in Microsoft Word |
| **PDF Document** | `.pdf` | Sharing, archiving, printing (read-only format) |

Simply select your desired format from the "Save as type" dropdown in the file dialog.

Example output with both timestamp options enabled:
```
Transcription Record - 09-Jan-2026
========================================

This is my first transcription segment.
[Recorded: 09-Jan-2026 14:32:15]

This is my second transcription segment.
[Recorded: 09-Jan-2026 14:35:42]
```

---

## Transcription Modes

CamoVoice offers two transcription modes, selectable at the bottom of the window:

| Model Mode | Speed | Accuracy | Best For |
|------|-------|----------|----------|
| **Fast** | ★★★★★ | ★★★☆☆ | Quick notes, short recordings, real-time feel |
| **Thinking** | ★★★☆☆ | ★★★★★ | Important transcriptions, longer recordings |

- **Fast mode**: Uses the compact base model (~140MB) with greedy decoding for maximum speed. Great for quick voice memos, short dictation, or when you want near-instant results. Trades some accuracy for responsiveness.

- **Thinking mode**: Uses the full large model (~1.4GB) with beam search and voice activity detection. Better accuracy for complex vocabulary, accents, background noise, or professional transcription work.

Your mode selection is automatically saved. The model loads on first use of each mode, so the first transcription after opening the app or switching modes may take slightly longer.

Recordings have a time limit (currently 10 minutes for Fast, 5 minutes for Thinking) to prevent freezing; the recording will be automatically stopped and transcribed when the limit is reached. Break up recordings to avoid limits.

---

## Settings

Click the **Settings** button to open the settings panel.

### Input Device

Select which microphone to use for recording. Options include:
- **Default**: Uses your system's default input device
- All detected input devices are listed with their audio API

If you have multiple microphones (e.g., headset, webcam, USB mic), select the one you want to use here.

### Playback Voice

Choose the voice used for the **▶ Play** feature, which reads your transcription aloud.

**These are system voices installed on your device**, not voices bundled with CamoVoice. To add or remove voices:

- **Windows**: Settings → Time & Language → Speech → Manage voices
- **macOS**: System Settings → Accessibility → Spoken Content → System Voice → Manage Voices

The available voices depend on what you've installed on your operating system.

### Show Timestamps in Transcriptions

When enabled, each transcription segment displays its recording time directly in the app, formatted like a 24-hour ISO-style legal/medical record with unambiguous month abbreviations:

```
Your transcribed text here.
[Recorded: 09-Jan-2026 14:32:15]
```

This is useful for keeping track of when recordings were made. Timestamps are always stored internally — this setting just controls whether they're visible in the app. When you save, you can choose whether to include timestamps regardless of this display setting.

---

## Accessibility Features

### Scalable Interface

The **Text Size** slider adjusts the font size throughout the entire application — not just the transcription area. This includes:
- Transcription text
- All buttons and labels
- Status messages
- Mode selector

Slide right for larger text, left for smaller. Your preference is automatically saved.

This makes CamoVoice usable for:
- Users with visual impairments
- High-DPI displays
- Presentations or screen sharing
- Personal comfort preferences

### Keyboard Shortcuts

| Action | Windows | macOS |
|--------|---------|-------|
| Hold to record | Spacebar (hold) | Spacebar (hold) |
| Save As | Ctrl+S | ⌘S |
| Undo clear | Ctrl+Z | ⌘Z |

---

## How It Works (Technical)

CamoVoice is built on several key technologies:

### Speech Recognition
- **Two model options**: Fast mode uses base.en (~140MB), Thinking mode uses distil-large-v3 (~1.4GB)
- **faster-whisper**: CTranslate2-based implementation that's 4-6x faster than the original Whisper with lower memory usage
- Models are bundled with the application — no download required after installation
- All processing uses your CPU with int8 quantization for efficiency

### Audio Capture
- **SoundDevice**: Cross-platform audio recording
- Records at 16kHz mono (Whisper's native sample rate)
- Audio is processed directly in memory — no temporary files

### Text-to-Speech
- **pyttsx3**: Interfaces with your operating system's speech synthesis
- Uses voices installed on your system (SAPI5 on Windows, NSSpeechSynthesizer on macOS)

### User Interface
- **CustomTkinter**: Modern-looking Python GUI framework
- Dark theme with orange accent colors
- Responsive layout that scales with window size

---

## Troubleshooting

### "No voices available" for Playback
Your system may not have TTS voices installed. Install voices through your operating system's speech settings.

### Recording doesn't start
- Check that your microphone is connected and selected in Settings
- Ensure no other application is exclusively using the microphone
- Try selecting a different Input Device

### Transcription is inaccurate
- Speak clearly and at a moderate pace
- Reduce background noise
- Try switching to Thinking mode for better accuracy
- Ensure you're speaking English (CamoVoice is optimized for English)

### App is slow on first transcription
The first transcription may take slightly longer as the model initializes. Subsequent transcriptions will be faster. Switching modes also requires loading a different model.

---

## Tips for Best Results

1. **Speak clearly** with natural pacing — the model handles conversational speech well
2. **Minimize background noise** — even with noise handling, clearer audio = better results
3. **Use Fast mode** for quick notes or short sequential dictations, **Thinking mode** for important uninterrupted long transcriptions
4. **Edit as you go** — freely adjust the text manually to fix mistakes or add/remove text before or after transcriptions

---

## Enterprise Customization & Expansion Options

- 17 input languages: English, Spanish, French, German, Italian, Portuguese, Dutch, Russian, Chinese, Japanese, Korean, Polish, Turkish, Ukrainian, Arabic, Hindi, and Vietnamese
- Option to auto-detect input language
- Option to auto-translate to English
- Additional file formats for input sounds and output files
- Enhanced audit trail features and export formats

---

## Privacy Commitment

- ✓ No internet connection required after installation
- ✓ No accounts, no sign-ups, no authentication
- ✓ No analytics or usage tracking
- ✓ No audio sent to any server
- ✓ Settings stored locally in plain JSON
- ✓ Models bundled locally — no APIs, no third party exposure

---

*CamoVoice v0.0.1*

