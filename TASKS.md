# PC Remote Control - Tasks

> **Project:** PC Remote Control  
> **Version:** 0.1.0  
> **Last Updated:** 2026-01-12

---

## ✅ Completed (v0.1.0)

### Backend
- [x] Initial FastAPI server setup.
- [x] Media control logic using PyAutoGUI.
- [x] System power controls (Shutdown, Reboot, Sleep, Lock).
- [x] Screenshot capture utility using MSS.
- [x] Local IP discovery helper.

### Frontend
- [x] Modern dark-themed UI.
- [x] Responsive layout for mobile devices.
- [x] AJAX-based command execution (Fetch API).
- [x] Confirmation dialogs for destructive actions (Reboot, Shutdown).

### Documentation
- [x] Comprehensive README with centered logo and tech stack.
- [x] Developer guide (DEVELOPMENT.md).
- [x] Change history (CHANGELOG.md).
- [x] Tremors Source License (LICENSE.md).

---

## 🚧 In Progress

### Backend
- [/] refining cross-platform support for Linux/macOS.

---

## 📋 To Do

### High Priority
- [ ] **Authentication**: Add a simple PIN or password protection for the web UI.
- [ ] **Tray Icon**: Add a system tray icon for easy server management (Start/Stop/Quit).

### Medium Priority
- [ ] **Custom Macros**: Allow users to define custom commands in the web UI.
- [ ] **Wake-on-LAN Support**: Instructions or integrated helper for waking the PC.

### Low Priority
- [ ] **Dark Mode Toggle**: Although default is dark, a light mode option.
- [ ] **File Transfer**: Simple way to push files to/from the PC.

---

## 🐛 Bug Fixes

- [ ] **BUG-1:** Screenshot capture might fail on multi-monitor setups (MSS focus).
- [ ] **BUG-2:** Media keys might not work if no player is active or focusable.

---

## 💡 Ideas / Future

- Mobile app version (though web UI works great).
- Integration with Home Assistant or other IoT platforms.

---

## 🏗️ Architecture Notes

- Uses `mss` for the fastest possible screenshots.
- `pyautogui` is used for global media key injection.
- Security is currently handled by local network isolation (trusted network).

---
