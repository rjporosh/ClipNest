# BUILD CLIPNEST — MASTER AUTONOMOUS CODING AGENT COMMAND

You are the autonomous product architect, senior software engineer, UI/UX designer, platform engineer, QA engineer, security engineer, build/release engineer, technical writer, and Git release manager for this project.

Your job is to **actually build and deliver the complete working application**, not merely describe how to build it.

Do not stop after creating a plan.

Do not return only sample code.

Implement the project, test it, fix it, document it, create professional Git history, package it, and return the completed project as a ZIP archive when the environment supports file creation.

---

# 1. PRODUCT NAME

The product name is:

# ClipNest

Tagline:

> Your clipboard. Everywhere.

Keep the branding short, elegant, modern, friendly, and professional.

The name should appear naturally in:

- application title
- UI
- README
- documentation
- package/build metadata where appropriate
- app icon/branding where practical

Do not make the branding childish.

The visual identity should feel like a polished native productivity utility.

---

# 2. PRIMARY PRODUCT GOAL

Build a small, beautiful, extremely practical clipboard manager.

The **FIRST AND MOST IMPORTANT TARGET IS macOS**.

The first release should make a Mac user feel:

> "This is basically the clipboard history experience I wish macOS had."

The primary experience should be similar in simplicity to Windows Clipboard History (`Win + V`).

Example:

    Copy something

        ↓

    Press the ClipNest global shortcut

        ↓

    Small beautiful floating clipboard-history window appears

        ↓

    See previous copied items

        ↓

    Search/select one

        ↓

    It becomes the current system clipboard

        ↓

    Paste normally

The application should be fast enough that this interaction feels almost instantaneous.

---

# 3. IMPORTANT PRODUCT PHILOSOPHY

Build a **small utility**, not a bloated enterprise system.

Prioritize:

1. Reliability
2. Native platform behavior
3. Speed
4. Privacy
5. Beautiful UX
6. Offline-first functionality
7. Maintainability
8. Cross-platform extensibility

Do NOT over-engineer the application.

Do NOT create unnecessary microservices.

Do NOT create a backend just because a backend is fashionable.

Do NOT create a huge architecture for a tiny clipboard utility.

Simple is a feature.

---

# 4. PHASE 1 — MACOS FIRST

The first genuinely working target is:

# macOS

The Mac version must be the most polished and complete initial implementation.

Support Apple Silicon Macs.

Support Intel Macs if the chosen technology and build environment make this reasonably practical.

The application should preferably run as a lightweight background/menu-bar utility.

It should:

- monitor clipboard changes using the appropriate macOS APIs
- store clipboard history locally
- provide a global keyboard shortcut
- display a floating clipboard-history popup
- allow keyboard navigation
- allow mouse interaction
- allow search
- allow copying an old item back to the system clipboard
- support pinning
- support deletion
- support clearing history
- support dark/light/system appearance
- launch in the background if enabled
- remain lightweight

---

# 5. MACOS CLIPBOARD EXPERIENCE

The primary Mac interaction should be similar to:

    Windows:
    Win + V

For macOS provide a configurable global shortcut.

A reasonable default can be:

    Command + Shift + V

or another safe shortcut if that conflicts with native macOS behavior.

The shortcut must be configurable.

When invoked, show a small floating UI such as:

    ┌───────────────────────────────────────────┐
    │  ClipNest                         ⚙      │
    │  🔍 Search clipboard...                  │
    ├───────────────────────────────────────────┤
    │  Hello World                         2m  │
    │  https://example.com                  5m │
    │  Console.WriteLine("Hello");          8m │
    │  Meeting notes...                     12m │
    └───────────────────────────────────────────┘

Selecting an item should:

1. copy it into the system clipboard
2. close or minimize the popup according to UX
3. allow the user to paste normally

The interaction should feel native and instant.

---

# 6. BEAUTIFUL UI / UX

Create a **professional, elegant, eye-catching, charming UI**.

The application should look like something a real software company could ship.

Visual direction:

- minimal
- premium
- modern
- calm
- polished
- compact
- responsive
- native-feeling
- excellent typography
- excellent spacing
- subtle animations
- beautiful hover/focus states
- keyboard-friendly
- dark mode
- light mode
- system theme

Avoid:

- excessive gradients
- giant cards
- unnecessary glassmorphism
- excessive shadows
- clutter
- huge headers
- dashboard-like layouts
- pointless animations

The app is a utility.

The UI should communicate:

> "Small. Fast. Beautiful. Useful."

---

# 7. CLIPBOARD HISTORY

Support a local clipboard history.

At minimum:

- plain text
- multiline text
- URLs
- numbers
- code snippets

Support images if technically practical for the selected architecture.

Each item should have appropriate metadata, such as:

    id
    content type
    content
    created time
    source device
    pinned state
    content hash
    size
    synchronization state

Avoid storing unnecessarily large binary content in inappropriate database fields.

Use suitable local storage.

---

# 8. CLIPBOARD HISTORY FEATURES

Implement:

- automatic capture
- search
- pin
- unpin
- delete
- clear all
- copy again
- duplicate detection
- configurable history limit
- automatic expiration
- pinned items survive normal cleanup

Keyboard navigation should be excellent on desktop.

For example:

    ↑ / ↓
    Enter
    Escape

and other appropriate shortcuts.

---

# 9. LOCAL-FIRST / OFFLINE-FIRST

This is a CORE requirement.

The application must NOT require Internet access for its fundamental functionality.

Without Internet the Mac application must still support:

- clipboard capture
- clipboard history
- search
- pinning
- deletion
- clearing
- copy-again
- local storage
- settings

The user should be able to use ClipNest completely offline on a single device.

Do not make cloud services mandatory.

---

# 10. CROSS-DEVICE SYNCHRONIZATION

Synchronization is a secondary feature.

The architecture must support synchronization without making the core clipboard dependent on it.

Preferred priority:

    1. Local clipboard
    2. Local history
    3. Same-device operation
    4. Local-network synchronization
    5. Optional secure peer-to-peer synchronization
    6. Optional encrypted Internet relay/cloud synchronization

Investigate whether local LAN synchronization can provide the first cross-device experience.

Example:

    MacBook
       ↕
    Home Wi-Fi
       ↕
    iPhone

or:

    MacBook
       ↕
    Home Wi-Fi
       ↕
    Windows PC

Do not blindly trust LAN devices.

Use secure device authorization and encryption.

---

# 11. CROSS-DEVICE VISION

The long-term experience should be:

    MacBook
       ↕
    iPhone
       ↕
    iPad
       ↕
    Windows PC
       ↕
    Android phone
       ↕
    Android tablet
       ↕
    Linux PC

A clipboard copied on one authorized device should become available on another authorized device when synchronization is enabled and technically permitted.

The application should use the same conceptual clipboard model across all platforms while respecting each operating system's limitations.

---

# 12. WINDOWS

The Windows version should provide a clipboard-history experience comparable to Windows Clipboard History.

Target:

    Win + V

If Windows allows safe integration with the native shortcut, investigate it.

If replacing/intercepting the system shortcut is unreliable or inappropriate:

- do not fake it
- provide a configurable global ClipNest shortcut
- make the experience equivalent

Windows should support:

- clipboard monitoring
- local history
- popup history UI
- search
- pinning
- deletion
- copy again
- offline use
- optional synchronization

Support Windows 10 and Windows 11 where reasonably possible.

Do not unnecessarily depend on Windows 11-only APIs.

---

# 13. LINUX

Provide Linux desktop support where practical.

The clipboard architecture must account for:

- X11
- Wayland

Do not assume X11 behavior automatically works under Wayland.

Provide:

- clipboard history
- global shortcut where possible
- popup UI
- search
- copy again
- local storage
- optional synchronization

If some functionality is impossible or restricted under a particular environment, document the exact limitation.

---

# 14. IPHONE / IPAD

iPhone and iPad do NOT have Windows-style `Win + V`.

Do not force desktop interaction patterns onto mobile.

Mobile UX should primarily be:

    Open ClipNest

        ↓

    Clipboard History

        ↓

    Search / select item

        ↓

    Copy Again

The iPad version should additionally investigate physical keyboard shortcuts when a keyboard is connected.

Investigate appropriate platform features:

- iOS/iPadOS Share Sheet
- Widgets
- App Shortcuts
- Shortcuts integration
- Quick Actions
- iPad keyboard shortcuts

Respect Apple's actual background clipboard/pasteboard restrictions.

Do NOT falsely claim that iOS/iPadOS permits unrestricted background clipboard monitoring.

If iOS/iPadOS limits automatic clipboard monitoring, implement the best practical native UX and document the limitation.

---

# 15. ANDROID

Android should provide:

- clipboard history screen
- search
- pin
- delete
- copy again
- device information
- synchronization status

Investigate practical integration with:

- Android clipboard APIs
- widgets
- Quick Settings
- Share functionality
- keyboard-related clipboard workflows

Respect Android's clipboard/privacy/background restrictions.

Do not claim unrestricted background clipboard monitoring when the OS does not permit it.

---

# 16. PRIVACY & SECURITY

Clipboard data can contain:

- passwords
- OTPs
- API keys
- tokens
- private keys
- credit-card information
- personal messages
- confidential work data

Treat clipboard content as sensitive.

Requirements:

- never log clipboard contents
- never send clipboard contents to an AI service
- never expose clipboard contents in diagnostics
- encrypt synchronization traffic
- securely authenticate devices
- allow device revocation
- protect local data appropriately
- configurable history expiration
- ability to disable synchronization

Investigate platform-secure storage mechanisms.

If sensitive-content detection is implemented, document that detection is not perfect.

Do not falsely promise perfect secret detection.

---

# 17. ARCHITECTURE

Choose the most appropriate technology based on real platform capabilities.

Before coding:

1. inspect the environment
2. inspect available SDKs
3. inspect available build tools
4. evaluate realistic cross-platform technologies
5. choose the architecture

Prefer:

    Shared Core
        │
        ├── Clipboard Domain
        ├── History
        ├── Search
        ├── Storage
        ├── Sync
        └── Security
              │
              ├── macOS adapter
              ├── iOS/iPadOS adapter
              ├── Windows adapter
              ├── Android adapter
              └── Linux adapter

Platform-specific clipboard functionality MUST remain isolated from the shared business logic.

If one framework cannot correctly implement native clipboard behavior on every platform, use platform-specific implementations behind shared interfaces.

Do not force a framework to do something the operating system does not allow.

---

# 18. TECHNOLOGY DECISION

You are responsible for selecting the technology stack.

Consider practical options such as:

- Swift/SwiftUI + native Apple implementation
- Flutter
- .NET MAUI
- Tauri
- Kotlin Multiplatform
- another appropriate solution

The decision must be based on:

- macOS clipboard APIs
- iOS/iPadOS restrictions
- Windows clipboard APIs
- Android restrictions
- Linux support
- native global shortcuts
- background execution
- performance
- packaging
- maintainability

Because macOS is the FIRST target, prioritize a solution that provides excellent native Mac behavior.

If a shared UI framework is selected, use native platform APIs where required.

Document the technology decision and alternatives in:

    master-specification.md

---

# 19. STORAGE

Use appropriate local persistence.

The local database/storage must support:

- clipboard history
- metadata
- pinned items
- timestamps
- hashes
- device information
- sync state

Use deduplication where sensible.

Do not store duplicate clipboard contents unnecessarily.

---

# 20. SYNC CONFLICTS

Design deterministic synchronization.

Handle:

- offline devices
- reconnecting devices
- duplicate clipboard content
- simultaneous clipboard changes
- deleted item vs incoming item
- pinned vs unpinned state
- timestamps
- interrupted synchronization

Document the conflict-resolution strategy.

Never silently destroy user data.

---

# 21. PERFORMANCE

Optimize for a utility application.

Prioritize:

- instant popup
- low CPU
- low memory
- low battery consumption
- event-based clipboard monitoring instead of unnecessary polling
- non-blocking storage
- efficient search
- efficient history cleanup

Do not run expensive work on the UI thread.

---

# 22. ACCESSIBILITY

Support where practical:

- keyboard navigation
- screen readers
- accessible labels
- focus management
- appropriate contrast
- scalable text

---

# 23. LOCALIZATION

Architect the application for localization.

Initial language:

    English

Keep user-visible strings centralized.

Future languages may include:

- Bengali
- Japanese
- Hindi
- Arabic

Do not scatter hardcoded strings throughout the application.

---

# 24. TESTING

Implement real tests.

At minimum:

### Unit Tests

- clipboard model
- history
- search
- pinning
- deletion
- cleanup
- deduplication
- sync logic
- conflict resolution

### Integration Tests

- local persistence
- device registration
- synchronization
- authentication

### UI Tests

Test important flows:

1. copy text
2. capture clipboard
3. open history
4. search
5. select old item
6. restore clipboard
7. pin
8. delete
9. clear
10. offline operation
11. synchronization where implemented

Actually run tests where the environment permits.

Never claim a test passed unless it was actually executed.

---

# 25. BUILD VALIDATION

Actually run builds where the environment allows.

Record:

- platform
- command
- result
- warnings
- errors
- fixes

If a platform cannot be built because the required SDK, signing certificate, simulator, account, or operating system is unavailable, document that honestly.

Never fabricate build success.

---

# 26. APP ICON / BRANDING

Create a professional ClipNest application icon.

The icon should be:

- recognizable
- minimal
- modern
- clipboard-inspired
- visually clean
- suitable for macOS
- scalable
- suitable for mobile later

Do not make the icon overly complicated.

Use the ClipNest branding consistently.

---

# 27. DOCUMENTATION

Create and maintain:

    README.md
    guide.md
    master-specification.md
    roadmap.md
    release-notes.md
    ai-handover.md

---

# 28. README.md

Include:

- ClipNest overview
- product philosophy
- screenshots/placeholders if appropriate
- supported platforms
- features
- architecture
- installation
- development
- build
- testing
- packaging
- limitations
- roadmap

---

# 29. guide.md

Create a practical user/developer guide.

Explain:

### macOS

- installation
- permissions
- first launch
- menu bar
- keyboard shortcut
- clipboard history
- settings
- build
- `.app`
- `.dmg`
- `.pkg`

### Windows

- installation
- clipboard history
- shortcut
- build
- `.exe`
- installer

### Linux

- installation
- X11/Wayland considerations
- AppImage
- `.deb`
- `.rpm` where available

### Android

- APK installation
- AAB generation
- permissions
- clipboard limitations

### iPhone/iPad

- development installation
- signing
- TestFlight
- App Store
- IPA limitations

Clearly distinguish unsigned/debug builds from signed production builds.

---

# 30. MASTER-SPECIFICATION.md

This is the permanent source of truth.

It must document:

- product purpose
- architecture
- technology decision
- directory structure
- requirements
- implemented features
- unfinished features
- platform behavior
- platform limitations
- storage
- synchronization
- security
- APIs
- configuration
- build system
- testing
- packaging
- distribution
- Git conventions
- architectural decisions
- rejected approaches
- trade-offs

Update it whenever important architecture or product decisions change.

---

# 31. ROADMAP.MD

Track:

    [x] Completed
    [~] In Progress
    [ ] Planned
    [!] Blocked

At minimum include:

## Phase 1
Mac MVP

## Phase 2
Mac polish + advanced clipboard features

## Phase 3
LAN synchronization

## Phase 4
iPhone/iPad

## Phase 5
Windows

## Phase 6
Android

## Phase 7
Linux

## Phase 8
Optional encrypted Internet synchronization

Do not mark anything completed unless it is actually implemented and validated.

---

# 32. RELEASE-NOTES.MD

For every meaningful milestone record:

- version
- date
- features
- improvements
- bugs fixed
- breaking changes
- known issues
- build status
- artifacts

---

# 33. AI-HANDOVER.MD

This file exists specifically so another AI agent can continue the project later.

Whenever context/token budget becomes insufficient:

STOP implementation safely.

Before stopping update:

    ai-handover.md
    roadmap.md
    release-notes.md
    master-specification.md

The handover MUST include:

### Current State

- current branch
- latest commit
- current milestone
- current feature
- current file being modified

### Completed

Exact completed work.

### In Progress

Exact unfinished work.

### Not Started

Untouched requirements.

### Bugs

For every important bug:

    Symptom:
    Root Cause:
    Investigation:
    Selected Fix:
    Why This Fix:
    Alternatives:
    Trade-offs:
    Verification:

### Next Actions

Give exact steps another agent can execute.

Example:

    1. Open X
    2. Implement Y
    3. Run Z
    4. Fix result
    5. Run tests
    6. Commit milestone

The next agent must be able to continue without reading this original conversation.

---

# 34. GIT HISTORY

Create professional Git history throughout development.

EVERY COMMIT MUST USE:

    Name:
    MD IKRAMUL ISLAM SIDDIQUE POROSH

    Email:
    poroshScientist@outlook.com

Do NOT use:

- ChatGPT
- Claude
- Codex
- OpenAI
- Anthropic
- AI
- AI Agent

as Git author/committer identity.

Use meaningful milestone commits.

Examples:

    chore: initialize ClipNest project

    feat(core): define clipboard domain model

    feat(storage): implement local clipboard history

    feat(macOS): implement native clipboard monitoring

    feat(macOS): add global clipboard history shortcut

    feat(ui): implement ClipNest history popup

    feat(ui): add clipboard search and pinning

    test(core): add clipboard history coverage

    fix(macOS): prevent duplicate clipboard events

    feat(sync): add local device discovery

    feat(sync): implement encrypted device communication

    docs: add ClipNest distribution guide

    release: prepare v0.1.0

Avoid meaningless commits such as:

    update
    changes
    final
    stuff
    fix
    test

Create commits at logical engineering milestones.

---

# 35. GIT SAFETY

Do NOT push to GitHub or any remote.

Do NOT:

- git push
- force push
- rewrite history
- delete remote branches
- modify remote settings

unless I explicitly instruct you to do so.

You may create local commits.

Before each meaningful commit inspect:

    git status
    git diff
    git diff --cached

Never commit secrets.

Never commit:

- API keys
- passwords
- tokens
- certificates
- private signing keys
- `.env` secrets
- credentials

---

# 36. REQUIRED GIT VERIFICATION

Before final delivery execute:

    git log --format="%h | %an | %ae | %s"

Verify that the project commits use:

    MD IKRAMUL ISLAM SIDDIQUE POROSH
    poroshScientist@outlook.com

Also verify:

    git status

The repository must be clean or the remaining changes must be explicitly documented.

---

# 37. ZIP DELIVERY — VERY IMPORTANT

When implementation is complete, create a complete ZIP archive.

The PRIMARY deliverable must be:

    ClipNest-with-git-history.zip

It MUST contain:

- complete source code
- tests
- documentation
- build scripts
- configuration templates
- `master-specification.md`
- `roadmap.md`
- `release-notes.md`
- `ai-handover.md`
- `guide.md`
- `README.md`
- `.git/`

The `.git/` directory MUST be included so the complete local Git history is preserved.

After extracting the ZIP, this must work:

    cd ClipNest
    git log --oneline --all

and show the professional commit history.

Also verify:

    git status

---

# 38. OPTIONAL SOURCE-ONLY ZIP

If practical, also create:

    ClipNest-source.zip

This may exclude `.git/`.

The important required artifact is:

    ClipNest-with-git-history.zip

---

# 39. FINAL ARTIFACT CHECK

Before returning the ZIP verify:

    [ ] Source exists
    [ ] Mac implementation works
    [ ] Clipboard monitoring works
    [ ] Local clipboard history works
    [ ] Global shortcut works
    [ ] Popup UI works
    [ ] Search works
    [ ] Pin works
    [ ] Delete works
    [ ] Clear works
    [ ] Copy-again works
    [ ] Offline functionality works
    [ ] Tests executed
    [ ] Documentation exists
    [ ] Git repository exists
    [ ] Git history exists
    [ ] Git author verified
    [ ] .git included in ZIP
    [ ] ZIP can be extracted
    [ ] Extracted repository has valid Git history
    [ ] No secrets included
    [ ] No remote push performed
    [ ] Platform limitations documented
    [ ] Remaining roadmap accurately documented

Do NOT claim something is complete if it was not actually implemented.

---

# 40. IF THE ENVIRONMENT SUPPORTS IMAGE GENERATION

If the coding environment provides an image-generation capability, create a professional ClipNest icon/logo and include the generated assets in the project.

If image generation is unavailable, create an appropriate vector/programmatic icon instead.

Do not block the entire project merely because image generation is unavailable.

---

# 41. DEVELOPMENT STRATEGY

Work autonomously in this order:

### Step 1
Inspect environment.

### Step 2
Select technology.

### Step 3
Create architecture.

### Step 4
Initialize Git with the required author identity.

### Step 5
Create:

    master-specification.md
    roadmap.md
    release-notes.md
    ai-handover.md

### Step 6
Build the Mac clipboard engine.

### Step 7
Build local storage/history.

### Step 8
Build the Mac floating clipboard popup.

### Step 9
Build global shortcut.

### Step 10
Build search/pinning/deletion.

### Step 11
Polish UI/UX.

### Step 12
Add tests.

### Step 13
Add synchronization architecture.

### Step 14
Implement LAN synchronization if practical.

### Step 15
Prepare future iOS/iPadOS/Windows/Android/Linux adapters.

### Step 16
Build and validate available targets.

### Step 17
Complete documentation.

### Step 18
Update release notes and roadmap.

### Step 19
Verify Git history.

### Step 20
Create:

    ClipNest-with-git-history.zip

### Step 21
Return the ZIP as the final deliverable.

---

# 42. IMPORTANT — DO NOT PRETEND

If something cannot be completed because of:

- missing Apple Developer credentials
- missing certificates
- missing provisioning profiles
- unavailable platform SDK
- unavailable physical device
- unavailable simulator
- unavailable operating system
- platform security restrictions

do not fake it.

Implement everything that can genuinely be implemented.

Document exactly what remains.

The ZIP should still contain the complete working source and all documentation.

---

# 43. TOKEN / CONTEXT EXHAUSTION RULE

This rule is mandatory.

If you estimate that the remaining context/token budget is insufficient to safely continue:

STOP.

Do not rush.

Do not leave undocumented half-finished work.

Do not claim completion.

Do not start another feature.

Instead:

1. Save current work.
2. Leave the project in a recoverable state.
3. Update:

       ai-handover.md
       roadmap.md
       release-notes.md
       master-specification.md

4. Create a logical Git commit using:

       MD IKRAMUL ISLAM SIDDIQUE POROSH
       poroshScientist@outlook.com

5. Document exactly what the next agent must do.
6. Stop safely.

The next agent should be able to read the repository and continue from exactly that point.

---

# 44. FINAL RESPONSE

When the project is actually complete, return:

1. A concise completion summary.
2. The generated ZIP file:

       ClipNest-with-git-history.zip

3. If created:

       ClipNest-source.zip

4. Build/test status.
5. Platforms actually implemented.
6. Known platform limitations.
7. Latest Git commit.
8. Confirmation that `.git` is included.
9. Confirmation that no remote push was performed.

Do not give me a huge explanation instead of the artifact.

The actual deliverable is the working project.

---

# 45. MOST IMPORTANT REQUIREMENT

The FIRST release priority is:

# MACOS

I want to be able to use ClipNest on my Mac like this:

    Copy text
        ↓
    Press global ClipNest shortcut
        ↓
    Beautiful clipboard history popup
        ↓
    See everything I recently copied
        ↓
    Search if necessary
        ↓
    Select an item
        ↓
    ClipNest puts it back into macOS clipboard
        ↓
    Paste normally

It should feel simple, fast, polished and natural.

Then build the architecture so the same core experience can eventually extend to:

    macOS
    Windows
    Linux
    iPhone
    iPad
    Android phone
    Android tablet

while respecting the real limitations of each operating system.

Build something genuinely useful rather than something merely impressive in a README.

BEGIN NOW.

Inspect the environment first.

Then build ClipNest.

Do not stop at planning.

Implement, test, fix, document, commit, package, and deliver the ZIP with complete Git history.