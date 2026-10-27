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


## GraveMint integration (in progress)

The website now includes a guarded GraveMint mint panel for the Recruitment Badges drop:
- Drop: https://gravemint.io/mint/rdzucb
- SDK: `@solanadeads/gravemint@1.3.0`, loaded as a browser ESM module.
- The panel connects an injected Solana wallet, reads the collection and active phase, checks wallet eligibility, and only attempts the embedded mint flow when GraveMint reports `capabilities.supportedBySurface === true`.
- Unsupported mechanics or missing active phases direct collectors to the official GraveMint page.
- A browser-side publishable key is required. The key is intentionally public, but GraveMint must allow-list the exact website origin and scope the key to this collection with mint permission.

### Configure before testing

1. In `index.html`, replace `PASTE_GM_PUB_KEY_HERE` in `GM_CONFIG.apiKey` with the `gm_pub_` key GraveMint issued for collection `rdzucb`.
2. Ask GraveMint to allow-list every origin used by this site (including `https://obideft.github.io` and any custom domain or preview origin).
3. Confirm the key has the required collection scope and mint permission.
4. Test with a wallet and a small/appropriate mint on the live drop; verify the transaction on Solscan and confirm the NFT in the wallet.

**Never put a `gm_live_` secret key in `index.html` or any other browser-delivered file.** A `gm_pub_` key is designed for browser use and relies on origin allow-listing. The embedded mint path only supports the mechanics GraveMint explicitly marks as supported; otherwise the official drop page is the fallback. This front-end alone does not provide a secure one-spin-per-wallet lottery or guarantee that a particular rarity is minted. GraveMint decides the actual NFT/phase outcome.
