# ClipNest

### Your clipboard. Everywhere.

ClipNest is a lightweight, privacy-conscious clipboard manager designed to make clipboard history fast, simple, and beautiful.

The project starts with a **macOS-first clipboard experience inspired by the simplicity of Windows Clipboard History (`Win + V`)**, while the architecture is designed to expand to:

- macOS
- iPhone
- iPad
- Windows
- Android
- Linux

---

## ✨ What is ClipNest?

Copy something.

ClipNest remembers it.

Press the ClipNest shortcut.

Find what you copied earlier.

Select it.

Paste normally.

That's it.

```text
Copy
 ↓
ClipNest
 ↓
Clipboard History
 ↓
Search / Select
 ↓
Copy Again
 ↓
Paste
```

The goal is to make clipboard history feel like a small, natural part of the operating system rather than another complicated application.

---

# 🎯 Project Goals

ClipNest is being built around a few simple principles:

- **Fast**
- **Small**
- **Beautiful**
- **Private**
- **Offline-first**
- **Native where necessary**
- **Cross-platform by design**
- **Simple to maintain**

The core clipboard experience should never depend on an Internet connection.

Synchronization is an additional capability, not a requirement for basic clipboard functionality.

---

# 🖥️ Primary Target

## macOS

The first and highest-priority target is macOS.

The intended experience is similar in spirit to Windows Clipboard History:

```text
Global Shortcut
      ↓
ClipNest Popup
      ↓
Clipboard History
      ↓
Search
      ↓
Select
      ↓
Restore to System Clipboard
      ↓
Paste
```

The Mac application is intended to operate as a lightweight utility, potentially from the menu bar/background.

---

# 📱 Planned Platforms

| Platform | Status |
|---|---|
| macOS | 🚧 Primary |
| iPhone | 🗺️ Planned |
| iPad | 🗺️ Planned |
| Windows 10 | 🗺️ Planned |
| Windows 11 | 🗺️ Planned |
| Android Phone | 🗺️ Planned |
| Android Tablet | 🗺️ Planned |
| Linux X11 | 🗺️ Planned |
| Linux Wayland | 🗺️ Planned |

Platform support will depend on the actual APIs and security restrictions provided by each operating system.

---

# ✨ Planned Features

## Clipboard History

- Automatic clipboard capture
- Local history
- Search
- Pin/favorite
- Delete
- Clear history
- Copy previous item again
- Duplicate detection
- Configurable history size
- Automatic expiration

## Desktop

- Global keyboard shortcut
- Floating clipboard-history popup
- Keyboard navigation
- Mouse interaction
- Menu-bar integration
- Dark mode
- Light mode
- System appearance

## Privacy

- Local-first operation
- No unnecessary telemetry
- Clipboard content not sent to AI services
- Clipboard content not written into normal application logs
- Secure device authorization for synchronization

## Synchronization

Planned synchronization layers:

```text
Local
  ↓
Same Network
  ↓
Peer-to-Peer
  ↓
Optional Encrypted Internet Relay
```

Internet synchronization is intentionally optional.

---

# 🔐 Privacy

Clipboard history can contain extremely sensitive information.

For example:

- passwords
- OTP codes
- API keys
- access tokens
- private keys
- financial information
- confidential work data

ClipNest therefore treats clipboard content as sensitive data.

The project aims to:

- avoid logging clipboard contents
- avoid unnecessary external transmission
- protect synchronized data
- provide device authorization/revocation
- allow users to control history retention
- operate normally without cloud connectivity

Platform-specific privacy restrictions will always take precedence over product assumptions.

---

# 📴 Offline First

ClipNest is designed to remain useful without Internet access.

The following core functionality should work offline:

- Clipboard capture
- Clipboard history
- Search
- Pinning
- Deletion
- Clearing
- Copy-again
- Local storage
- Settings

Network connectivity is only required for features that actually need communication with another device or service.

---

# 🧩 Architecture

The intended architecture separates shared clipboard logic from platform-specific implementations.

Conceptually:

```text
                  ClipNest
                     │
              ┌──────┴──────┐
              │ Shared Core │
              └──────┬──────┘
                     │
       ┌─────────────┼─────────────┐
       │             │             │
   Clipboard      Storage         Sync
       │             │             │
       └─────────────┼─────────────┘
                     │
            Platform Adapters
                     │
       ┌─────────────┼──────────────┐
       │             │              │
     macOS        Windows      Mobile/Linux
```

The actual technology stack will be selected after evaluating real platform requirements.

---

# 🛠️ Technology

The final technology stack has not been permanently selected at the initial specification stage.

Potential technologies may include:

- Swift / SwiftUI
- Flutter
- .NET MAUI
- Tauri
- Kotlin Multiplatform
- other suitable technologies

The final decision will be based on:

- native clipboard API access
- global shortcut support
- background behavior
- mobile restrictions
- Windows support
- Linux support
- packaging
- performance
- maintainability

The decision will be documented in:

**`MASTER-SPECIFICATION.md`**

---

# 📂 Repository Structure

The project is expected to contain documentation such as:

```text
ClipNest/
│
├── README.md
├── MASTER-SPECIFICATION.md
├── ROADMAP.md
├── guide.md
├── release-notes.md
├── ai-handover.md
│
├── src/
├── tests/
├── assets/
├── scripts/
└── ...
```

The exact source structure will be determined by the selected technology.

---

# 🚀 Getting Started

> These instructions will be updated once the implementation technology and build system are finalized.

## Clone

```bash
git clone <repository-url>
cd ClipNest
```

## Inspect the project

```bash
git status
git log --oneline --all
```

## Read the specification

Before contributing:

```text
MASTER-SPECIFICATION.md
ROADMAP.md
```

should be read first.

---

# 🧪 Testing

The project will contain tests covering areas such as:

- clipboard history
- storage
- search
- deduplication
- pinning
- deletion
- expiration
- synchronization
- platform integration

Tests should be executed before marking a milestone complete.

A build or test must never be described as successful unless it was actually executed.

---

# 📦 Distribution

Planned distribution artifacts include:

### macOS

```text
.app
.dmg
.pkg
```

### Windows

```text
.exe
Installer
```

### Linux

```text
.AppImage
.deb
.rpm
```

### Android

```text
.apk
.aab
```

### iOS/iPadOS

```text
Development build
IPA / TestFlight / App Store workflow
```

Apple and other platform signing requirements will be documented separately.

Unsigned builds may be produced where production signing credentials are unavailable.

---

# 🔄 Synchronization

Synchronization is deliberately separated from the local clipboard experience.

A user should be able to run:

```text
ClipNest on Mac
```

with synchronization disabled and still have a complete clipboard-history utility.

Future synchronization may support:

```text
Mac
 ↕
LAN
 ↕
iPhone
```

and eventually:

```text
Mac
 ↕
Internet / Secure Relay
 ↕
Windows / Android / iPad
```

Any Internet synchronization must be designed with privacy and encryption as core requirements.

---

# ⌨️ User Experience

## Desktop

The target interaction is:

```text
Copy something
       ↓
Global ClipNest Shortcut
       ↓
Clipboard Popup
       ↓
Search / Navigate
       ↓
Select
       ↓
Clipboard Restored
       ↓
Paste
```

## Mobile

Mobile platforms do not provide a universal `Win + V` equivalent.

The intended mobile experience is:

```text
Open ClipNest
       ↓
Clipboard History
       ↓
Search
       ↓
Select
       ↓
Copy Again
```

Platform-specific features such as widgets, Share Sheets, Quick Settings, App Shortcuts, and hardware-keyboard shortcuts will be investigated where available.

---

# 🗺️ Roadmap

The current development priority is:

```text
1. macOS MVP
        ↓
2. macOS Polish
        ↓
3. Testing
        ↓
4. Packaging
        ↓
5. Local Network Sync
        ↓
6. iPhone / iPad
        ↓
7. Windows
        ↓
8. Android
        ↓
9. Linux
        ↓
10. Optional Internet Sync
```

See:

**`ROADMAP.md`**

for the detailed implementation plan.

---

# 🤖 AI-Assisted Development

ClipNest is designed so that future AI coding agents can continue development without requiring the original conversation.

The permanent project context is stored in:

```text
MASTER-SPECIFICATION.md
ROADMAP.md
release-notes.md
ai-handover.md
```

The AI handover document records:

- current state
- completed work
- unfinished work
- bugs
- root causes
- fixes
- trade-offs
- exact next steps

---

# 📜 Git Standards

All project commits must use:

```text
MD IKRAMUL ISLAM SIDDIQUE POROSH
poroshScientist@outlook.com
```

Commit messages should describe the actual engineering change.

Examples:

```text
feat(core): define clipboard domain

feat(macOS): implement clipboard monitoring

feat(ui): add clipboard history popup

fix(macOS): prevent duplicate clipboard events

test(core): add clipboard history coverage

docs: add distribution guide
```

AI tools must not appear as the Git author identity.

---

# 🔒 Git Safety

The project should not automatically push to a remote repository.

Unless explicitly authorized:

- no `git push`
- no force push
- no history rewriting
- no remote branch deletion

Local commits are expected.

---

# 📦 Project Archive

The intended primary project archive is:

```text
ClipNest-with-git-history.zip
```

It should contain the complete `.git` directory so the project's local Git history survives extraction.

After extraction:

```bash
git log --oneline --all
```

should display the project's commit history.

A source-only archive may additionally be created:

```text
ClipNest-source.zip
```

---

# 🧭 Project Documentation

| File | Purpose |
|---|---|
| `README.md` | Public project overview |
| `MASTER-SPECIFICATION.md` | Permanent technical/product source of truth |
| `ROADMAP.md` | Development roadmap |
| `guide.md` | Build, run, use and distribution guide |
| `release-notes.md` | Version/release history |
| `ai-handover.md` | Continuity document for future AI agents |

---

# 📌 Current Status

**Project:** ClipNest

**Version:** 0.1.0

**Status:** Pre-MVP

**Primary target:** macOS

**Current implementation:** Not started

**Repository:** Initialized

**Next milestone:** macOS architecture and MVP implementation

---

# ❤️ Philosophy

ClipNest should not try to be everything.

It should do one small thing exceptionally well:

> **Remember what you copied, help you find it, and let you use it again.**

Fast enough to disappear.

Simple enough to trust.

Beautiful enough to enjoy.

---

## License

License information will be added when the project licensing decision is finalized.

---

**ClipNest — Your clipboard. Everywhere.**