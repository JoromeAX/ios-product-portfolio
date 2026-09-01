# Charades Party Game

[View on the App Store](https://apps.apple.com/us/app/charades-party-game/id6787904891)

## Product context

Charades Party Game is a social word game in which a player holds the phone to their forehead while teammates provide clues. Device tilt records correct answers or skips, configurable timers shape each round, and optional replay capture preserves gameplay moments.

The central challenge is combining a simple party-game experience with reliable motion interpretation, orientation changes, camera recording, media lifecycle management, localization, and monetization.

## My scope

My work included:

- implementing the application flow and SwiftUI screens from product designs;
- building deck selection, round configuration, gameplay, scoring, and result flows;
- implementing tilt-driven answer input with Core Motion;
- managing portrait and landscape orientation transitions during gameplay;
- implementing optional camera replay recording, local replay storage, playback, sharing, and deletion;
- creating localized deck content and language-selection flows;
- integrating sound, haptics, onboarding, settings, subscriptions, and release configuration;
- delivering the initial release and several follow-up versions.

## Engineering focus

### Motion as user input

Raw orientation values are noisy and can cross thresholds repeatedly. A small state machine distinguishes neutral, pending, and accepted states so that one physical gesture produces one answer event and the device must return to a neutral position before another event is accepted.

### Coordinated game state

Round time, current card, score, answer history, sound, haptics, motion input, and recording state all progress together. The gameplay screen coordinates these concerns around a clear round lifecycle so cleanup occurs when a round ends or the user leaves early.

### Replay capture and ownership

Camera recording is optional and permission-aware. Recorded files are moved into an app-managed location and represented by lightweight metadata, allowing the replay library to load thumbnails, play, share, and delete files without keeping media resources open unnecessarily.

### Localization-ready content

Interface strings and deck content use an explicit language model. This keeps content selection predictable and allows the product to support multiple languages without tying game logic to the current device locale.

## Technology

Swift, SwiftUI, Combine, Core Motion, AVFoundation, AVKit, UIKit, StoreKit, Apphud, Lottie, Core Graphics, and App Store Connect.

## Public outcome

The game shipped to the App Store and progressed through multiple follow-up releases with multilingual support and subscription monetization. Source code, internal metrics, and proprietary visual assets are intentionally not published.

