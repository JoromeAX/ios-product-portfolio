# Cleaner — Phone Space Manager

[View on the App Store](https://apps.apple.com/us/app/cleaner-phone-space-manager/id6761115303)

## Product context

Cleaner is a consumer iPhone utility designed to help users understand and manage storage, review large or redundant media, organize contacts, compress photos, and keep selected personal content in protected local storage.

The product combines several privacy-sensitive system integrations in a single guided experience. Its core challenge is not only processing a large photo library, but also making destructive actions understandable and keeping permission-dependent flows reliable.

## My scope

As the iOS Developer responsible for mobile implementation, my work included:

- translating product flows and Figma designs into the SwiftUI application;
- structuring navigation, feature state, reusable UI components, and service boundaries;
- implementing photo-library authorization, asset loading, grouping, selection, and deletion workflows;
- implementing photo compression and output handling;
- building contact review and duplicate-management flows;
- implementing protected local media storage and passcode-based access;
- integrating subscriptions and release configuration;
- preparing the initial App Store delivery and supporting follow-up product iterations.

## Engineering focus

### Permission-aware media workflows

Photo-library access can be full, limited, denied, or changed outside the app. The UI and feature state therefore need to treat authorization as a changing dependency rather than a one-time onboarding result.

The implementation separates library operations from screen state, allowing permission, loading, selection, and destructive-action states to be handled explicitly.

### Working with large libraries

Media-heavy screens need to avoid eagerly loading full-resolution assets. The product uses identifier-based models, thumbnail-oriented loading, asynchronous operations, and progressive state updates so that the UI remains responsive while the library is inspected.

### Safe destructive actions

Cleaning products must make scope and consequences visible. Selection summaries, grouped review screens, confirmation steps, and success states are used to keep users in control before changes are committed to the photo library or contacts.

### Product monetization

Subscription state is integrated into the launch and feature-access flow instead of being treated as an isolated screen. The implementation accounts for available plans, purchase and restore actions, entitlement refresh, and a usable fallback when product information is unavailable.

## Technology

Swift, SwiftUI, Combine, Swift Concurrency, PhotoKit, PhotosUI, AVFoundation, Contacts, Core Image, StoreKit, Apphud, Lottie, and App Store Connect.

## Public outcome

The product shipped to the App Store with subscription monetization and multilingual support. Its public listing and release history are linked above; internal source code, analytics, and proprietary assets are intentionally excluded from this case study.

