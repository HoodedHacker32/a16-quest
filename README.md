# A16 QUEST — Encrypted Savings Vault ⚡

A mobile-first savings tracker for one mission: the **[GIGABYTE A16 16" Gaming Laptop](https://www.currys.ie/products/gigabyte-a16-16-gaming-laptop-intel-core-i7-rtx-5050-1-tb-ssd-10286164.html)** (Intel i7-13620H · RTX 5050 8GB GDDR7 · 16GB DDR5 · 1TB SSD · 16″ 165Hz) — **€1,299** at Currys IE.

## Security model

- All savings data is encrypted **on-device** with **AES-256-GCM** before it leaves the browser.
- The key is derived from your password via **PBKDF2-SHA256 (310,000 iterations)** with a random salt.
- The encrypted blob syncs through a **GitHub Gist** (reads via `gist.githubusercontent.com`, writes via the Gist API) — only ciphertext is ever stored in the cloud.
- The gist-scoped write token also roams **inside the encrypted blob**, so a new device only needs the password — it inherits sync access on first unlock.
- Wrong password → GCM authentication fails → access denied. No password, no data.
- A `localStorage` copy of the (still encrypted) blob serves as the offline fallback.
- ⚠️ There is **no recovery**. Lose the password and the vault stays locked forever.

## Features

- Animated progress ring + milestone progress bar with 25/50/75% ticks
- Achievements, confetti, haptic feedback, goal-reached victory screen
- Savings pace + projected completion date (ETA)
- Deposits **and** withdrawals, with notes and a full save log
- Editable goal price, password change, JSON export, vault wipe
- Installable PWA — works offline, add it to your home screen
- 100% static: just open `index.html` over HTTPS (Web Crypto requires a secure context)

## Run locally

Any static server works:

```
npx serve .
```

(then open the `localhost` URL — `localhost` counts as a secure context).
