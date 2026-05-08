# Polymarket Weather Bot

TypeScript bot for researching Polymarket weather markets with NWS forecast data, configurable thresholds, Kelly-style sizing, simulation state, and an optional dashboard.

> ⚠️ This project can interact with real Polymarket wallets. Start in simulation / read-only mode, use a dedicated low-balance wallet, and never commit private keys or seed phrases.

## Requirements

- Node.js 20+
- npm
- Internet access for NWS and Polymarket APIs

## Local setup

```bash
git clone https://github.com/MusicBoiyzzz/Polymarket-Weather-Bot.git
cd Polymarket-Weather-Bot
npm install
cp .env.sample .env
```

Edit `.env` locally. Do not commit `.env`.

Important fields:

```env
POLYMARKET_PRIVATE_KEY=
POLYMARKET_PROXY_WALLET_ADDRESS=
USE_PROXY_WALLET=false
SIGNATURE_TYPE=0
ENTRY_THRESHOLD=0.15
EXIT_THRESHOLD=0.45
MAX_TRADES_PER_RUN=5
MIN_HOURS_TO_RESOLUTION=2
LOCATIONS=nyc,chicago,miami,dallas,seattle,atlanta
```

Private-key guidance:

- Use a new wallet with limited funds.
- Do not reuse a main wallet.
- Do not paste seed phrases anywhere in this project.
- Keep `.env` out of Git.

## Build

```bash
npm run build
```

## Run

After configuring `.env`:

```bash
node dist/index.js
```

For development:

```bash
npx ts-node src/index.ts
```

## Dashboard

```bash
npm run serve-dashboard
```

or run the live dashboard helper:

```bash
npm run dev-live-dashboard
```

## Safety checklist before live trading

- Confirm the bot is using the expected wallet and proxy wallet settings.
- Check wallet balance and max trades before starting.
- Use conservative thresholds until behavior is verified.
- Review generated logs / simulation output before leaving the bot unattended.
- Treat forecasts and signals as inputs, not guaranteed outcomes.

## Project structure

- `src/index.ts` — main bot entrypoint.
- `src/config.ts` — environment/config parsing.
- `src/nws.ts` — weather forecast integration.
- `src/polymarket.ts` — Polymarket integration.
- `src/strategy.ts` — strategy logic.
- `src/simState.ts` — simulation state handling.
- `index.html` — dashboard.
