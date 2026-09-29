# ClipNest — Master Specification

> **Your clipboard. Everywhere.**

**Project:** ClipNest  
**Document:** Master Product & Technical Specification  
**Status:** Initial Specification  
**Version:** 0.1.0  
**Primary Target:** macOS  
**Future Targets:** iOS, iPadOS, Windows, Android, Linux  
**Repository:** ClipNest  
**Git Author:** MD IKRAMUL ISLAM SIDDIQUE POROSH  
**Git Email:** poroshScientist@outlook.com

---

# 1. Document Purpose

This document is the permanent source of truth for the ClipNest project.

It defines:

- product vision
- functional requirements
- UX requirements
- architecture
- platform strategy
- storage
- synchronization
- security
- testing
- packaging
- documentation
- Git conventions
- roadmap
- known limitations
- architectural decisions
- implementation status

Any future developer or AI coding agent should read this document before modifying the project.

A future agent must NOT assume that the original conversation is available.

The repository and this document must contain enough information to continue development independently.

---

# 2. Product Overview

ClipNest is a lightweight, privacy-conscious clipboard manager designed to provide a clipboard-history experience similar in spirit to Windows Clipboard History.

The first and most important target is macOS.

The core Mac experience is:

```text
Copy something
      ↓
ClipNest captures it
      ↓
Press ClipNest global shortcut
      ↓
Clipboard history popup appears
      ↓
Search/select previous item
      ↓
ClipNest restores it to system clipboard
      ↓
Paste normally
```

The application should feel:

- fast
- small
- polished
- native
- reliable
- private
- easy to understand

ClipNest is a utility application, not an enterprise platform.

---

# 3. Product Philosophy

The following principles govern the project.

## 3.1 Reliability First

A clipboard manager must work consistently.

A beautiful interface is useless if clipboard capture silently fails.

## 3.2 Local-First

Basic clipboard functionality must work without Internet connectivity.

## 3.3 Privacy First

Clipboard contents can contain highly sensitive information.

Clipboard data must never be unnecessarily exposed.

## 3.4 Native Where Necessary

Shared code is desirable, but platform-specific clipboard APIs must be used when required.

Never force a cross-platform abstraction to behave in a way that conflicts with the operating system.

## 3.5 Simple Architecture

Avoid unnecessary complexity.

Do not introduce:

- unnecessary microservices
- unnecessary backend infrastructure
- unnecessary abstraction layers
- unnecessary dependencies

## 3.6 Cross-Platform by Architecture

The first implementation is macOS-first.

However, the core architecture should allow future implementations for:

- iOS
- iPadOS
- Windows
- Android
- Linux

---

# 4. Product Name

## ClipNest

The name represents a small place where clipboard items are collected and kept available.

Primary tagline:

> Your clipboard. Everywhere.

The branding should be:

- professional
- modern
- friendly
- memorable
- minimal

Avoid childish or overly playful branding.

---

# 5. Target Platforms

## Phase 1

### macOS

Primary and highest-priority platform.

Target:

- Apple Silicon
- Intel Mac where practical

---

## Future Platforms

### Apple Mobile

- iPhone
- iPad

### Microsoft

- Windows 10
- Windows 11

### Android

- Android smartphones
- Android tablets

### Linux

- X11
- Wayland where practical

---

# 6. Core MVP

The first complete MVP should provide:

- automatic clipboard capture
- local clipboard history
- clipboard history popup
- global keyboard shortcut
- search
- copy previous item
- pin
- unpin
- delete
- clear history
- duplicate detection
- configurable history size
- automatic expiration
- light theme
- dark theme
- system theme
- keyboard navigation
- local/offline operation
- persistent local storage

---

# 7. macOS UX Specification

The macOS version is the reference UX for the product.

The application should preferably operate as a lightweight menu-bar/background utility.

## 7.1 Global Shortcut

ClipNest must provide a configurable global shortcut.

A candidate default is:

```text
Command + Shift + V
```

However, the implementation must verify that this does not create unacceptable conflicts with native macOS functionality.

The shortcut should be configurable.

---

## 7.2 Clipboard Popup

When the global shortcut is invoked, display a compact floating window.

Conceptually:

```text
┌─────────────────────────────────────┐
│ ClipNest                       ⚙    │
│                                     │
│ 🔍 Search clipboard...              │
├─────────────────────────────────────┤
│ Hello World                    2m   │
│ https://example.com             5m   │
│ Console.WriteLine("Hello");     8m   │
│ Meeting notes...               12m   │
└─────────────────────────────────────┘
```

The exact visual design is implementation-dependent.

The popup must:

- open quickly
- receive keyboard focus
- support keyboard navigation
- support mouse interaction
- support search
- clearly identify pinned items
- show useful timestamps
- show content type where appropriate
- restore selected content to the system clipboard

---

# 8. Clipboard Restoration

Selecting an existing history item must place that content into the operating system clipboard.

The expected workflow is:

```text
Select item
    ↓
Set system clipboard
    ↓
Close/minimize popup
    ↓
User pastes normally
```

ClipNest should not require users to manually copy the selected item again unless platform limitations require it.

---

# 9. Clipboard Content

MVP content types:

- plain text
- multiline text
- URLs
- numbers
- code
- ordinary textual content

Images should be supported if technically practical for the selected architecture.

Future content types may include:

- rich text
- files
- structured content

Do not allow future complexity to destabilize the text-based MVP.

---

# 10. Clipboard History

Each clipboard item should conceptually contain:

```text
id
contentType
content
createdAt
updatedAt
sourceDeviceId
sourceDeviceName
isPinned
size
contentHash
syncStatus
```

The final implementation may alter this model if there is a documented technical reason.

---

# 11. History Rules

ClipNest must support:

- configurable maximum history size
- automatic cleanup
- configurable expiration
- pinned items surviving normal cleanup
- duplicate detection
- manual deletion
- clear-all functionality

Duplicate behavior should be deterministic.

A repeated clipboard value should not unnecessarily create endless identical history entries.

---

# 12. Search

Clipboard search must be:

- fast
- local
- case-aware according to UX design
- useful for long histories

Search should work without network access.

For large histories, use appropriate indexing/search mechanisms rather than repeatedly scanning huge datasets on the UI thread.

---

# 13. Keyboard UX

Desktop users should be able to use ClipNest primarily from the keyboard.

At minimum support:

```text
Arrow Up
Arrow Down
Enter
Escape
```

Additional shortcuts may include:

```text
Delete
Pin
Copy
Search
```

Do not conflict unnecessarily with native operating-system shortcuts.

---

# 14. Offline-First Requirement

The core product must work completely offline.

The following MUST work without Internet:

- clipboard capture
- history
- search
- pin
- delete
- clear
- copy-again
- settings
- local storage

Internet connectivity must not be required for the core Mac experience.

---

# 15. Synchronization

Synchronization is a secondary capability.

It must not make local clipboard functionality dependent on the network.

Preferred architecture:

```text
Local clipboard
      ↓
Local history
      ↓
Optional synchronization
      ↓
Other authorized devices
```

Potential synchronization levels:

1. Same-device only
2. Same-LAN synchronization
3. Peer-to-peer synchronization
4. Optional encrypted Internet relay

The project should prefer simpler mechanisms where they satisfy the requirements.

---

# 16. LAN Synchronization

A future synchronization implementation should investigate local-network synchronization.

Example:

```text
MacBook
   ↕
Home Wi-Fi
   ↕
iPhone
```

or:

```text
MacBook
   ↕
Home Wi-Fi
   ↕
Windows PC
```

LAN presence alone must NOT be treated as authorization.

Devices should explicitly trust/authorize one another.

---

# 17. Internet Synchronization

Cloud synchronization is optional.

If implemented, it must use:

- secure authentication
- encrypted transport
- appropriate encryption at rest
- device authorization
- device revocation
- privacy-conscious storage

No cloud service should be introduced merely because it is convenient for implementation.

The architecture must document:

- why the service exists
- what data is transmitted
- where data is stored
- encryption model
- retention
- account model
- cost
- failure behavior

---

# 18. Mobile UX

Mobile platforms do not have a universal Windows-style `Win + V` interaction.

Therefore the mobile UX should be native to each platform.

Primary model:

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

---

# 19. iPhone / iPad

The implementation must respect Apple's pasteboard and background-execution restrictions.

Do not promise unrestricted background clipboard monitoring.

Investigate:

- pasteboard APIs
- Share Sheet
- Widgets
- App Shortcuts
- Shortcuts integration
- Quick Actions
- iPad hardware-keyboard shortcuts

The iPad may support useful keyboard shortcuts when a physical keyboard is connected.

---

# 20. Android

Investigate:

- ClipboardManager
- widgets
- Quick Settings
- Share integration
- keyboard workflows
- Android version-specific clipboard restrictions

Do not assume unrestricted background clipboard monitoring.

---

# 21. Windows

The Windows experience should be conceptually similar to Windows Clipboard History.

Target interaction:

```text
Win + V
```

The project must investigate whether ClipNest can safely integrate with or provide an equivalent experience around this shortcut.

If direct interception/replacement is unreliable or inappropriate:

- do not fake it
- provide a configurable ClipNest global shortcut
- provide equivalent clipboard-history functionality

Windows targets:

- Windows 10
- Windows 11

---

# 22. Linux

Linux support should investigate:

- X11 clipboard mechanisms
- Wayland clipboard mechanisms
- desktop environment behavior
- global shortcuts

Do not assume X11 behavior works unchanged under Wayland.

Document differences.

---

# 23. Security

Clipboard data is sensitive.

The application must:

- never log clipboard content
- never expose clipboard content in crash logs unnecessarily
- never send clipboard data to AI services
- never include clipboard content in analytics
- protect stored data appropriately
- protect synchronized data
- support device revocation

---

# 24. Sensitive Clipboard Data

Potentially sensitive content includes:

- passwords
- OTPs
- API keys
- access tokens
- private keys
- financial information
- confidential text

If sensitive-content detection is implemented, it must be treated as best-effort.

Do not claim perfect detection.

Provide configuration to disable synchronization or retention when appropriate.

---

# 25. Architecture

The final technology stack must be selected based on real platform capabilities.

Potential technologies may include:

- Swift/SwiftUI
- Flutter
- .NET MAUI
- Tauri
- Kotlin Multiplatform
- another appropriate architecture

The selection must consider:

- macOS clipboard APIs
- native global shortcuts
- iOS/iPadOS restrictions
- Windows clipboard APIs
- Android restrictions
- Linux support
- packaging
- maintainability
- performance

The technology decision must be documented.

---

# 26. Logical Architecture

Conceptual architecture:

```text
                    ClipNest
                       │
              ┌────────┴────────┐
              │   Shared Core   │
              └────────┬────────┘
                       │
       ┌───────────────┼────────────────┐
       │               │                │
 Clipboard         Storage            Sync
 Domain             Layer             Layer
       │               │                │
       └───────────────┼────────────────┘
                       │
              Platform Adapters
                       │
       ┌───────────────┼───────────────────┐
       │               │                   │
     macOS          Windows          Mobile/Linux
```

The actual architecture may differ.

The key principle is that platform-specific APIs must not contaminate the core domain unnecessarily.

---

# 27. Local Storage

The application must persist clipboard history locally.

Storage should support:

- item identity
- content
- metadata
- timestamps
- hashes
- pinned state
- synchronization state

Use an appropriate database or persistence mechanism.

Do not choose a database simply because it is familiar.

Choose the smallest reliable solution.

---

# 28. Deduplication

Clipboard duplication should be detected using an appropriate content hash or equivalent mechanism.

Repeated copies of identical content should not unnecessarily fill history.

The exact UX behavior must be documented.

---

# 29. Sync Conflicts

Future synchronization must handle:

- simultaneous changes
- offline devices
- reconnection
- duplicate items
- deletion
- pinning
- timestamps
- failed transfers

Conflict resolution must be deterministic.

Never silently discard data.

---

# 30. Performance

Target:

- instant-feeling popup
- low idle CPU
- low memory usage
- low battery impact
- event-driven clipboard monitoring
- asynchronous persistence
- efficient search

Avoid aggressive polling where platform events are available.

---

# 31. UI Design Language

ClipNest should feel like a polished native productivity application.

Desired qualities:

- compact
- elegant
- clean
- friendly
- premium
- readable
- calm
- modern

Support:

- Light mode
- Dark mode
- System appearance

Avoid excessive:

- gradients
- animations
- glass effects
- rounded-card overload
- decorative UI

The interface should prioritize content.

---

# 32. App Icon

The ClipNest icon should communicate:

- clipboard
- organization
- quick access
- simplicity

It must work at:

- macOS icon sizes
- Dock
- menu bar where applicable
- mobile icon sizes
- installer/package branding

The icon should remain recognizable when very small.

---

# 33. Accessibility

Where platform APIs allow:

- keyboard navigation
- accessible labels
- screen reader support
- focus management
- sufficient contrast
- scalable text

Accessibility should be considered during implementation, not added as an afterthought.

---

# 34. Localization

Initial language:

```text
English
```

Future languages:

```text
Bengali
Japanese
Hindi
Arabic
```

User-facing strings should be centralized.

---

# 35. Testing

Required testing categories:

## Unit

- history
- search
- deduplication
- pinning
- deletion
- expiration
- storage
- sync logic

## Integration

- clipboard capture
- persistence
- device registration
- synchronization

## UI

- open popup
- search
- keyboard navigation
- select item
- copy item
- pin
- delete
- clear

Tests must actually be executed before marking functionality complete.

---

# 36. Build Validation

Every supported target must be validated where the environment permits.

Record:

- command
- target
- result
- warnings
- errors
- fixes

Never claim a successful build that was not actually executed.

---

# 37. Packaging

Potential artifacts:

## macOS

```text
.app
.dmg
.pkg
```

## Windows

```text
.exe
installer
```

## Linux

```text
.AppImage
.deb
.rpm
```

## Android

```text
.apk
.aab
```

## iOS/iPadOS

Signed archive / IPA / TestFlight / App Store workflow where credentials and platform tooling permit.

Signing limitations must be documented.

---

# 38. Documentation Requirements

Required repository documentation:

```text
README.md
MASTER-SPECIFICATION.md
ROADMAP.md
guide.md
release-notes.md
ai-handover.md
```

---

# 39. Git Standards

All project commits must use:

```text
Name:
MD IKRAMUL ISLAM SIDDIQUE POROSH

Email:
poroshScientist@outlook.com
```

No AI identity should appear as the author.

Suggested commit style:

```text
chore: initialize ClipNest project

feat(core): define clipboard domain

feat(storage): implement local clipboard history

feat(macOS): implement native clipboard monitoring

feat(macOS): add global history shortcut

feat(ui): implement clipboard history popup

feat(ui): add search and pinning

test(core): add clipboard history tests

fix(macOS): prevent duplicate clipboard events

docs: add build and distribution guide

release: prepare v0.1.0
```

Do not use meaningless commit messages.

---

# 40. Git Safety

Do not push automatically.

Do not:

- force push
- rewrite history
- delete remote branches
- modify remote configuration

unless explicitly authorized.

Local commits are expected.

---

# 41. ZIP Requirement

The final project should be deliverable as:

```text
ClipNest-with-git-history.zip
```

This archive must contain:

```text
.git/
source/
tests/
documentation/
configuration/
build scripts/
```

The `.git` directory must be preserved.

After extraction:

```bash
git log --oneline --all
```

must show the project history.

Also:

```bash
git status
```

must be valid.

---

# 42. Source-Only ZIP

If practical, also create:

```text
ClipNest-source.zip
```

This may omit `.git`.

The Git-preserving archive is the primary deliverable.

---

# 43. AI Continuity

A future AI agent must be able to continue the project by reading:

```text
MASTER-SPECIFICATION.md
ROADMAP.md
README.md
guide.md
release-notes.md
ai-handover.md
```

No future agent should need the original conversation to understand the project.

---

# 44. Context Exhaustion Procedure

If an AI agent is approaching its context/token limit:

STOP safely.

Do not rush implementation.

Update:

```text
ai-handover.md
ROADMAP.md
release-notes.md
MASTER-SPECIFICATION.md
```

Document:

- current state
- latest commit
- current branch
- completed features
- incomplete features
- current file
- current bug
- root cause
- attempted fixes
- selected fix
- trade-offs
- next exact steps

Then create a logical Git commit using the required author identity.

---

# 45. Bug Documentation

Every significant bug should record:

```text
Problem:
Root Cause:
Affected Platform:
Investigation:
Selected Fix:
Why This Fix:
Alternatives Considered:
Trade-offs:
Verification:
```

This information should be preserved in the appropriate documentation.

---

# 46. Definition of Done — Mac MVP

Mac MVP is complete only when all applicable items below are genuinely implemented and tested:

- [ ] ClipNest launches
- [ ] Clipboard capture works
- [ ] Clipboard history persists
- [ ] History popup works
- [ ] Global shortcut works
- [ ] Shortcut is configurable
- [ ] Search works
- [ ] Keyboard navigation works
- [ ] Mouse interaction works
- [ ] Selecting an item restores clipboard
- [ ] Pin works
- [ ] Delete works
- [ ] Clear works
- [ ] Duplicate handling works
- [ ] History cleanup works
- [ ] Dark mode works
- [ ] Light mode works
- [ ] System appearance works
- [ ] Menu-bar/background operation works where designed
- [ ] Offline operation works
- [ ] Tests pass
- [ ] Documentation is updated
- [ ] Git history is professional
- [ ] Git identity is correct
- [ ] No secrets are committed

---

# 47. Current Project State

At the creation of this specification:

```text
Project:
ClipNest

Primary platform:
macOS

Development status:
Pre-MVP / Initial repository

Core implementation:
Not yet started

Cross-device synchronization:
Not yet implemented

Windows:
Not yet implemented

Linux:
Not yet implemented

Android:
Not yet implemented

iOS:
Not yet implemented

iPadOS:
Not yet implemented
```

This section must be updated as development progresses.

---

# 48. Current Architectural Decisions

## Decision 001 — Mac First

**Decision:** Build and validate macOS before broad cross-platform implementation.

**Reason:** The Mac experience is the immediate product goal.

**Status:** Accepted.

---

## Decision 002 — Offline First

**Decision:** Local clipboard history must work independently of Internet connectivity.

**Reason:** Clipboard management is fundamentally a local utility function.

**Status:** Accepted.

---

## Decision 003 — Synchronization Optional

**Decision:** Synchronization must be an independent capability.

**Reason:** The core product should not depend on servers or Internet connectivity.

**Status:** Accepted.

---

## Decision 004 — Platform Adapters

**Decision:** Platform-specific clipboard behavior must be isolated behind platform adapters/interfaces where practical.

**Reason:** Clipboard APIs and background restrictions differ significantly across operating systems.

**Status:** Accepted.

---

# 49. Open Technical Decisions

The implementation agent must investigate and document:

- final technology stack
- local storage technology
- macOS clipboard API implementation
- global shortcut implementation
- popup/window architecture
- image clipboard support
- LAN discovery
- synchronization protocol
- encryption model
- device identity
- Windows implementation
- Linux X11/Wayland implementation
- mobile strategy

Do not guess when a platform API can be verified.

---

# 50. Final Principle

ClipNest should become a small piece of software that users simply trust.

The ideal experience is:

```text
Copy.
Open ClipNest.
Find it.
Use it.
Done.
```

No unnecessary ceremony.

No unnecessary cloud dependency.

No unnecessary complexity.

Build the smallest reliable thing first.

Then make it beautiful.

Then make it cross-platform.

---

**End of Master Specification**