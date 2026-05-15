# PandaGenie SDK Provider Template

This repository is a standalone Android template for apps that want to expose callable capabilities to PandaGenie or any trusted AI assistant that integrates the PandaGenie SDK.

Use it when you want to build a provider app that can:

- Publish a machine-readable capability manifest.
- Receive calls from verified AI assistants.
- Expose Activity, Service, ContentProvider, and BroadcastReceiver based examples.
- Validate caller identity through PandaGenie SDK registry checks.
- Return structured results that assistants can pass back to users.

## Project Structure

```text
.
├── app/                         # Demo provider application
│   ├── src/main/AndroidManifest.xml
│   └── src/main/java/...        # Activity, Service, Provider, Broadcast examples
├── build.gradle                 # Root Gradle configuration
├── settings.gradle              # Android project settings
└── README.md                    # This guide
```

## Quick Start

1. Open this project in Android Studio.
2. Replace `applicationId`, package names, app label, and exported capabilities with your own app information.
3. Register your app at the PandaGenie SDK portal:
   [https://pandagenie.ai/sdk](https://pandagenie.ai/sdk)
4. Submit your release package name and SHA-256 signing certificate fingerprint.
5. Build a release APK and install it on a device that also has PandaGenie installed.

## Dependency

The template is written for the public SDK artifact:

```gradle
dependencies {
    implementation "ai.rorsch.pandagenie:pandagenie-sdk:0.1.0-preview"
}
```

If you are developing the SDK locally, replace the dependency with your local module or composite build.

## Signing Fingerprint

Use one of the following commands to get the release signing SHA-256 fingerprint:

```bash
apksigner verify --print-certs app-release.apk
```

```bash
keytool -list -v -keystore release.jks -alias your_alias
```

Submit the SHA-256 value as 64 hexadecimal characters. Colons are accepted by the portal and normalized automatically.

## Demo Capabilities

The demo app includes examples for:

- Opening the app to a target screen with text passed by the caller.
- Returning a capability manifest through a ContentProvider.
- Handling a callable Service request.
- Handling a BroadcastReceiver request.

These examples are intentionally small, so you can replace them with your own business logic.

## Related Links

- Website: [https://pandagenie.ai](https://pandagenie.ai)
- SDK Portal: [https://pandagenie.ai/sdk](https://pandagenie.ai/sdk)
- SDK Source: [https://github.com/Rorschach123/PandaGenieSDK](https://github.com/Rorschach123/PandaGenieSDK)
- Module Source: [https://github.com/Rorschach123/PandaGenie-Source](https://github.com/Rorschach123/PandaGenie-Source)
- Discord: [https://discord.gg/pandagenie](https://discord.gg/pandagenie)
