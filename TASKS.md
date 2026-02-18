# PC Remote Control - Tasks

> **Project:** PC Remote Control  
> **Version:** 0.1.0  
> **Last Updated:** 2026-01-14

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
- [/] Refining cross-platform support for Linux/macOS.

---

## 📋 To Do

### High Priority
- [ ] **Authentication**: Add a simple PIN or password protection for the web UI.
- [ ] **Tray Icon**: Add a system tray icon for easy server management (Start/Stop/Quit).
- [ ] **Screenshot Cleanup**: Screenshots accumulate indefinitely in `screenshots/` folder. Add cleanup on startup or a max-age policy.
- [ ] **Graceful Error Handling**: Frontend shows generic "Failed to connect" for all errors. Differentiate between network errors, server errors, and action failures.

### Medium Priority
- [ ] **Custom Macros**: Allow users to define custom commands in the web UI.
- [ ] **Wake-on-LAN Support**: Instructions or integrated helper for waking the PC.
- [ ] **Configurable Browser URL**: Currently hardcoded to `https://google.com`. Allow users to configure default URL.
- [ ] **Screenshot Quality Options**: Allow choosing between PNG (high quality) and JPEG (faster transfer).
- [ ] **Status Auto-Clear**: Clear status message after a few seconds instead of leaving it visible indefinitely.

### Low Priority
- [ ] **Dark Mode Toggle**: Although default is dark, a light mode option.
- [ ] **File Transfer**: Simple way to push files to/from the PC.
- [ ] **pyproject.toml Description**: Current description is placeholder "Add your description here".
- [ ] **API Versioning**: Add `/api/v1/` prefix for future compatibility.

---

## 🐛 Bug Fixes

### Critical
- [ ] **BUG-1:** Cross-platform sleep/lock logic is flawed. `os.name == 'posix'` is used for macOS-specific `pmset` command, but Linux also returns `'posix'`. The `else` branch for Linux will never execute. Should check `sys.platform` instead.

### High
- [ ] **BUG-2:** Screenshot capture might fail on multi-monitor setups (MSS defaults to primary).
- [ ] **BUG-3:** Media keys might not work if no player is active or focusable.
- [ ] **BUG-4:** Previous track button SVG icon is reversed (shows forward arrow with skip bar on left).
- [ ] **BUG-5:** Next track button SVG icon is malformed (shows skip bar in wrong position).

### Medium
- [ ] **BUG-6:** Screenshot endpoint lacks file cleanup. Old screenshots persist on disk, causing potential disk space issues.
- [ ] **BUG-7:** `get_local_ip()` uses UDP probe to `10.255.255.255` which may fail on some network configurations or VPNs.

---

## 🔧 Code Quality

### Refactoring Needed
- [ ] **REFACTOR-1:** System power control uses repetitive `if os.name` checks. Extract platform detection to a helper function.
- [ ] **REFACTOR-2:** Inline `os.system()` calls for system commands. Consider using `subprocess.run()` for better error handling and security.
- [ ] **REFACTOR-3:** Screenshot path construction inline in endpoint. Move to a utility function for reusability.

### Code Improvements
- [ ] **IMPROVE-1:** Add type hints to all functions for better IDE support and documentation.
- [ ] **IMPROVE-2:** Add request/response models using Pydantic for API documentation.
- [ ] **IMPROVE-3:** Consider async file I/O for screenshot operations to avoid blocking.

---

## 🌐 Cross-Platform Issues

- [ ] **PLATFORM-1:** Sleep command: Linux uses `systemctl suspend` but `pmset` (macOS) runs first due to `os.name == 'posix'` logic bug.
- [ ] **PLATFORM-2:** Lock command: Same issue - macOS `pmset displaysleepnow` runs instead of Linux `xdg-screensaver lock`.
- [ ] **PLATFORM-3:** macOS may require accessibility permissions for PyAutoGUI.
- [ ] **PLATFORM-4:** Linux media keys via PyAutoGUI require X11; Wayland support is limited.

---

## 📖 Documentation Gaps

- [ ] **DOC-1:** No `.env.example` file provided. Users won't know available environment variables without reading docs.
- [ ] **DOC-2:** Missing API error response documentation in DEVELOPMENT.md.
- [ ] **DOC-3:** No instructions for running as a system service or on startup.
- [ ] **DOC-4:** macOS/Linux specific setup (permissions, dependencies) not documented.
- [ ] **DOC-5:** Missing CONTRIBUTING.md as a standalone file (currently inline in DEVELOPMENT.md).

---

## 💡 Ideas / Future

- Mobile app version (though web UI works great).
- Integration with Home Assistant or other IoT platforms.
- WebSocket for real-time status updates instead of polling.
- Keyboard/mouse control for full remote desktop-lite experience.
- Screenshot streaming/live preview mode.

---

## 🏗️ Architecture Notes

- Uses `mss` for the fastest possible screenshots.
- `pyautogui` is used for global media key injection.
- Security is currently handled by local network isolation (trusted network).
- Frontend uses template injection (`{{API_BASE_URL}}`) for dynamic API URL.

---
