# Solana DEX App

A Solana token dashboard and swap interface built with Next.js, Prisma, NextAuth, and Solana Web3.

![Next.js](https://img.shields.io/badge/Next.js-14-black)
![React](https://img.shields.io/badge/React-18-61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6)
![Prisma](https://img.shields.io/badge/Prisma-2D3748)
![Solana](https://img.shields.io/badge/Solana-14F195)

## Project Preview

This app includes a landing page, Google sign-in, authenticated dashboard, token list, profile card, and swap interface.

Screenshots can be added in a future `screenshots/` folder:

- Landing page
- Dashboard
- Swap screen

## Features

- Google OAuth authentication with NextAuth.
- Prisma database layer for users, accounts, and sessions.
- Token list and swap-focused UI.
- Authenticated dashboard experience.
- Solana Web3 and SPL Token dependencies for blockchain integration.
- Production deployment guide and improvement roadmap.

## Tech Stack

- Next.js App Router
- React
- TypeScript
- Tailwind CSS
- NextAuth
- Prisma
- PostgreSQL
- Solana Web3.js
- Solana SPL Token

## Getting Started

Install dependencies:

```bash
npm install
```

Create an environment file:

```bash
cp .env.example .env
```

Run Prisma setup:

```bash
npx prisma generate
npx prisma migrate dev
```

Start the development server:

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

## Environment Variables

```bash
DATABASE_URL=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
NEXTAUTH_URL=
NEXTAUTH_SECRET=
```

## Documentation

- [Project Overview](./OVERVIEW.md)
- [Deployment Guide](./DEPLOYMENT.md)
- [Improvement Roadmap](./ROADMAP.md)

## Status

Core app structure, authentication, dashboard UI, Prisma setup, and Solana dependencies are in place. The next major step is production-grade wallet connection, quote routing, transaction signing, and swap confirmation.
