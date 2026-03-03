# Serial Console

A privacy-first browser-based serial terminal with P2P remote sharing and file transfer.

## Features

- **Serial Terminal** — Connect to serial devices from Chrome/Edge (89+) with configurable baud rate, data bits, stop bits, parity, and flow control.
- **Dual P2P Sharing Modes**:
  - **Private Mode** — Manual SDP exchange via encrypted invite links. No servers touched. Uses AES-GCM encryption (Web Crypto API) for invite data.
  - **Quick Connect** — Encrypted MQTT signaling via [Trystero](https://github.com/dmotz/trystero). MQTT brokers see only encrypted blobs. One-step room code sharing.
- **Connection Approval** — Host accepts or rejects incoming peers before data is shared.
- **Per-Peer Permissions** — Toggle read/write access per connected peer.
- **Config Transfer** — Upload files or paste configuration text, then send line-by-line to the serial device with configurable delays, progress tracking, pause/cancel, and wait-for-prompt.
- **P2P File Sharing** — Separate tab for browser-to-browser file transfer with drag-and-drop, progress tracking, and download.
- **DTR/RTS Control** — Toggle serial signals directly from the toolbar.
- **Hex View** — Display received data as hex bytes.
- **Timestamps** — Toggle timestamp prefixes on terminal output.
- **Command History** — Arrow Up/Down to navigate previously sent commands.
- **Log Download** — Save the full terminal session as a text file.
- **IP Privacy** — Optional TURN server configuration to relay traffic and hide peer IPs.

## Privacy

- **Private Mode** makes zero requests to third-party servers (only Google STUN for NAT traversal).
- **Quick Connect** encrypts all signaling data with a shared password before sending through MQTT brokers.
- **Auth and session tokens are separate mechanisms**: one-time invite auth keys are consumed on first use; persistent session tokens (SHA-256 derived) allow reconnection.
- **Optional TURN relay** hides IP addresses from peers when a self-hosted TURN server is configured.

## How It Works

The entire application is a single static HTML file (`docs/index.html`) with no build step and no server required. Trystero is loaded dynamically from CDN only when Quick Connect mode is used. Private Mode runs entirely offline (after the page loads).

## Deployment

The site is served via GitHub Pages from the `docs/` folder:

1. Go to **Settings > Pages**
2. Set source to **Deploy from a branch**
3. Set branch to `main` and folder to `/docs`
4. (Optional) Configure a custom domain

## License

[MIT](LICENSE)
