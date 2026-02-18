# SOVEREIGN-OS

SOVEREIGN-OS is a fully self-sovereign, browser-native identity and governance system. It combines cryptography, local AI, and peer-to-peer networking to let users experiment with digital sovereignty without servers, blockchains, or external authorities.

## Features

- **Single-file sovereign identity**: Generate your decentralized identifier (DID) and Ed25519 keypair entirely in the browser.
- **Shamir 3-of-5 recovery**: Safely recover your key without trusting anyone.
- **Entropy-based identity creation**: Wiggle your mouse and type a meaningful word to feed a Keccak sponge until your identity is ready.
- **Local AI Witness**: Connect a local Ollama model tied to your birth entropy to serve as a personal witness.
- **Peer-to-peer governance**: Gossip pseudonymous birth certificates, messages, proposals, and valuations with friends via WebRTC.
- **Mini local DAOs**: Experiment with small-scale governance structures among trusted peers.
- **Offline capable**: After first load, everything runs without a server, blockchain, oracle, or token.
- **Fully forkable**: You can strip, harden, or extend the software as you see fit.

## How to Use

1. Save this HTML file somewhere safe (Ctrl+S or right-click → Save As).
2. Open it in a modern browser (Chrome/Edge/Firefox). Offline use works after the first load.
3. Complete the Birth Certificate flow.
4. Never lose your 5 Shamir shares — they are your only way back.
5. (Optional) Run Ollama locally (`ollama serve`) and connect the Witness tab.

## Security Notes

- This is an experiment and **not audited** for high-stakes secrets.
- IndexedDB is not encrypted at rest. Local attacks can read stored data.
- WebRTC is end-to-end encrypted, but metadata (IP addresses, peer graph) may leak briefly to STUN/TURN servers.
- Closing the tab before exporting shares **will permanently lose your key**.
- Use only for personal or experimental purposes until fully hardened.

## License

See `LICENSE.md` for details. SOVEREIGN-OS is **free for personal, educational, and research use**. Businesses and government entities require a separate commercial license.

## Authors

- XheCarpenXer  
- James Brian Chapman  
- vessel
