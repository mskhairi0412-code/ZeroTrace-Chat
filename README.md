# ZeroTrace Chat

**Peer-to-peer encrypted messaging — no servers, no accounts, no traces.**

ZeroTrace Chat is a privacy-first Android messaging app built on WebRTC and NaCl Box cryptography. Messages are encrypted end-to-end between devices and never stored on any server. Your identity is a self-sovereign Ethereum-compatible keypair generated entirely on your device.

---

## Features

- **End-to-end encrypted** — NaCl Box (TweetNaCl) encryption on every message
- **P2P delivery** — messages travel directly between peers via PeerJS WebRTC
- **Zero server storage** — ntfy.sh relay used only for signaling, never for message storage
- **Self-sovereign identity** — Ethereum-compatible keypair, no account registration
- **Voice messages** — recorded and encrypted before transmission
- **Image sharing** — chunked transfer with encryption
- **Encrypted typing indicators** — even metadata is protected
- **PIN / biometric unlock** — PBKDF2-derived key, 6-digit auto-submit PIN
- **WhatsApp-style UI** — swipe-to-reply, radial reactions, streak counters, haptic feedback
- **No ads. No tracking. No cloud.**

---

## Tech Stack

| Layer | Technology |
|---|---|
| Android wrapper | Java + WebView (API 24+) |
| Encryption | NaCl Box via TweetNaCl.js |
| P2P transport | PeerJS (WebRTC) |
| Push relay | ntfy.sh (signaling only) |
| Identity | Ethereum-compatible ECDSA keypair |
| Key derivation | PBKDF2 (Web Crypto API) |
| Storage | IndexedDB (on-device only) |

---

## Package Info

| Field | Value |
|---|---|
| Package ID | `io.zerotrace.chat` |
| Min SDK | Android 7.0 (API 24) |
| Target SDK | API 36 |
| Version | 1.0.2 |

---

## Permissions

| Permission | Reason |
|---|---|
| `INTERNET` | P2P WebRTC connection and ntfy.sh relay |
| `ACCESS_NETWORK_STATE` | Connection status checks |
| `RECORD_AUDIO` | Voice messages |
| `MODIFY_AUDIO_SETTINGS` | Audio routing during calls |
| `CAMERA` | Image capture for sharing |
| `READ_MEDIA_IMAGES` / `READ_EXTERNAL_STORAGE` | Image picking from gallery |

All permissions are requested at runtime. No permission is used for analytics or tracking.

---

## Privacy

ZeroTrace Chat is designed to be **server-blind**. The relay infrastructure (PeerJS signaling, ntfy.sh) handles connection setup only — it never sees message content. All encryption and decryption happens on-device using the Web Crypto API and TweetNaCl.js before any data leaves your phone.

See [PRIVACY_POLICY.md](./PRIVACY_POLICY.md) for the full policy.

---

## Building

```bash
# Clone the repo
git clone https://github.com/zerotrace/zerotrace-chat.git
cd zerotrace-chat

# Open in Android Studio and sync Gradle
# or build from CLI:
./gradlew assembleRelease
```

Requires Android Studio Hedgehog or later, AGP 8.4.2+, Gradle 8.6+.

---

## Project Structure

```
app/
├── src/main/
│   ├── AndroidManifest.xml
│   ├── assets/
│   │   └── mobile.html        # Main app (HTML/JS/CSS)
│   ├── java/io/zerotrace/chat/
│   │   └── MainActivity.java  # WebView wrapper
│   └── res/
│       ├── mipmap-*/          # App icons
│       └── values/
│           └── strings.xml
└── build.gradle.kts
```

---

## ZeroTrace Ecosystem

ZeroTrace Chat is part of a broader suite of privacy-first apps:

- [ZeroTrace Vault](https://github.com/zerotrace/zerotrace-vault) — AES-256 encrypted file storage
- [ZeroTrace Cam](https://github.com/zerotrace/zerotrace-cam) — Privacy camera with EXIF stripping
- [ZeroTrace Maps](https://github.com/zerotrace/zerotrace-maps) — P2P encrypted location sharing

---

## License

This project is licensed under the [GNU Affero General Public License v3.0](./LICENSE) (AGPL-3.0).

---

## Contact

Built by the ZeroTrace team. For security disclosures, open a private GitHub issue or email **security@zerotrace.io**.
