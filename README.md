# 🖥️ PC Remote Control API

A simple yet powerful web API that runs on your PC, allowing you to control system functions, media playback, and applications directly from your phone's web browser.

## 🚀 Overview

This project turns your phone into a wireless remote for your computer.  
It runs a lightweight Python server on your PC that listens for commands sent from a clean, modern web interface on your phone.  

Perfect for:
- Controlling media from the couch  
- Locking your PC from another room  
- Quickly launching applications  

## ✨ Current Features

The web interface provides a clean, responsive layout with the following controls grouped into logical sections:

### 🖥️ System Power
- Lock: Instantly lock your PC's screen  
- Sleep: Put your PC into sleep/suspend mode  
- Reboot: Safely restart your computer (with confirmation)  
- Shutdown: Power down your computer (with confirmation)  

### 🎵 Media Controls
- Volume Up / Down / Mute: Control the system volume  
- Play / Pause: Control media playback in the active application (e.g., Spotify, YouTube)  
- Previous / Next Track: Skip between tracks in your media player  

### 🛠️ Utilities & Applications
- Open Browser: Launches your default web browser  
- Take Screenshot: Captures your PC's screen and opens it in a new browser tab on your phone  

## 🧠 Technology Stack

- Backend: Python with FastAPI for a fast and efficient API  
- System & Media Control: PyAutoGUI to simulate keyboard presses for universal media control  
- Screenshot: MSS for fast and cross-platform screen capturing  
- Frontend: A single, dependency-free HTML file with modern CSS for a responsive UI  

## ⚙️ How to Run

Follow these steps to get the project running on your local network.

### 1. Clone the Repository
```bash
git clone https://github.com/qtremors/pc-rc
cd pc-rc
``` 

### 2. Set Up Virtual Environment
Create and activate a virtual environment using uv.  
```bash
uv sync
``` 

### 4. Create Environment File
Create a file named `.env` in the root of the project directory with the following content:  
```bash
HOST=0.0.0.0  
PORT=8000
``` 

### 5. Run the Server
Start the application with this command:  
```python
python main.py
```

The terminal will display the URL to open on your phone’s browser, for example:  
`http://192.111.1.10:8000` 

Your phone must be connected to the same Wi-Fi network as your PC.

## 🧭 Future Roadmap

This project is the foundation for a more robust and seamless remote control experience.  
The long-term vision is to evolve it from a simple web server into a polished, always-on application.

### Phase 1: Background Service
Convert the Python server into a background service that automatically starts when the PC boots up.  
This removes the need to manually run python main.py each time.

### Phase 2: Native Android Application
Develop a dedicated Android app to replace the web client.  
It will offer:  
- Automatic server discovery on the local network  
- A more fluid, native interface  
- The ability to save server addresses  
- Potential for widgets and notifications  

### Phase 3: Zero-Config Remote Access (Tailscale)
Integrate Tailscale to provide secure and effortless control from anywhere in the world.  
This creates a private overlay network between your phone and PC, removing the need for port forwarding and enhancing security.

### Phase 4: Enhanced Security
Implement a basic authentication layer (API key or simple PIN system) to prevent unauthorized access, even on a trusted local network.

### Phase 5: Extensibility
Add support for custom user-defined commands or scripts that can be triggered from the app.

## 💡 Inspiration

This project was inspired by the need for a minimalist, privacy-respecting alternative to commercial remote control tools.  
Everything runs locally — your commands never leave your network.

## 🧑‍💻 Author

Made with ❤️ by Tremors
