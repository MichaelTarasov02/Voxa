# Voxa privacy notes

Last updated: September 18, 2026. Covers the macOS 0.1.1 and Windows 0.2.0 beta downloads in this repository.

## What leaves your device

Voxa connects directly to OpenAI using your API key. It sends recordings for transcription and text for cleanup or translation. Selected-text translation sends the text you select. Your key is included as authentication for OpenAI requests.

This processing uses OpenAI's API and is subject to your agreement with OpenAI and its data policies. Voxa doesn't promise zero retention by OpenAI. Check your account's policies before sending confidential, regulated or other sensitive material.

Voxa doesn't operate a separate transcription server or include product analytics or telemetry. Downloading from GitHub and opening links to other services are subject to those services' own policies.

## What stays on your device

| Data | macOS | Windows |
| --- | --- | --- |
| API key | Keychain, service `com.voxa.app` | Credential Manager, target `Voxa/OpenAI` |
| History, audio and settings | `~/Library/Application Support/Voxa/` | `%LOCALAPPDATA%\Voxa` |

Recordings and transcripts are local files, not an encrypted Voxa vault. Your operating-system account, disk encryption and backup settings determine who else may access them. Device backups may retain copies after you delete them from the app.

## Retention and deletion

Use History to delete an entry and its saved audio. Audio retention is configurable. The Mac app also has a setting for keeping audio; the Windows beta retains failed recordings and favorites until you remove them yourself. Successful, non-favorite Windows recordings can expire under your retention setting. Expiring audio doesn't delete the transcript.

Cancelling an active recording discards it. Cancelling Windows API processing retains the recording for retry. A failed processing request may already have reached OpenAI and may still incur usage charges.

Uninstalling does not guarantee removal of history, recordings or stored credentials. For a full local reset: quit Voxa, delete its data folder, and remove its key from Keychain or Credential Manager. This also removes your retry audio, so export anything you want to keep first.

## Support and public issues

GitHub issues in this repository are public. Share reproduction steps rather than recordings or transcript contents. Never upload API keys or a full history file. The [security reporting instructions](SECURITY.md) explain how to report a suspected vulnerability privately.
