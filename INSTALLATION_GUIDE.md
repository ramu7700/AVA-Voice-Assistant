AVA Installation & Setup Guide

Complete step-by-step guide to get AVA running on your system.

---

Table of Contents

1. System Requirements
2. Installation Steps
3. Platform-Specific Instructions
4. API Configuration
5. Troubleshooting
6. Advanced Setup

---

System Requirements

Minimum Requirements
- OS: Windows 10/11, macOS 10.14+, Ubuntu 18.04+
- Python: 3.8 or higher
- RAM: 4GB minimum (8GB recommended)
- Storage: 500MB free space
- Microphone: Any USB or built-in microphone
- Internet: Required for API features

Recommended Requirements
- OS: Windows 11, macOS 13+, Ubuntu 22.04+
- Python: 3.10+
- RAM: 8GB or more
- Storage: 1GB free space
- Microphone: Good quality USB microphone
- Internet: Broadband connection

---

Installation Steps

Step 1: Install Python

Windows
1. Download Python from [python.org](https://www.python.org/downloads/)
2. Run installer and **CHECK** "Add Python to PATH"
3. Verify installation:
```bash
python --version
```

macOS
```bash
# Using Homebrew
brew install python@3.10
```

Linux
```bash
sudo apt update
sudo apt install python3.10 python3-pip python3-venv
```

Step 2: Clone Repository

```bash
git clone https://github.com/yourusername/ava-voice-assistant.git
cd ava-voice-assistant
```

Or download ZIP and extract.

Step 3: Create Virtual Environment

```bash
# Create virtual environment
python -m venv venv

# Activate it
# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

Step 4: Install Dependencies

```bash
# Upgrade pip first
pip install --upgrade pip

# Install requirements
pip install -r requirements.txt
```

Step 5: Install PyAudio (Critical!)

PyAudio is required for microphone input but can be tricky to install.

Windows
```bash
# Method 1: Using pipwin (Recommended)
pip install pipwin
pipwin install pyaudio

# Method 2: Download wheel file
# Go to: https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyaudio
# Download appropriate .whl file for your Python version
# Example for Python 3.10 64-bit:
pip install PyAudio‑0.2.13‑cp310‑cp310‑win_amd64.whl
```

macOS
```bash
# Install portaudio first
brew install portaudio

# Then install PyAudio
pip install pyaudio
```

Linux
```bash
# Install dependencies
sudo apt-get install python3-pyaudio portaudio19-dev

# Install PyAudio
pip install pyaudio
```

---

Platform-Specific Instructions

Windows Setup

1. Install Microsoft Visual C++ (if not already installed)
   - Download from Microsoft website
   - Required for some Python packages

2. Configure Microphone
   - Go to Settings → Privacy → Microphone
   - Allow apps to access microphone
   - Test microphone in Sound settings

3. Run AVA
```bash
python ava.py
```

macOS Setup

1. Grant Microphone Permission
   - System Preferences → Security & Privacy → Microphone
   - Allow Terminal/Python to access microphone

2. Install Xcode Command Line Tools (if needed)
```bash
xcode-select --install
```

3. Run AVA
```bash
python3 ava.py
```

Linux Setup

1. Install Audio Dependencies
```bash
sudo apt-get install python3-dev portaudio19-dev
sudo apt-get install alsa-utils pulseaudio
```

2. Test Microphone
```bash
arecord -l  # List recording devices
arecord -d 5 test.wav  # Record 5 seconds
aplay test.wav  # Play back
```

3. Run AVA
```bash
python3 ava.py
```

---

API Configuration

Required APIs

1. OpenWeatherMap (Weather)

1. Go to [OpenWeatherMap](https://openweathermap.org/api)
2. Sign up for free account
3. Get API key from dashboard
4. Add to `ava.py`:
```python
self.WEATHER_API_KEY = "your_api_key_here"
```

Free Tier: 60 calls/minute, 1M calls/month

2. NewsAPI (News)

1. Visit [NewsAPI](https://newsapi.org/)
2. Register for free account
3. Get API key
4. Add to `ava.py`:
```python
self.NEWS_API_KEY = "your_api_key_here"
```

Free Tier: 100 requests/day

3. OpenAI (Optional - GPT Features)

1. Go to [OpenAI Platform](https://platform.openai.com/)
2. Create account
3. Add payment method
4. Get API key
5. Add to `ava.py`:
```python
self.OPENAI_API_KEY = "your_api_key_here"
```

Pricing: Pay-as-you-go, ~$0.002 per 1K tokens

Using Environment Variables (Recommended)

Create a `.env` file:

```env
WEATHER_API_KEY=your_openweather_key
NEWS_API_KEY=your_newsapi_key
OPENAI_API_KEY=your_openai_key
```

Install python-dotenv:
```bash
pip install python-dotenv
```

Load in `ava.py`:
```python
from dotenv import load_dotenv
import os

load_dotenv()
self.WEATHER_API_KEY = os.getenv('WEATHER_API_KEY')
```

---

Troubleshooting

Common Issues

1. "ModuleNotFoundError: No module named 'pyaudio'"

**Solution:**
```bash
# Windows
pipwin install pyaudio

# macOS
brew install portaudio
pip install pyaudio

# Linux
sudo apt-get install python3-pyaudio
```

2. "Could not understand audio"

Solutions:
- Check microphone connection
- Reduce background noise
- Speak clearly and closer to microphone
- Adjust microphone sensitivity in system settings
- Try different microphone

3. "Connection Error" or "API timeout"

Solutions:
- Check internet connection
- Verify API keys are correct
- Check API rate limits
- Use VPN if API is blocked in your region

4. "pyttsx3 init error" on Linux

Solution:
```bash
sudo apt-get install espeak espeak-data libespeak-dev
pip install pyttsx3
```

5. Import Error: googletrans

Solution:
```bash
pip uninstall googletrans
pip install googletrans==4.0.0rc1
```

Permission Issues

Windows
Run Command Prompt as Administrator

macOS/Linux
```bash
sudo python3 ava.py
# Or change file permissions
chmod +x ava.py
```

Testing Components

Test microphone:
```python
import speech_recognition as sr
r = sr.Recognizer()
with sr.Microphone() as source:
    print("Say something!")
    audio = r.listen(source)
    print(r.recognize_google(audio))
```

Test TTS:
```python
import pyttsx3
engine = pyttsx3.init()
engine.say("Testing text to speech")
engine.runAndWait()
```

---

Advanced Setup

GUI Application

To run the desktop GUI:

```bash
python gui_desktop_app.py
```

Requirements:
- tkinter (usually comes with Python)
- Additional: `pip install pillow` for images

IoT Integration

For IoT features:

```bash
pip install paho-mqtt firebase-admin
```

Configure MQTT broker in `iot_integration.py`:
```python
self.mqtt_broker = "your_broker_address"
self.mqtt_port = 1883
```

Web Interface

To run web interface:

```bash
pip install flask flask-cors
python web_app.py
```

Access at: `http://localhost:5000`

Docker Deployment (Advanced)

Create `Dockerfile`:
```dockerfile
FROM python:3.10-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
CMD ["python", "ava.py"]
```

Build and run:
```bash
docker build -t ava-assistant .
docker run -it --device /dev/snd ava-assistant
```

---

Mobile App Setup

Using Kivy (Cross-platform)

```bash
pip install kivy
python mobile_app.py
```

Using Flutter

1. Install Flutter SDK
2. Navigate to `flutter_app` directory
3. Run:
```bash
flutter pub get
flutter run
```

---

Security Best Practices

1. Never commit API keys to GitHub
   - Use `.gitignore` for `.env` file
   - Use environment variables

2. Rotate API keys regularly
   - Change keys every 3-6 months
   - Use different keys for dev/prod

3. Limit API access
   - Set IP restrictions if available
   - Use read-only keys where possible

---

Performance Optimization

Reduce Latency
```python
# Adjust timeout values
audio = r.listen(source, timeout=3, phrase_time_limit=5)
```

Optimize Memory
```python
# Limit conversation history
self.conversation_memory = self.conversation_memory[-50:]
```

Cache Responses
```python
import functools

@functools.lru_cache(maxsize=100)
def get_weather(city):
    # Weather data cached for repeated requests
    pass
```

---

Next Steps

1. Complete basic setup
2. Test core features
3. Configure all API keys
4. Try GUI application
5. Explore IoT integration
6. Customize AVA's personality
7. Add custom commands
8. Build mobile app

---

Getting Help

- Email: kethireddyramachandrareddy7700@gmail.com

---

Installation Checklist

- Python 3.8+ installed
- Virtual environment created
- All dependencies installed
- PyAudio working
- Microphone detected
- API keys configured
- First successful voice command
- All features tested

---

Happy Building!

If you encounter any issues not covered here, please open an issue on GitHub.
