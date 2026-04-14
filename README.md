
<div align="center">

# 🧠 FRIDAY AI Assistant
### *An Iron Man–Inspired AI Assistant with Holographic Interface & Gesture Control*

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python)
![Flask](https://img.shields.io/badge/Flask-3.1.0-black?style=for-the-badge&logo=flask)
![MediaPipe](https://img.shields.io/badge/MediaPipe-0.10.20-orange?style=for-the-badge&logo=google)
![Gemini AI](https://img.shields.io/badge/Gemini_AI-Pro-blueviolet?style=for-the-badge&logo=google)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **FRIDAY** is a real-time, voice-activated AI assistant inspired by Tony Stark's **F.R.I.D.A.Y.** system.
> It combines a futuristic holographic web interface, gesture-based mouse control, voice commands, and Google's Gemini AI —
> all running locally on your machine.

</div>

---

<div align="center">
  <video src="0122.mp4" width="100%" autoplay loop muted playsinline controls></video>
  <br>
  <em>(If the preview video doesn't load above, you can find it as <code>0122.mp4</code> in the repository root).</em>
</div>

---

## 📌 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Project Workflow](#-project-workflow)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Pages & Screens](#-pages--screens)
- [Voice Commands](#-voice-commands)
- [Gesture Controls](#-gesture-controls)
- [Tech Stack](#-tech-stack)
- [Installation & Setup](#-installation--setup)
- [Configuration](#-configuration)
- [How to Run](#-how-to-run)
- [Demo](#-demo)
- [Future Ideas](#-future-ideas)
- [License](#-license)

---

## 🚀 About the Project

**FRIDAY AI Assistant** is a passion project built to bridge the gap between science fiction and reality. If you've ever watched Iron Man and wanted your own personal AI assistant like J.A.R.V.I.S or F.R.I.D.A.Y., this project acts as a functional prototype of that exact dream.

The name **"FRIDAY"** pays direct homage to Tony Stark's secondary AI interface, standing for *Female Replacement Intelligent Digital Assistant Youth*, and symbolizes cutting-edge tech acting as your ultimate digital toolset.

At its core, FRIDAY operates dynamically across three distinct domains in real-time:
1. **The Brain:** Powered by the advanced **Google Gemini Pro AI**, it understands natural language queries and speaks back to you conversationally via local Text-to-Speech (gTTS).
2. **The Sight:** Leveraging your webcam and **MediaPipe Computer Vision**, FRIDAY tracks 21 distinct hand landmarks globally. Instead of a standard mouse, hand gestures trigger Left Clicks, Right Clicks, and smooth screen navigation. 
3. **The Interface:** A responsive **Flask web server** hosts a stylized frontend UI featuring animated Iron Man dashboards, live dynamic web particles acting as holographic cursors, and functional sub-interfaces like the Mark 42 suit-up experience.

Whether you're looking to query an LLM entirely hands-free, command YouTube media effortlessly, quickly verify live weather/news data, or simply show off a highly interactive, futuristic computer UI to friends—FRIDAY delivers a deeply immersive sci-fi developer experience.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎙️ **Voice Activation** | Wake-word `"Friday"` activates the assistant |
| 🤖 **Gemini AI Brain** | Powered by Google Gemini Pro for intelligent answers |
| 🗣️ **Text-to-Speech** | Responds with a natural voice using gTTS |
| 🌐 **Flask Web Interface** | Multi-page holographic browser UI |
| 💠 **Holomat Interface** | Interactive sci-fi holographic panel with particle effects |
| 🤚 **Gesture Mouse Control** | Control your PC mouse with hand gestures via webcam |
| 🦾 **Mark 42 Suit Assembly** | Animated Iron Man suit assembly experience |
| 📰 **Live News Feed** | Top headlines fetched from NewsAPI |
| 🌤️ **Weather Widget** | Real-time weather data from OpenWeatherMap |
| 🎵 **YouTube Integration** | Play any song/video on YouTube by voice |
| 🎧 **Spotify Integration** | Open Spotify by voice command |
| ⏱️ **Real-Time Clock** | Tells you the current time on request |
| ⛔ **Interrupt Control** | Press `Q` to stop Friday mid-response |

---

## 🔄 Project Workflow

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER INTERACTION                         │
└────────────────────────────┬────────────────────────────────────┘
                             │
              ┌──────────────▼──────────────┐
              │   Microphone Input (Speech) │
              └──────────────┬──────────────┘
                             │
              ┌──────────────▼──────────────┐
              │  Speech Recognition (Google) │
              │  Detects wake-word "FRIDAY"  │
              └──────────────┬──────────────┘
                             │
         ┌───────────────────▼───────────────────┐
         │         Intent Classification          │
         │  (Time / Holomat / YouTube / Spotify / │
         │   Suit Assembly / AI Query / etc.)      │
         └───────────────────┬───────────────────┘
                             │
     ┌───────────────────────┼────────────────────────┐
     │                       │                        │
     ▼                       ▼                        ▼
┌──────────┐       ┌──────────────────┐      ┌──────────────────┐
│ Built-in │       │  Google Gemini   │      │  Web Browser /   │
│ Handlers │       │  AI (Pro Model)  │      │  Flask Routes    │
│ (Time,   │       │  (Open queries)  │      │  (Holomat, Suit, │
│  Weather,│       └────────┬─────────┘      │   YouTube, etc.) │
│  Music)  │                │                └──────────────────┘
└──────────┘       ┌────────▼─────────┐
                   │  gTTS + pydub    │
                   │  (Voice Response)│
                   └──────────────────┘

           ┌─────────────────────────────────┐
           │   PARALLEL: Gesture Control     │
           │  Webcam → MediaPipe → Mouse     │
           │  (Left Click / Right Click /    │
           │   Cursor Movement by Hand)      │
           └─────────────────────────────────┘
```

---

## 🏗️ System Architecture

```
FRIDAY_AI/
│
├── 🧠 Core AI Engine (friday.py)
│    ├── Wake-word detection via SpeechRecognition
│    ├── Intent routing (time, media, AI, navigation)
│    ├── Gemini Pro API (streaming response)
│    └── gTTS voice synthesis + interrupt support
│
├── 🌐 Web Server (Flask)
│    ├── / → FRIDAY Home Dashboard
│    ├── /hm → Holomat Interface
│    ├── /sa → Mark 42 Suit Assembly
│    └── /get_site_choice → Voice-driven page redirect
│
├── 🤚 Gesture Engine (gesture_control.py)
│    ├── MediaPipe hand landmark detection
│    ├── Finger angle calculation
│    ├── Left click / Right click gestures
│    └── Smooth cursor movement via pynput
│
└── 🎨 Frontend (templates/ + static/)
     ├── Iron Man themed UI (Orbitron font, dark sci-fi style)
     ├── Particle cursor effects (Three.js)
     ├── Draggable holographic elements
     ├── Live weather + news widgets
     └── Suit assembly animation experience
```

---

## 📁 Project Structure

```
Hologram_table_ft_FRIDAY/
│
├── friday.py               # 🧠 Main AI assistant + Flask server
├── gesture_control.py      # 🤚 Hand gesture mouse control
├── util.py                 # 🔧 Geometry utility functions
├── requirements.txt        # 📦 All Python dependencies
│
├── templates/
│   ├── index.html          # 🏠 Main FRIDAY dashboard
│   ├── hm.html             # 💠 Holographic Holomat interface
│   ├── test.html           # 🦾 Mark 42 Suit Assembly page
│   └── yt_t.html           # 🎵 YouTube playback helper
│
├── static/
│   ├── styles.css          # 🎨 Main dashboard styles
│   ├── stylehm.css         # 🎨 Holomat styles
│   ├── scripthm.js         # ⚙️ Holomat drag logic
│   ├── jarvis_2.gif        # 🌀 Iron Man left animation
│   ├── suit_animation.gif  # 🌀 Suit animation
│   ├── friday_icon2.png    # 🔵 FRIDAY AI icon
│   ├── image*.gif/png      # 🖼️ Holographic panel elements
│   └── [sound assets]      # 🔊 Assembly audio effects
│
└── suit_assemble/
    ├── test.html           # 🦾 Suit assembly animation HTML
    ├── mark_42.png         # Iron Man Mark 42 image
    ├── helmet.png          # Helmet piece
    ├── chest_piece.png     # Chest piece
    ├── suit.png            # Full suit image
    ├── final-repulse.gif   # Repulsor charge animation
    ├── snap.mp3            # Snap sound effect
    └── assembly_complete.mp3 # Assembly complete audio
```

---

## 🖥️ Pages & Screens

### 1. 🏠 FRIDAY Home Dashboard (`/`)
The main landing page of the FRIDAY AI. Features:
- Iron Man GIF animations on left and right panels
- FRIDAY AI logo (clickable mic icon)
- **Live Weather Widget** — current temperature, humidity, wind speed
- **Live News Feed** — Top 5 global headlines
- Voice-command driven page navigation

### 2. 💠 Holomat Interface (`/hm`)
A sci-fi holographic control panel. Features:
- Animated holographic data orbs (draggable GIFs)
- **Three.js particle cursor** — particles follow your mouse
- Futuristic dark theme with glowing blue particles
- Click FRIDAY icon to return to home
- Accessible by voice: *"Friday, open holomat"*

### 3. 🦾 Mark 42 Suit Assembly (`/sa`)
An Iron Man suit assembly animation experience. Features:
- Piece-by-piece suit assembly animation (helmet, chest, full suit)
- Sound effects on assembly completion
- Accessible by voice: *"Friday, assemble suit"*

---

## 🎙️ Voice Commands

All commands must start with the wake-word **"Friday"**:

| Voice Command | Action |
|---|---|
| `"Friday hello"` | Greeting response |
| `"Friday what is the time"` | Speaks the current time |
| `"Friday open holomat"` | Opens the Holomat interface |
| `"Friday open youtube"` | Opens YouTube browser |
| `"Friday open spotify"` | Opens Spotify browser |
| `"Friday play the song [name]"` | Plays song on YouTube |
| `"Friday assemble suit"` | Opens Mark 42 assembly page |
| `"Friday open mark 42 project"` | Opens assembly page |
| `"Friday go back"` | Navigates to home page |
| `"Friday [any question]"` | Answered by Gemini AI |

> 💡 Press **`Q`** on your keyboard at any time to interrupt Friday's response.

---

## 🤚 Gesture Controls

Run `gesture_control.py` separately alongside the main app.

| Gesture | Action |
|---|---|
| ✊ All fingers curled (index bent, middle & ring curled) | **Left Click** |
| 👆 Index finger extended, middle & ring curled | **Right Click** |
| 🖐️ Open hand / move wrist | **Move Mouse Cursor** |

- Uses **MediaPipe** hand tracking at 70%+ confidence
- Smooth cursor movement with configurable multipliers
- 1-second click cooldown to prevent accidental double clicks

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **AI Brain** | Google Gemini Pro API |
| **Speech-to-Text** | SpeechRecognition + Google Speech API |
| **Text-to-Speech** | gTTS (Google Text-to-Speech) + pydub |
| **Web Framework** | Flask 3.1.0 |
| **Hand Tracking** | MediaPipe 0.10.20 |
| **Computer Vision** | OpenCV 4.10 |
| **Mouse Control** | pynput + pyautogui |
| **Frontend FX** | Three.js (particle cursor) |
| **Weather API** | OpenWeatherMap API |
| **News API** | NewsAPI.org |
| **Media Playback** | pywhatkit (YouTube) |
| **Fonts** | Google Fonts — Orbitron |

---

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.8 or higher
- A working **microphone**
- A working **webcam** (for gesture control)
- Internet connection (for AI, weather, and news)

### Step 1: Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/FRIDAY_AI.git
cd FRIDAY_AI
```

### Step 2: Create a Virtual Environment (Recommended)
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

> ⚠️ **Note:** If `pydub` audio playback fails on Windows, install `ffmpeg` and add it to your system PATH.

---

## 🔑 Configuration

Open `friday.py` and replace the placeholder API key:

```python
# Line 97 — Replace with your real Gemini API key
GOOGLE_API_KEY = '<<<<<<YOUR API KEY>>>>>>>'
```

**Get your free Gemini API Key:** [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)

Open `templates/index.html` and optionally update:
```javascript
// Line 66 — Change city for weather
const city = "your_city_name";

// Line 67 — Replace with your OpenWeatherMap API key
const apiKey = "YOUR_OPENWEATHERMAP_KEY";
```

**Get Weather API Key:** [https://openweathermap.org/api](https://openweathermap.org/api)

---

## ▶️ How to Run

### Run the Main FRIDAY Assistant
```bash
python friday.py
```
Then open your browser at: **[http://127.0.0.1:5000](http://127.0.0.1:5000)**

### Run Gesture Control (Optional — Separate Window)
```bash
python gesture_control.py
```

> Both can run simultaneously. FRIDAY handles voice + web, while gesture_control handles mouse.

---

## 🎬 Demo

*(You can watch the full system in action in the auto-playing video at the top of this page!)*

Core working flow:
1. Run `python friday.py`
2. Browser opens the FRIDAY dashboard automatically
3. Say **"Friday, open holomat"** → holographic panel opens
4. Say **"Friday, what is the time"** → Friday speaks the time
5. Say **"Friday, play the song Believer"** → YouTube plays
6. Say **"Friday, assemble suit"** → Iron Man Mark 42 assembles
7. Run gesture control → move your hand in front of the webcam to control the mouse

---

## 🔭 Future Ideas

- [ ] 🔐 Add secure API key management (`.env` file)
- [ ] 📷 Face recognition to identify the user before activating
- [ ] 🧩 Plugin system for expandable command modules
- [ ] 📱 Mobile-friendly holographic UI
- [ ] 🌍 Multi-language voice support
- [ ] 🎮 Integrate with smart home devices (IoT)
- [ ] 🖥️ Full-screen holographic projection table mode
- [ ] 🤖 Multi-turn conversation memory with Gemini
- [ ] 🧤 Two-hand gesture support (zoom, scroll, pinch)

---

## 🪪 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with ❤️ and a dream of being Tony Stark.**

*"Sometimes you gotta run before you can walk."* — Tony Stark

⭐ If you like this project, please **star** the repository!

</div>
