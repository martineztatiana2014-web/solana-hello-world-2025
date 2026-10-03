# Solana Hello World App

![Solana Hello World Screenshot](https://alchemyapi-res.cloudinary.com/image/upload/v1763746952/Screenshot_2025-11-21_at_9.42.27_AM_efycbi.png)


This is a minimal Next.js demo DApp for interacting with a Solana on-chain "Hello World" program using the Phantom wallet and the Alchemy RPC proxy. Users can connect their Solana wallet (e.g., Phantom), send a simple "ping" transaction to their deployed Solana program on **devnet**, and view the transaction signature and program logs directly in the app UI. 

**Features:**
- Connect to your Solana wallet (Phantom or compatible)
- Send a transaction to your Hello World program on Solana devnet
- View transaction signature and link to Solana Explorer
- See logs output by your program
- All RPC requests are securely proxied via a Next.js API route to protect your Alchemy API key

## Required configuration

Create `.env.local` in the project root:

```bash
NEXT_PUBLIC_PROGRAM_ID=<YOUR_SOLANA_PROGRAM_PUBLIC_KEY>
ALCHEMY_API_URL_SOLANA_DEVNET=<YOUR_ALCHEMY_SOLANA_DEVNET_RPC_URL>
```

Optional fallback env vars supported by the RPC proxy route:

```bash
ALCHEMY_API_URL=<DEFAULT_RPC_URL>
ALCHEMY_API_URL_SOLANA_MAINNET=<MAINNET_RPC_URL>
ALCHEMY_API_URL_SOLANA_TESTNET=<TESTNET_RPC_URL>
```

### What each value is used for

- `NEXT_PUBLIC_PROGRAM_ID`: Program public key invoked by the frontend ping transaction.
- `ALCHEMY_API_URL_SOLANA_DEVNET`: Upstream Solana devnet RPC used by `POST /api/rpc`.
- `ALCHEMY_API_URL`: Generic fallback if a chain-specific URL is not set.

## Run locally

```bash
npm install
npm run dev
```

Then open `http://localhost:3000`.

## Scripts

- `npm run dev` - Start the Next.js development server
- `npm run build` - Build for production
- `npm run start` - Start the production server
- `npm run lint` - Run ESLint

_Note:_ This app is meant for demo/educational purposes and uses client-side wallet connections only. See the source code for details on how transactions are built and sent with `@solana/web3.js` and how the Alchemy API proxy is implemented.