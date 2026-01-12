# PC Remote Control - Developer Documentation

> Comprehensive documentation for developers working on PC Remote Control.

**Version:** 0.1.0 | **Last Updated:** 2026-01-12

---

## Table of Contents

- [Architecture Overview](#architecture-overview)
- [Project Structure](#project-structure)
- [API Routes](#api-routes)
- [Environment Variables](#environment-variables)
- [Configuration](#configuration)
- [Testing](#testing)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

---

## Architecture Overview

PC Remote Control follows a **Client-Server** architecture:

```
┌──────────────────────────────────────────────────────────────┐
│                        Smartphone Browser                     │
│              (Frontend: HTML5/CSS3/Vanilla JS)               │
└──────────────────────────────────────────────────────────────┘
                              │
                    HTTP REST Requests (Fetch)
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                         FastAPI Server                        │
│              (Backend: Python/Uvicorn/PyAutoGUI)              │
└──────────────────────────────────────────────────────────────┘
                              │
                    Simulated Keypresses / OS Commands
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                        Machine OS (PC)                       │
│              (Hardware Control / System Actions)             │
└──────────────────────────────────────────────────────────────┘
```

### Key Design Decisions

| Decision | Rationale |
|----------|-----------|
| **FastAPI** | High performance and ease of use for building RESTful APIs in Python. |
| **PyAutoGUI** | Cross-platform support for simulating media keys and keyboard actions. |
| **Vanilla JS** | Minimizes overhead and ensures the frontend is fast and responsive on mobile devices without complex build steps. |
| **uv** | Provides extremely fast dependency resolution and environment management. |

---

## Project Structure

```
pc-rc/
├── assets/               # Project images and logo
├── screenshots/          # Saved remote screenshots
├── main.py               # Backend API and server logic
├── index.html            # Frontend remote interface
├── pyproject.toml        # Dependencies and build config
├── uv.lock               # Dependency lockfile
├── .env                  # Environment configuration (ignored)
├── DEVELOPMENT.md        # This file
├── CHANGELOG.md          # Version history
├── LICENSE.md            # License terms
└── README.md             # User-facing documentation
```

---

## API Routes

### System Controls

| Method | Path | Handler | Description |
|--------|------|---------|-------------|
| POST | `/system/lock` | `system_power_control` | Locks the workstation. |
| POST | `/system/sleep` | `system_power_control` | Puts the system to sleep. |
| POST | `/system/reboot` | `system_power_control` | Restarts the PC. |
| POST | `/system/shutdown` | `system_power_control` | Powers off the PC. |

### Media Controls

| Method | Path | Handler | Description |
|--------|------|---------|-------------|
| POST | `/media/playpause` | `media_control` | Toggles play/pause state. |
| POST | `/media/nexttrack` | `media_control` | Skips to the next track. |
| POST | `/media/prevtrack` | `media_control` | Goes to the previous track. |
| POST | `/media/volumeup` | `media_control` | Increases system volume. |
| POST | `/media/volumedown` | `media_control` | Decreases system volume. |
| POST | `/media/volumemute` | `media_control` | Mutes/unmutes audio. |

### Utilities

| Method | Path | Handler | Description |
|--------|------|---------|-------------|
| GET | `/action/screenshot` | `get_screenshot` | Captures and returns a PNG screenshot. |
| POST | `/app/browser` | `open_browser` | Opens the default web browser on the PC. |

---

## Environment Variables

### Optional

| Variable | Description | Default |
|----------|-------------|---------|
| `HOST` | IP address to bind the server to. | `0.0.0.0` |
| `PORT` | Port number to run the server on. | `8000` |

---

## Configuration

The application uses `python-dotenv` to load configurations from a `.env` file if present.

---

## Testing

### Running the application

```bash
uv run main.py
```

Manual verification is the primary method for testing as the application interacts with hardware and OS-level commands that are difficult to mock effectively in a CI environment.

---

## Troubleshooting

### Common Issues

| Issue | Solution |
|-------|----------|
| **Connection Refused** | Ensure the phone is on the same Wi-Fi. Check if the PC firewall allows port 8000. |
| **Media Keys not working** | Ensure the media player is focusable or supports global media keys. |
| **Screenshot fails** | Ensure the application has permission to record the screen on your OS. |

---

## Contributing

### Pull Request Process

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test thoroughly on your target OS
5. Commit with clear messages
6. Push and create a Pull Request

---

<p align="center">
  <a href="README.md">← Back to README</a>
</p>
