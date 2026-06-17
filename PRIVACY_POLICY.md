# Privacy Policy — ZeroTrace Chat

**Last updated: June 17, 2026**

ZeroTrace Chat ("the App") is developed and maintained by ZeroTrace ("we", "us", "our"). This Privacy Policy explains what data the App collects, how it is used, and your rights as a user.

---

## Summary

ZeroTrace Chat is built on a zero-knowledge, server-blind architecture. We do not collect, store, or process your personal data. Messages are encrypted on your device before transmission and can only be decrypted by the intended recipient.

---

## 1. Data We Do NOT Collect

We do not collect or store:

- Your name, email address, or phone number
- Account credentials (no accounts exist)
- Message content, attachments, or voice recordings
- Contact lists or address books
- Device identifiers (IMEI, advertising ID, etc.)
- Location data
- Usage analytics or behavioral data
- Crash reports sent to our servers

---

## 2. Data Stored On Your Device

All app data is stored locally on your device using IndexedDB within the Android WebView sandbox. This includes:

- Your cryptographic identity keypair (generated locally, never transmitted)
- Your PIN-protected encryption key (derived via PBKDF2, never leaves the device)
- Conversation history and received messages
- Saved contacts (public keys only)

This data is accessible only to the App and is protected by your device's security model. You can delete all local data at any time by clearing the App's storage in Android Settings, or by uninstalling the App.

---

## 3. Encryption

All messages are encrypted end-to-end using **NaCl Box** (TweetNaCl.js) before leaving your device. The encryption keys are generated and stored locally. We have no technical ability to read your messages.

Key derivation for PIN unlock uses **PBKDF2** via the Web Crypto API with a random salt stored on-device.

---

## 4. Third-Party Services

ZeroTrace Chat uses minimal third-party infrastructure for connection setup only:

### PeerJS (WebRTC Signaling)
- Used to establish direct peer-to-peer connections between devices
- Handles connection metadata (peer IDs) only — never message content
- PeerJS signaling servers do not store messages
- See [PeerJS Privacy](https://peerjs.com) for their terms

### ntfy.sh (Push Relay)
- Used to deliver encrypted push signals to wake the recipient's app
- Only encrypted, opaque payloads are transmitted — ntfy.sh cannot read content
- No user identifiers are sent to ntfy.sh beyond a randomly generated topic string
- See [ntfy.sh Privacy Policy](https://ntfy.sh/privacy) for their terms

Neither service receives your identity keypair, message content, or any personally identifiable information.

---

## 5. Permissions

The App requests the following Android permissions at runtime:

| Permission | Purpose |
|---|---|
| `INTERNET` | WebRTC P2P connection and ntfy.sh relay |
| `ACCESS_NETWORK_STATE` | Detect connectivity before establishing a connection |
| `RECORD_AUDIO` | Send encrypted voice messages |
| `MODIFY_AUDIO_SETTINGS` | Route audio correctly during voice message playback |
| `CAMERA` | Capture images for encrypted sharing |
| `READ_MEDIA_IMAGES` / `READ_EXTERNAL_STORAGE` | Pick images from your gallery for encrypted sharing |

No permission is used for advertising, analytics, or tracking purposes.

---

## 6. Children's Privacy

ZeroTrace Chat is not directed at children under the age of 13. We do not knowingly collect any information from children. If you believe a child has used this App, please contact us so we can take appropriate action.

---

## 7. Changes to This Policy

We may update this Privacy Policy from time to time. Changes will be reflected by updating the "Last updated" date at the top of this document. Continued use of the App after changes constitutes acceptance of the updated policy.

---

## 8. Contact

If you have questions or concerns about this Privacy Policy, please contact us:

**Email:** privacy@zerotrace.io  
**GitHub:** [https://github.com/zerotrace/zerotrace-chat/issues](https://github.com/zerotrace/zerotrace-chat/issues)

---

*ZeroTrace Chat — No accounts. No servers. No traces.*
