# ClipNest — Roadmap

> **Your clipboard. Everywhere.**

This roadmap tracks the actual implementation state of ClipNest.

Statuses:

- `[x]` Completed
- `[~]` In Progress
- `[ ]` Planned
- `[!]` Blocked

**Important:** Never mark an item `[x]` unless it has actually been implemented and appropriately validated.

---

# Phase 0 — Repository & Foundation

## Project Initialization

- [x] Create ClipNest repository
- [ ] Initialize application project
- [ ] Configure package/build tooling
- [ ] Configure formatting/linting
- [ ] Configure test infrastructure
- [ ] Configure Git author identity
- [ ] Create initial project structure
- [ ] Create `.gitignore`
- [ ] Create environment/configuration templates

## Documentation Foundation

- [x] Create `README.md`
- [x] Create `MASTER-SPECIFICATION.md`
- [x] Create `ROADMAP.md`
- [ ] Create `guide.md`
- [ ] Create `release-notes.md`
- [ ] Create `ai-handover.md`

---

# Phase 1 — macOS MVP

**Highest priority**

Goal:

> A genuinely usable Mac clipboard-history utility.

---

## 1.1 Architecture

- [ ] Select final technology stack
- [ ] Document technology decision
- [ ] Define shared core interfaces
- [ ] Define macOS platform adapter
- [ ] Define storage abstraction
- [ ] Define clipboard domain model

---

## 1.2 macOS Clipboard Capture

- [ ] Investigate native macOS clipboard APIs
- [ ] Implement clipboard monitoring
- [ ] Capture text clipboard content
- [ ] Detect clipboard changes
- [ ] Prevent duplicate events
- [ ] Handle clipboard monitoring lifecycle
- [ ] Handle application startup
- [ ] Handle application shutdown
- [ ] Validate behavior after system sleep/wake

---

## 1.3 Local History

- [ ] Implement local persistence
- [ ] Store clipboard items
- [ ] Store timestamps
- [ ] Store content type
- [ ] Store hashes
- [ ] Store pinned state
- [ ] Implement configurable history size
- [ ] Implement automatic expiration
- [ ] Implement duplicate detection
- [ ] Preserve pinned items

---

## 1.4 Clipboard History UI

- [ ] Create ClipNest visual identity
- [ ] Create application icon
- [ ] Create floating clipboard popup
- [ ] Implement compact layout
- [ ] Implement clipboard item component
- [ ] Implement timestamps
- [ ] Implement pinned indicators
- [ ] Implement empty state
- [ ] Implement loading state where required
- [ ] Implement error state
- [ ] Implement dark mode
- [ ] Implement light mode
- [ ] Implement system appearance

---

## 1.5 Global Shortcut

- [ ] Research safe macOS global shortcut implementation
- [ ] Implement global shortcut
- [ ] Select initial default shortcut
- [ ] Make shortcut configurable
- [ ] Detect shortcut conflicts where practical
- [ ] Document required permissions

---

## 1.6 Clipboard Restoration

- [ ] Select history item
- [ ] Restore item to system clipboard
- [ ] Close/minimize history popup
- [ ] Verify normal paste behavior
- [ ] Test keyboard selection
- [ ] Test mouse selection

---

## 1.7 Search

- [ ] Add search field
- [ ] Implement local search
- [ ] Add keyboard shortcut/focus behavior
- [ ] Optimize search for larger histories
- [ ] Test search performance

---

## 1.8 History Actions

- [ ] Pin item
- [ ] Unpin item
- [ ] Delete item
- [ ] Clear history
- [ ] Confirm destructive actions where appropriate
- [ ] Copy item again
- [ ] Handle duplicate clipboard values

---

## 1.9 Keyboard UX

- [ ] Arrow navigation
- [ ] Enter to select
- [ ] Escape to close
- [ ] Keyboard search
- [ ] Delete shortcut where appropriate
- [ ] Pin shortcut where appropriate
- [ ] Ensure focus management

---

## 1.10 macOS Background Experience

- [ ] Menu-bar integration
- [ ] Background operation
- [ ] Launch-at-login option if appropriate
- [ ] Settings access
- [ ] Quit behavior
- [ ] Sleep/wake handling

---

## 1.11 macOS Testing

- [ ] Unit tests
- [ ] Storage tests
- [ ] Clipboard tests
- [ ] Search tests
- [ ] History tests
- [ ] UI tests where practical
- [ ] Global shortcut tests
- [ ] Offline tests
- [ ] Long-history performance tests

---

# Phase 2 — macOS Polish & Release

Goal:

> Turn the working MVP into a polished first release.

- [ ] Refine UI
- [ ] Refine typography
- [ ] Refine spacing
- [ ] Refine animations
- [ ] Refine keyboard navigation
- [ ] Accessibility pass
- [ ] Performance profiling
- [ ] Memory profiling
- [ ] CPU profiling
- [ ] Error handling pass
- [ ] Privacy review
- [ ] Security review
- [ ] App icon finalization
- [ ] Build `.app`
- [ ] Build `.dmg`
- [ ] Build `.pkg` where practical
- [ ] Test clean installation
- [ ] Test upgrade installation
- [ ] Test uninstall/removal workflow
- [ ] Create release documentation
- [ ] Prepare first version

---

# Phase 3 — Local Network Synchronization

Goal:

> Synchronize authorized ClipNest devices on the same network without requiring cloud infrastructure.

- [ ] Define sync protocol
- [ ] Define device identity
- [ ] Define device authorization
- [ ] Define secure pairing
- [ ] Implement LAN discovery
- [ ] Implement encrypted communication
- [ ] Implement sync queue
- [ ] Implement retry
- [ ] Implement offline queue
- [ ] Implement deduplication
- [ ] Implement conflict resolution
- [ ] Implement device revocation
- [ ] Add sync status UI
- [ ] Add sync settings
- [ ] Test network interruption
- [ ] Test device restart
- [ ] Test simultaneous clipboard changes

---

# Phase 4 — iPhone & iPad

Goal:

> Provide the best practical clipboard-history experience allowed by iOS/iPadOS.

- [ ] Evaluate iOS/iPadOS clipboard restrictions
- [ ] Implement mobile UI
- [ ] Implement local history where permitted
- [ ] Implement search
- [ ] Implement pinning
- [ ] Implement deletion
- [ ] Implement copy-again
- [ ] Implement device synchronization
- [ ] Investigate Share Sheet
- [ ] Investigate Widgets
- [ ] Investigate App Shortcuts
- [ ] Investigate Shortcuts integration
- [ ] Investigate iPad keyboard shortcuts
- [ ] Implement appropriate features
- [ ] Document platform restrictions
- [ ] Test on iPhone
- [ ] Test on iPad
- [ ] Prepare signing/distribution documentation

---

# Phase 5 — Windows

Goal:

> Provide a Windows clipboard-history experience comparable in concept to `Win + V`.

- [ ] Implement Windows clipboard adapter
- [ ] Implement local history
- [ ] Implement popup
- [ ] Implement global shortcut
- [ ] Investigate `Win + V`
- [ ] Determine whether safe integration is possible
- [ ] Implement equivalent shortcut if required
- [ ] Windows 10 validation
- [ ] Windows 11 validation
- [ ] Test sleep/wake
- [ ] Test clipboard synchronization
- [ ] Build `.exe`
- [ ] Build installer
- [ ] Test clean installation

---

# Phase 6 — Android

Goal:

> Provide a native-feeling clipboard history experience on Android within OS restrictions.

- [ ] Investigate Android clipboard restrictions
- [ ] Implement Android storage
- [ ] Implement mobile history UI
- [ ] Implement search
- [ ] Implement pin
- [ ] Implement deletion
- [ ] Implement copy-again
- [ ] Implement synchronization
- [ ] Investigate widgets
- [ ] Investigate Quick Settings
- [ ] Investigate Share integration
- [ ] Investigate keyboard integration
- [ ] Test supported Android versions
- [ ] Build APK
- [ ] Build AAB

---

# Phase 7 — Linux

Goal:

> Provide practical desktop clipboard management across Linux environments.

- [ ] Implement Linux clipboard adapter
- [ ] Investigate X11
- [ ] Implement X11 support
- [ ] Investigate Wayland
- [ ] Implement Wayland support where practical
- [ ] Implement history
- [ ] Implement popup
- [ ] Implement global shortcut
- [ ] Test major desktop environments where practical
- [ ] Build AppImage
- [ ] Build `.deb`
- [ ] Build `.rpm` where practical
- [ ] Document environment-specific limitations

---

# Phase 8 — Optional Internet Synchronization

This phase is intentionally optional.

- [ ] Determine whether Internet sync provides meaningful value
- [ ] Define account model
- [ ] Define authentication
- [ ] Define device authorization
- [ ] Define encryption model
- [ ] Define server architecture
- [ ] Define retention policy
- [ ] Define cost model
- [ ] Implement encrypted transport
- [ ] Implement synchronization
- [ ] Implement offline queue
- [ ] Implement device revocation
- [ ] Implement privacy controls
- [ ] Document all transmitted data

Do NOT implement this phase merely because a backend can be built.

---

# Phase 9 — Security & Privacy Hardening

- [ ] Security review
- [ ] Dependency audit
- [ ] Secret scanning
- [ ] Storage protection review
- [ ] Network encryption review
- [ ] Device authentication review
- [ ] Device revocation testing
- [ ] Logging review
- [ ] Sensitive clipboard handling review
- [ ] Privacy documentation

---

# Phase 10 — Quality & Performance

- [ ] Startup performance profiling
- [ ] Popup latency profiling
- [ ] CPU usage profiling
- [ ] Memory usage profiling
- [ ] Large history testing
- [ ] Large clipboard content testing
- [ ] Battery impact testing
- [ ] Network interruption testing
- [ ] Long-running process testing
- [ ] Sleep/wake testing
- [ ] Crash recovery testing

---

# Phase 11 — Distribution

## macOS

- [ ] `.app`
- [ ] `.dmg`
- [ ] `.pkg`
- [ ] Signing documentation
- [ ] Notarization documentation

## Windows

- [ ] `.exe`
- [ ] Installer
- [ ] Distribution documentation

## Linux

- [ ] AppImage
- [ ] `.deb`
- [ ] `.rpm` where practical

## Android

- [ ] `.apk`
- [ ] `.aab`

## iOS/iPadOS

- [ ] Development build
- [ ] Signing documentation
- [ ] TestFlight documentation
- [ ] App Store documentation

---

# Phase 12 — Documentation

- [ ] README complete
- [ ] Master specification updated
- [ ] Roadmap updated
- [ ] User/developer guide complete
- [ ] Release notes complete
- [ ] AI handover complete
- [ ] Architecture documented
- [ ] Platform limitations documented
- [ ] Build instructions verified
- [ ] Distribution instructions verified

---

# Phase 13 — Git & Release Management

- [ ] All commits use required author
- [ ] Commit messages are professional
- [ ] No secrets in history
- [ ] No AI identity in history
- [ ] No unnecessary history rewriting
- [ ] Working tree verified
- [ ] Release tag created where appropriate
- [ ] Release notes finalized
- [ ] Source ZIP generated
- [ ] Git-history ZIP generated

---

# Definition of Product Completion

ClipNest can be considered a mature cross-platform product when:

- [ ] macOS experience is polished
- [ ] Windows experience is polished
- [ ] Linux support is practical
- [ ] iPhone/iPad experience respects platform limitations
- [ ] Android experience respects platform limitations
- [ ] local clipboard history is reliable
- [ ] synchronization is reliable
- [ ] security model is documented and tested
- [ ] builds are reproducible
- [ ] distribution is documented
- [ ] tests provide meaningful coverage
- [ ] documentation is complete
- [ ] Git history is professional

---

# Current Priority

The immediate priority is NOT to implement every platform.

The immediate priority is:

```text
MACOS MVP
    ↓
POLISH
    ↓
TEST
    ↓
PACKAGE
    ↓
RELEASE
    ↓
SYNC
    ↓
OTHER PLATFORMS
```

Build the foundation correctly before expanding.

---

# Future Ideas

Potential future enhancements:

- clipboard categories
- favorites
- tags
- snippets
- smart clipboard filtering
- file clipboard support
- rich-text clipboard support
- customizable popup size
- customizable keyboard shortcuts
- multiple clipboard profiles
- import/export history
- encrypted backups
- automatic backup
- device groups
- per-device sync rules
- application-specific exclusions
- temporary clipboard mode
- sensitive-content expiration
- advanced search
- clipboard statistics

These are ideas, not MVP requirements.

Do not implement them before the core product is stable unless there is a strong technical reason.

---

**Last Updated:** Initial project specification  
**Maintainer:** MD IKRAMUL ISLAM SIDDIQUE POROSH