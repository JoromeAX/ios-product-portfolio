# Audio Notes

[View on the App Store](https://apps.apple.com/us/app/audio-notes/id6785789163)

## Product context

Audio Notes is an iPhone productivity app for capturing conversations, meetings, lectures, interviews, and personal ideas. Users can record audio, manage a local recording library, transcribe speech, edit and export recordings, and organize important items around dates.

The main engineering challenge is coordinating long-running audio work with a responsive interface while keeping file state, playback state, and user actions consistent.

## My scope

My work on the iOS product included:

- implementing the application structure and SwiftUI user flows from product designs;
- building recording, pause, resume, stop, playback, editing, export, and sharing workflows;
- implementing waveform extraction and timeline presentation;
- integrating on-device speech transcription with language selection;
- designing file-backed recording persistence and repository interfaces;
- implementing search, favorites, scheduled items, notifications, and settings;
- integrating subscription access and App Store release configuration;
- supporting the product from its first release through a follow-up version.

## Engineering focus

### Actor-isolated audio services

Recording, playback, editing, export, transcription, and waveform work have different lifecycles but often operate on the same files. These capabilities are separated behind service interfaces and implemented with actor-isolated components, reducing shared mutable state and clarifying ownership of long-running operations.

### Observable recording state

The recording interface needs frequent duration and audio-level updates without coupling AVFoundation callbacks directly to the view. A stream of recording snapshots represents phase, elapsed time, and current level, while the view model translates that stream into presentation state.

### File-backed persistence

Recording metadata and audio files are treated as related but separate resources. Repository and file-URL abstractions make create, duplicate, rename, edit, export, and delete operations explicit, while in-memory implementations support isolated development states.

### Recoverable user flows

Microphone and speech permissions, audio-session interruptions, missing files, failed exports, and transcription availability all affect the user journey. The product models alerts, sheets, progress, and transient feedback as explicit presentation states instead of relying on silent failure.

## Technology

Swift, SwiftUI, Combine, Swift Concurrency, AVFoundation, AVFAudio, Speech, UIKit, UserNotifications, Apphud, Lottie, and App Store Connect.

## Public outcome

Audio Notes shipped to the App Store and received a follow-up release. The public product supports recording, multilingual transcription, and calendar-oriented organization. Commercial source code, private configuration, and internal product data are not included here.

