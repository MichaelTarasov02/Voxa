# Voxa privacy notes

Last updated: September 24, 2026. Covers the macOS 0.3.1 and Windows 0.2.1 beta downloads in this repository.

## What leaves your device

Voxa connects directly to OpenAI using your API key. It sends recordings for transcription and text for cleanup or translation. Selected-text translation sends the text you select. Your key is included as authentication for OpenAI requests.

The text translator sends the entered text and target language. On Mac, it does so automatically after a typing pause. Requesting word alternatives sends the selected word, translated context and original source text; requesting another translation also sends the previous result. Relevant vocabulary may be included to preserve your preferred terminology. If Mac personalization is enabled, up to 12 saved spellings may also accompany a dictation with an explicitly selected Russian or English speech language. Auto-detected speech has no audio vocabulary prompt. Relevant saved aliases and any context you entered may accompany text cleanup for that dictation.

This processing uses OpenAI's API and is subject to your agreement with OpenAI and its data policies. Voxa doesn't promise zero retention by OpenAI. Check your account's policies before sending confidential, regulated or other sensitive material.

Voxa doesn't operate a separate transcription server or include product analytics or telemetry. Downloading from GitHub and opening links to other services are subject to those services' own policies.

## What stays on your device

| Data | macOS | Windows |
| --- | --- | --- |
| API key | Keychain, service `com.voxa.app` | Credential Manager, target `Voxa/OpenAI` |
| History, audio and settings | `~/Library/Application Support/Voxa/` | `%LOCALAPPDATA%\Voxa` |

Recordings and transcripts are local files, not an encrypted Voxa vault. Your operating-system account, disk encryption and backup settings determine who else may access them. Device backups may retain copies after you delete them from the app.

Mac also stores translation originals/results, dictionary entries, a personal vocabulary of names and spelling variants, and usage events locally. Personalization is off by default for new installs. If enabled, Voxa briefly observes the same focused editor after confirming a pasted dictation. Plausible name or term corrections may be saved automatically; a brief notice offers Undo. You can turn learning off and remove saved entries in Dictionary. Optional role and organization details are entered by you, not inferred from recordings. Usage events retain model names, timestamps, estimated costs, token counts and source-text/target-language fingerprints for deduplication. These fingerprints are hashes, not encrypted copies or a promise of anonymity.

## Retention and deletion

Use History to delete an entry and its saved audio. Audio retention is configurable. The Mac app also has a setting for keeping audio; the Windows beta retains failed recordings and favorites until you remove them yourself. Successful, non-favorite Windows recordings can expire under your retention setting. Expiring audio doesn't delete the transcript.

On Mac, delete translation text in History → Translations and remove learned entries in Dictionary. Deleting history does not remove independent usage totals or deduplication fingerprints. A full local reset removes these too.

Cancelling an active recording discards it. Cancelling Windows API processing retains the recording for retry. A failed processing request may already have reached OpenAI and may still incur usage charges.

Uninstalling does not guarantee removal of history, recordings or stored credentials. For a full local reset: quit Voxa, delete its data folder, and remove its key from Keychain or Credential Manager. This also removes your retry audio, so export anything you want to keep first.

## Support and public issues

GitHub issues in this repository are public. Share reproduction steps rather than recordings or transcript contents. Never upload API keys or a full history file. The [security reporting instructions](SECURITY.md) explain how to report a suspected vulnerability privately.
