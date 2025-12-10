Quick Start Guide - Get AVA Running in 5 Minutes

The fastest way to get AVA up and running!

---

Prerequisites

Before you start, make sure you have:
- Python 3.8+ installed
- A working microphone
- Internet connection
- 10 minutes of your time

---

Installation (Choose Your OS)

Windows

```bash
# 1. Clone repository
git clone https://github.com/yourusername/ava-voice-assistant.git
cd ava-voice-assistant

# 2. Create virtual environment
python -m venv venv
venv\Scripts\activate

# 3. Install dependencies
pip install --upgrade pip
pip install pipwin
pipwin install pyaudio
pip install -r requirements.txt

# 4. Run AVA!
python ava.py
```

macOS

```bash
# 1. Clone repository
git clone https://github.com/yourusername/ava-voice-assistant.git
cd ava-voice-assistant

# 2. Install audio dependencies
brew install portaudio

# 3. Create virtual environment
python3 -m venv venv
source venv/bin/activate

# 4. Install dependencies
pip install --upgrade pip
pip install -r requirements.txt

# 5. Run AVA!
python3 ava.py
```

Linux (Ubuntu/Debian)

```bash
# 1. Install system dependencies
sudo apt-get update
sudo apt-get install python3-pyaudio portaudio19-dev python3-pip

# 2. Clone repository
git clone https://github.com/yourusername/ava-voice-assistant.git
cd ava-voice-assistant

# 3. Create virtual environment
python3 -m venv venv
source venv/bin/activate

# 4. Install dependencies
pip install --upgrade pip
pip install -r requirements.txt

# 5. Run AVA!
python3 ava.py
```

---

First Steps

1. Start AVA

Once running, you'll see:
```
🎙️ AVA initialized successfully!
AVA: Good morning User! I'm AVA, your personal assistant. How can I help you today?
AVA: Listening for 'Hey AVA'
🎧 Listening...
```

2. Activate AVA

Say: "Hey AVA"

You'll hear: "Yes, I'm listening"

3. Try Your First Commands

Try these to test AVA:

```
"What's the time?"
"What's the date?"
"Tell me a joke"
"Open YouTube"
"Search Google for Python tutorials"
```

---

Essential Commands

  Information
| Command | What it does |
|---------|--------------|
| "What's the time?" | Tells current time |
| "What's the date?" | Tells current date |
| "What's the weather?" | Gets weather info |
| "Tell me the news" | Latest headlines |

System Control
| Command | What it does |
|---------|--------------|
| "Open Chrome" | Opens Chrome browser |
| "Open YouTube" | Opens YouTube |
| "Open Calculator" | Opens calculator |
| "Increase volume" | Raises volume |

Productivity
| Command | What it does |
|---------|--------------|
| "Add reminder: buy milk" | Creates reminder |
| "Add task: finish report" | Adds to todo |
| "Show my todo list" | Shows tasks |

Search & Entertainment
| Command | What it does |
|---------|--------------|
| "Search Google for [topic]" | Google search |
| "YouTube search [topic]" | YouTube search |
| "Play [song name]" | Plays music |
| "Tell me a joke" | Random joke |
| "Wikipedia [topic]" | Wiki summary |

Exit
| Command | What it does |
|---------|--------------|
| "Stop" or "Exit" | Quits AVA |

---

Quick Configuration

Set Your Name & Location

Edit `ava_preferences.json` (created after first run):

```json
{
  "name": "Your Name",
  "location": "Your City",
  "favorite_music": [],
  "reminders": [],
  "todo_list": []
}
```

Add API Keys (Optional but Recommended)

For weather and news features, get free API keys:

1. Weather: [OpenWeatherMap](https://openweathermap.org/api) (Free)
2. News: [NewsAPI](https://newsapi.org/) (Free)

Add to `ava.py` line 26-27:
```python
self.WEATHER_API_KEY = "your_key_here"
self.NEWS_API_KEY = "your_key_here"
```

Without keys, these features won't work, but everything else will!

---

Quick Troubleshooting

Problem: "No module named 'pyaudio'"

Windows:
```bash
pip install pipwin
pipwin install pyaudio
```

Mac:
```bash
brew install portaudio
pip install pyaudio
```

Linux:
```bash
sudo apt-get install python3-pyaudio
```

Problem: "Could not understand audio"

- Speak clearly and closer to mic
- Reduce background noise
- Check microphone in system settings
- Try: "Hey AVA" louder and clearer

Problem: AVA not responding

- Check internet connection
- Restart AVA
- Verify microphone permissions

---

Try the GUI Version

For a graphical interface:

```bash
python gui_desktop_app.py
```

Features:
- Visual conversation history
- Quick action buttons
- Manual text input
- Status indicators

---

Command Examples by Category

Web & Search
```
"Hey AVA, search Google for best pizza recipe"
"Hey AVA, YouTube search funny cat videos"
"Hey AVA, open WhatsApp"
```

Information
```
"Hey AVA, what's the weather in London?"
"Hey AVA, tell me about Elon Musk on Wikipedia"
"Hey AVA, what's 25 times 4?"
```

Entertainment
```
"Hey AVA, play Imagine Dragons"
"Hey AVA, tell me a joke"
"Hey AVA, search YouTube for movie trailers"
```

Productivity
```
"Hey AVA, add reminder call mom tomorrow"
"Hey AVA, add task submit assignment"
"Hey AVA, show my todo list"
```

Translation
```
"Hey AVA, translate to Hindi"
[AVA asks what to translate]
"Hello, how are you?"
```

---

Next Level

Once comfortable with basics:

1. Customize Personality
   - Edit responses in `ava.py`
   - Change voice settings

2. Add Custom Commands
   - Modify `process_command()` function
   - Add your own functions

3. Try Advanced Features
   - IoT integration
   - GPT conversation mode
   - Mobile app

4. Contribute
   - Report bugs
   - Suggest features
   - Submit PRs

---

Pro Tips

1. Speak naturally - AVA understands conversational language
2. Wait for response - Give AVA time to process
3. Be specific - "Play Bohemian Rhapsody" vs "Play song"
4. Save common tasks - Use reminders and todos
5. Explore features - Try different commands!

---

You're Ready!

AVA is now set up and ready to assist you. Here's a sample conversation:

```
You: "Hey AVA"
AVA: "Yes, I'm listening"

You: "What's the time?"
AVA: "The time is 3:45 PM"

You: "Tell me a joke"
AVA: "Why don't scientists trust atoms? Because they make up everything!"

You: "Open YouTube"
AVA: "Opening YouTube"

You: "Thanks AVA!"
AVA: "You're welcome! Anything else I can help with?"

You: "Stop"
AVA: "Goodbye! Have a great day!"
```

---

Need Help?

- Email: kethireddyramachandrareddy7700@gmail.com

---

Enjoy using AVA! 
