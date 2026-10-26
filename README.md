# FROGINALS SWAMP SPIN

A standalone, front-end collectible wheel prototype for the FROGINALS community.

## Run locally
Open `index.html` in a modern browser, or enable GitHub Pages in repository settings to publish the static prototype.

## Prototype behavior
- Animated prize wheel with visible drop rates.
- Welcome spin and collectible inventory stored in this browser's `localStorage`.
- Collection gallery shows locked and unlocked rewards.
- Duplicate rewards are allowed in the demo.

## Important security note
This is **not production-secure**. Browser storage can be cleared or modified, and the demo's random selection runs client-side. Before public launch or Discord integration, move reward selection to a trusted server, use cryptographically secure randomness, and persist spins/rewards in a database with an atomic one-spin-per-user constraint. The animation must only reveal a server-selected result.

Rewards are cosmetic demo items only; no NFTs, tokens, tradable currency, or real-world value are issued. Keep this project separate from the existing FROGINALS production website and authentication.
