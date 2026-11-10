# DriftWatch dApp (`drift-watch-app`)

Web application for **DriftWatch** and **DriftGuard**: monitoring terms-of-service semantic drift with consensus-based AI verification on GenLayer Studionet.

- **Status**: Preview
- **Production URL**: [https://drift-watch-app.vercel.app](https://drift-watch-app.vercel.app) (also at [https://drift-watch-app-hyper-8cdf.vercel.app](https://drift-watch-app-hyper-8cdf.vercel.app))
- **Contract Repository**: [hypercybers99/drift-watch-genlayer](https://github.com/hypercybers99/drift-watch-genlayer)
- **Fixtures Repository**: [hypercybers99/drift-watch-fixtures](https://github.com/hypercybers99/drift-watch-fixtures)
- **License**: Hyper (hypercybers99)

---

## Active Studionet Contracts (Pinned V3)

- **Network**: GenLayer Studionet (Chain ID `61999`, RPC `https://studio.genlayer.com/api`)
- **Pinned Commit**: Contract repo HEAD `732614e3164c97958f303e6df188e1cd3bca56ad` (tag `dw-v3`)
- **DriftWatch Contract (V3)**: [`0xf8D23c16B5655bE7dF9897dC76C1C576d4c68F85`](https://explorer-studio.genlayer.com/address/0xf8D23c16B5655bE7dF9897dC76C1C576d4c68F85)
  - Source SHA-256: `2a2d3ebde7563ba146de73ead1cbdc3b0b52e82cfc60eddce3a595a5ea4c428c`
- **DriftGuard Contract (V3)**: [`0x4D2123ac8Ceb59967B2009ab7A261C290348abC4`](https://explorer-studio.genlayer.com/address/0x4D2123ac8Ceb59967B2009ab7A261C290348abC4)
  - Source SHA-256: `eb1b26aed095daf61ad1b94b1752d1636055965311543319d8fe214bc24863dc`

---

## Features

1. **Paper-Identity UI**: Warm paper tones, stamped verdict badges (`UNCHANGED`, `COSMETIC`, `NONE`, `MINOR`, `MATERIAL`, `REVIEW`), and explicit redline diff (`del`/`ins`).
2. **Watches Dashboard (`/app`)**: Summary stats cards, list of active terms watches, and one-click navigation.
3. **Watch Creator (`/app/create`)**: Pre-filled Acme Notes example, client-side canonical redlines hashing, and real-time on-chain comparison via `compute_redlines_hash`.
4. **Watch Detail & Diff (`/app/watch/:id`)**: Real-time elapsed transaction timer, clause breakdown, and Salami Attack Detection view comparing cumulative drift across revisions.
5. **DriftGuard Consumer Hub (`/app/guard`)**: One-click `pin`, `acknowledge`, and `repin`. Interactive `is_safe_for` playground with a **Change one character** button to demonstrate how downstream contracts prevent exploitation when terms drift.
6. **Evidence Center (`/app/evidence`)**: Complete pre-registered 8-fixture run table, 35-run robustness metrics (100% parse success on v2 & v5), and superseded deployments record.
7. **Operational Limits (`/app/limits`)**: Read directly from on-chain `get_limits`.
8. **Accessibility & Quality**: Fully tested with Vitest, 0 console errors, 0 serious/critical axe accessibility violations, and word budget compliance.

---

## Local Development & Testing

```bash
# Install dependencies
npm install

# Run automated unit tests (deployments sha256 match, error codes coverage, redlines hashing)
npm test

# Check word budgets (Landing <= 160 words, /app pages <= 40 words prose)
node scripts/check_word_budget.mjs

# Scan for banned words and secrets
python scripts/scan_banned_words.py
python scripts/scan_secrets.py

# Run headless console error and axe accessibility audit (dist must be built)
npm run build
node scripts/console_errors.mjs

# Execute Studionet throwaway key E2E verification
node scripts/e2e.mjs
```

---

## Manual MetaMask Verification

Follow the 8-step test script in [MANUAL_METAMASK_TEST.md](MANUAL_METAMASK_TEST.md) to test wallet connection, chain switching, watch creation, diff checking, and DriftGuard protection.
