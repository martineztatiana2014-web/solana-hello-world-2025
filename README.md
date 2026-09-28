# Solana Hello World App

![Solana Hello World Screenshot](https://alchemyapi-res.cloudinary.com/image/upload/v1763746952/Screenshot_2025-11-21_at_9.42.27_AM_efycbi.png)

This is a minimal Next.js demo DApp for interacting with a Solana on-chain "Hello World" program using a browser wallet (Phantom-compatible) and an RPC proxy route.

## Features

- Connect to a Solana wallet from the browser
- Send a "ping" transaction to your Hello World program
- View transaction signature and open it in Solana Explorer
- Display on-chain program logs returned after confirmation
- Proxy JSON-RPC requests through `src/app/api/rpc/route.ts` so RPC URLs are kept server-side

## Requirements

- Node.js (current LTS recommended)
- A Solana wallet extension (for example, Phantom)
- A deployed Solana program ID for `NEXT_PUBLIC_PROGRAM_ID`
- At least one configured RPC endpoint environment variable

## Environment variables

The app reads environment variables used by:

- `src/app/page.tsx`
  - `NEXT_PUBLIC_PROGRAM_ID` (required)
- `src/app/api/rpc/route.ts`
  - `ALCHEMY_API_URL` (fallback/default upstream)
  - `ALCHEMY_API_URL_SOLANA_DEVNET` (optional chain-specific)
  - `ALCHEMY_API_URL_SOLANA_MAINNET` (optional chain-specific)
  - `ALCHEMY_API_URL_SOLANA_TESTNET` (optional chain-specific)

Create `.env.local` in the repository root, for example:

```bash
NEXT_PUBLIC_PROGRAM_ID=<your_program_public_key>
ALCHEMY_API_URL_SOLANA_DEVNET=<your_devnet_rpc_url>
# Optional fallback used when no chain-specific URL exists:
# ALCHEMY_API_URL=<your_default_rpc_url>
```

## Local development

Install dependencies:

```bash
npm install
```

Start the dev server:

```bash
npm run dev
```

Then open [http://localhost:3000](http://localhost:3000).

## Available scripts

From `package.json`:

- `npm run dev` — start development server
- `npm run build` — create production build
- `npm run start` — run production server
- `npm run lint` — run ESLint

## Notes about network routing

The frontend currently calls `/api/rpc` without an `x-chain` header (`src/app/page.tsx`), so the proxy defaults to `solana-devnet` (`src/app/api/rpc/route.ts`).
