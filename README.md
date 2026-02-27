# Serial Console

A browser-based serial terminal using the Web Serial API with built-in P2P remote sharing.

## Features

- **Serial Terminal** -Connect to serial devices directly from Chrome/Edge (89+) with configurable baud rate, data bits, stop bits, parity, and flow control.
- **Remote Sharing** -Share your serial session with others over WebRTC using PeerJS. Peers connect via a 6-character room code.
- **Connection Approval** -Host must accept or reject incoming peer connections before any data is shared.
- **Per-Peer Permissions** -Individually toggle read/write access for each connected peer.
- **Session Resilience** -Auto-reconnect with exponential backoff on dropped connections. Sessions persist across page refresh.
- **Mobile Friendly** -Responsive layout optimized for remote peers on mobile devices.

## How It Works

The entire application is a single static HTML file (`docs/index.html`) with no build step, no dependencies to install, and no server required. WebRTC peer connections use public Google STUN servers for NAT traversal and PeerJS's free signaling server for connection setup.

## Deployment

The site is served via GitHub Pages from the `docs/` folder. To configure this on your own fork:

1. Go to **Settings > Pages**
2. Set source to **Deploy from a branch**
3. Set branch to `main` and folder to `/docs`
4. (Optional) Configure a custom domain

## License

[MIT](LICENSE)
