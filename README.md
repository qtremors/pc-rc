# 🖥️ PC Remote Control

A simple yet powerful web API that runs on your PC, allowing you to control system functions, media playback, and applications directly from your phone's web browser.

## 🚀 Overview

This tool lets you use your phone as a remote control for your computer. It creates a simple website on your PC that you can open on your phone's browser to:

* **Media:** Play/Pause, Change Volume, Skip Tracks.
* **Power:** Shutdown, Reboot, Sleep, or Lock your PC.
* **Utility:** Open the browser or take a screenshot remotely.

**No app required.** It works on any phone (iPhone or Android) using the web browser.

---

## ✨ Current Features

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

---

## 🧠 Technology Stack

- Backend: Python with FastAPI for a fast and efficient API  
- System & Media Control: PyAutoGUI to simulate keyboard presses for universal media control  
- Screenshot: MSS for fast and cross-platform screen capturing  
- Frontend: A single, dependency-free HTML file with modern CSS for a responsive UI  

---


## ⚙️ How to Install & Run

### Step 1: Install Python
You need Python installed on your computer to run this.
* **Download Python here:** [python.org/downloads](https://www.python.org/downloads/)
* **Important during installation:** Check the box that says **"Add Python to PATH"** before clicking Install.

### Step 2: Open a Terminal
* **Windows:** Press the `Windows Key`, type `cmd`, and press Enter.
* **Mac/Linux:** Open the `Terminal` app.

### Step 3: Install the "uv" tool
We use a tool called `uv` to handle all the complex setup automatically. Type this into your terminal and press Enter:
```bash
pip install uv
````

### Step 4: Get this project

Copy and paste these commands into your terminal one by one:

```bash
git clone https://github.com/qtremors/pc-rc.git
cd pc-rc
```

_(If you don't have "git" installed, you can just download this project as a ZIP file, extract it, and open your terminal inside that folder instead.)_

### Step 5: Setup and Run

Run these two commands to start the remote:

1. **Setup the environment (do this once):**
    
    ```bash
    uv sync
    ```
    
    >Note: If you are starting from scratch without a lockfile, add the dependencies:_

    ```bash
    uv add fastapi uvicorn pyautogui mss python-dotenv
    ```

2. **Start the server:**
    
    ```bash
    uv run main.py
    ```
    

### Step 6: Connect your Phone

1. Look at the text in your terminal. It will show a URL like:
    
    > `http://192.168.1.15:8000`
    
2. Make sure your phone is connected to the **same Wi-Fi** as your computer.
    
3. Type that URL into your phone's web browser (Chrome, Safari, etc.).
    

You should now see the remote control interface!

---

## 🧭 Roadmap

The vision is to evolve this from a script into a robust service.

- [ ] **Phase 1: Background Service**
    
    - Convert to a systemd service (Linux) or Task Scheduler task (Windows) for auto-start on boot.
        
- [ ] **Phase 2: Native Android App**
    
    - [ ] Auto-discovery of server on local network.
        
    - [ ] Widgets for quick access.
        
- [ ] **Phase 3: Remote Access (Tailscale)**
    
    - Integrate Tailscale for secure control outside the local network.
        
- [ ] **Phase 4: Security**
    
    - Implement API Key/PIN authentication.
        
- [ ] **Phase 5: Extensibility**
    
    - Allow users to define custom shell scripts to run via the UI.

---

## ❓ Troubleshooting

- **"Command not found"**: This usually means Python wasn't added to your PATH during installation. Reinstall Python and make sure to check the "Add to PATH" box.
    
- **Phone won't connect**:
    
    - Check that your phone and PC are on the same Wi-Fi network.
        
    - Your computer's Firewall might be blocking the connection. Allow Python through your firewall if asked.