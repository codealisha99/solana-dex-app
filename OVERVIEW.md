# Solana DEX App Overview

## What This Project Does

Solana DEX App is a Next.js application for signing in with Google, viewing token data, opening a user dashboard, and preparing token swap actions on Solana. The app combines a web dashboard, authentication, database-backed user records, and Solana SDK integrations.

## Main Features

- Google sign-in through NextAuth.
- Dashboard page for signed-in users.
- Token list and swap UI.
- API routes for auth, token data, and swap requests.
- Prisma-backed database layer for user and provider metadata.
- Solana Web3 and SPL Token libraries for blockchain interaction.

## Technology Stack

- **Next.js 14**: App Router, API routes, server rendering, and production build.
- **React 18**: Page and component UI.
- **TypeScript**: Typed application code.
- **Tailwind CSS**: Styling and layout.
- **NextAuth**: Google OAuth session handling.
- **Prisma**: Database schema, migrations, and client access.
- **PostgreSQL**: Production database target.
- **Solana Web3.js**: Wallet, public key, and transaction primitives.
- **Solana SPL Token**: Token-related helpers.
- **Axios**: HTTP requests where needed.

## Application Structure

- `app/page.tsx`: Main landing page.
- `app/dashboard/page.tsx`: Authenticated dashboard.
- `app/components`: Reusable UI pieces like app bar, token list, swap form, and profile card.
- `app/api/auth/[...nextauth]/route.ts`: NextAuth route.
- `app/api/tokens/route.ts`: Token API endpoint.
- `app/api/swap/route.ts`: Swap API endpoint.
- `app/lib`: Auth, constants, and token helpers.
- `app/db`: Prisma client setup.
- `prisma/schema.prisma`: Database schema.
- `prisma/migrations`: Database migration history.

## Data Flow

1. A user opens the app and signs in with Google.
2. NextAuth creates a session and stores user/account data through Prisma.
3. The frontend loads the dashboard and token UI.
4. Token data is requested through the app API layer.
5. Swap actions are started from the UI and routed through the swap endpoint.
6. Solana libraries provide the primitives needed for token and transaction work.

## Database Model

The Prisma schema stores authentication-related data, including users, accounts, sessions, and verification tokens. It also includes provider metadata used by the app to connect Google identity with local records.

## Current State

The project has the right foundation for a DEX-style app: auth, dashboard, token UI, Prisma, and Solana SDK wiring. The next step is making swaps production-grade by adding wallet connection, quote providers, transaction simulation, signing, submission, and confirmation states.
