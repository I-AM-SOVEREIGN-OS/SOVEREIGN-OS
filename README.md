# I AM SOVEREIGN-OS
## Sovereign OS

### Single-file sovereign identity ritual for the browser.

Wiggle your mouse. Type a word that means something to you. Watch the Keccak sponge fill with entropy until it says "enough".  

One Ed25519 keypair is born.  
One decentralized identifier (DID) is minted locally.  
Your private key is Shamir-split (3-of-5) so you can recover it without trusting anyone.  
Everything stays in your browser — IndexedDB, memory, nowhere else.

### Tabs let you:
- Talk to a local Ollama model that knows your birth entropy and calls itself your "AI Witness"
- Gossip pseudonymous birth certificates, short messages, governance proposals, and asset valuations with whoever you manually connect to via WebRTC
- Pretend you have a tiny local DAO that only you (and your connected friends) care about

# No server. No blockchain. No oracle. No token. No permission ever asked.

### How to use
1. Save this entire HTML file somewhere safe (Ctrl+S or right-click → Save As)
2. Open it in a modern browser (Chrome/Edge/Firefox, offline is fine after first load)
3. Complete the Birth Certificate flow
4. Never lose your 5 Shamir shares — they are your only way back
5. (Optional) Run Ollama locally (`ollama serve`) and connect the Witness tab

### Security reality check
- This is an experiment, not audited security software.
- IndexedDB is convenient but **not encrypted at rest** on disk — browser-level attacks or device compromise can read it.
- WebRTC connections are end-to-end encrypted but metadata (IP addresses, connection graph) leaks to peers and (briefly) to the public STUN/TURN servers PeerJS uses by default.
- If you close the tab before exporting/sharing recovery shares, your key is gone forever.
- Use only for things that matter to *you*, not for high-stakes secrets yet.

# Fork, strip, harden, or just keep one copy forever.  
# Your call.

## vessel
### James Brian Chapman  
###  XheCarpenXer
