# SOVEREIGN-OS

SOVEREIGN-OS is a fully self-sovereign, browser-native identity and governance system. It combines cryptography, local AI, and peer-to-peer networking to let users experiment with digital sovereignty without servers, blockchains, or external authorities.

Everything runs in a single HTML file — no build tools, no npm, no cloud.

---

## Features

- **Single-file sovereign identity** — Generate your decentralized identifier (DID) and Ed25519 keypair entirely in the browser using the Web Crypto API.
- **Shamir 3-of-5 recovery** — Safely split and recover your key across five shares without trusting any single party.
- **Entropy-based identity creation** — Mouse movement, keystrokes, and a meaningful seed word feed a Keccak-f[1600] sponge until your identity is ready.
- **Local AI Witness** — Connect a local Ollama model tied to your birth entropy to serve as a cryptographic personal witness.
- **Peer-to-peer governance** — Gossip pseudonymous birth certificates, messages, proposals, and valuations with peers via WebRTC.
- **Mini local DAOs** — Experiment with small-scale governance structures and on-chain-style proposals among trusted peers.
- **Asset Valuation** — Register and value sovereign assets with a local ledger.
- **Encrypted memory store (SCMP)** — Encrypt and retrieve structured documents, tied to your identity.
- **Architecture parser** — Paste and parse system architecture descriptions via local Ollama.
- **Sovereign token engine (CST)** — Initialize a local wallet, transfer tokens, and create time-locked capsules.
- **Solidity contract auditor** — AI-powered vulnerability analysis of Solidity contracts via Ollama, plus instant static pattern scans.
- **Adversarial testing (RRTK)** — Fuzz your JSONFlow workflows and run attack simulations against your own contracts.
- **Invariant engine** — Define and verify mathematical invariants over your identity, keys, and ledger state.
- **Feed / Mailbox** — Sign and send messages peer-to-peer with file attachment support.
- **Dev Tools** — Built-in debugger, test runner, auto-fix engine, and dependency scanner to inspect and maintain the system itself.
- **Offline capable** — After first load, everything runs without a server, blockchain, oracle, or token.
- **Fully forkable** — Strip, harden, or extend as you see fit. One file, no lock-in.

---

## How to Use

1. Save this HTML file somewhere safe (`Ctrl+S` or right-click → Save As).
2. Open it in a modern browser (Chrome, Edge, or Firefox). Offline use works after the first load.
3. Complete the **Birth Certificate** flow — collect entropy, generate your identity, and create your 5 Shamir shares.
4. **Never lose your 5 Shamir shares** — they are your only recovery path if your browser data is wiped.
5. *(Optional)* Run Ollama locally (`ollama serve`) and connect the AI Witness tab to bind a local model to your birth entropy.
6. *(Optional)* Open the **Dev Tools** tab to run diagnostics, verify all engines are healthy, and audit for external dependencies.

---

## Dev Tools

The **⬡ Dev Tools** tab provides four built-in maintenance tools:

- **Debug** — Scans all global engine modules, critical DOM elements, IndexedDB access, and Web Crypto availability. Lists any issues found and populates the fix queue automatically.
- **Test** — Smoke-tests every engine (Identity, Entropy, Crypto, Shamir, Network, Storage, Tokens, Governance) individually or all at once. Results appear as color-coded pass/fail badges.
- **Fix** — Attempts to repair detected issues: re-initialises broken engines, validates IndexedDB state, and re-binds event listeners.
- **Remove Dependencies** — Scans for and removes any external script, stylesheet, or image references to enforce the offline-first guarantee. Also audits the Content Security Policy for unsafe directives.

A live **Error Console** panel captures `console.error`, `console.warn`, unhandled exceptions, and promise rejections as they occur.

---

## Security Notes

- This is an experiment and **not audited** for high-stakes secrets.
- IndexedDB is not encrypted at rest. Local device attacks can read stored data.
- WebRTC is end-to-end encrypted between peers, but metadata (IP addresses, peer graph) may briefly leak to STUN/TURN relay servers.
- Closing the tab before exporting your Shamir shares **will permanently lose your key**. There is no recovery without them.
- The CSP meta tag uses `unsafe-inline` for scripts because all JavaScript is inline in a single-file app. In a deployed context, extract scripts to separate files and use nonces or hashes.
- Use only for personal, experimental, or research purposes until the codebase has been independently audited.

---

## Architecture

SOVEREIGN-OS is a single HTML file (~6,200 lines) with zero external runtime dependencies. All engines are self-contained IIFE modules exposed on `window`:

| Module | Role |
|---|---|
| `KeccakEngine` | Keccak-f[1600] hash primitive, entropy collection |
| `ShamirRecovery` | GF(256) Shamir secret sharing, 3-of-5 |
| `AIWitness` | Ollama integration, witness packet signing |
| `P2PNet` | WebRTC peer mesh, WebSocket relay, BroadcastChannel |
| `FeedMailbox` | Signed message feed, file attachments |
| `SCMPEngine` | Encrypted memory store |
| `ParserEngine` | Architecture document parser via Ollama |
| `TokenEngine` | CST token wallet, transfer, capsule |
| `Governance` | Proposal submission, voting, state root |
| `Assets` | Asset registration and valuation |
| `SolAudit` | Solidity static scan + AI audit |
| `AttackEngine` | Adversarial fuzzing, pattern attack simulation |
| `SearchEngine` | Full-text search across all stored data |
| `InvariantEngine` | Mathematical invariant verification suite |
| `DevTools` | Debug, test, fix, dependency scanner |

---

## Browser Compatibility

| Browser | Status |
|---|---|
| Chrome / Edge 120+ | ✓ Full support |
| Firefox 120+ | ✓ Full support |
| Safari 17+ | ✓ Supported (Ed25519 requires Safari 17+) |
| Mobile browsers | ⚠ Functional, not optimised for small screens |

---

## License

See `LICENSE.md` for details. SOVEREIGN-OS is **free for personal, educational, and research use**. Businesses and government entities require a separate commercial license.

---

## Authors

- XheCarpenXer
- James Brian Chapman
- vessel
