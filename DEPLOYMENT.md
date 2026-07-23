# Solana DEX App Deployment

## Production Targets

Recommended setup:

- **Frontend and API routes**: Vercel.
- **Database**: Neon PostgreSQL, Supabase PostgreSQL, or another managed PostgreSQL provider.
- **OAuth**: Google Cloud OAuth credentials.
- **Blockchain**: Solana RPC endpoint from a reliable provider.

Before deploying with the Vercel CLI, upgrade the CLI on your machine:

```bash
npm i -g vercel@latest
```

## Required Environment Variables

Create these values in the Vercel project settings and in local `.env` files:

```bash
DATABASE_URL=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
NEXTAUTH_URL=
NEXTAUTH_SECRET=
```

Recommended additions before production swap execution:

```bash
NEXT_PUBLIC_SOLANA_RPC_URL=
SOLANA_RPC_URL=
```

## Local Setup

1. Install dependencies:

```bash
npm install
```

2. Create `.env` from `.env.example`.

3. Set a PostgreSQL connection string:

```bash
DATABASE_URL="postgresql://USER:PASSWORD@HOST:5432/DB?schema=public"
```

4. Run Prisma generation and migrations:

```bash
npx prisma generate
npx prisma migrate dev
```

5. Start the app:

```bash
npm run dev
```

## Google OAuth Setup

1. Open Google Cloud Console.
2. Create or select a project.
3. Configure the OAuth consent screen.
4. Create OAuth client credentials for a web application.
5. Add local callback URL:

```text
http://localhost:3000/api/auth/callback/google
```

6. Add production callback URL:

```text
https://YOUR_DOMAIN/api/auth/callback/google
```

7. Copy the values into:

```bash
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
```

## Vercel Deployment

1. Import the GitHub repository into Vercel.
2. Use the default Next.js framework detection.
3. Set the environment variables above.
4. Set `NEXTAUTH_URL` to the production domain:

```bash
NEXTAUTH_URL=https://YOUR_DOMAIN
```

5. Deploy.

6. After deployment, run database migrations against production:

```bash
npx prisma migrate deploy
```

Run this from a secure environment with `DATABASE_URL` set to the production database.

## Database Provider Notes

For Neon:

- Create a project and database.
- Use the pooled connection string for runtime if needed.
- Use the direct connection string for migrations when the provider recommends it.

For Supabase PostgreSQL:

- Use the connection string from Project Settings.
- Keep service role keys out of this app unless a server-only admin path is added.

## Solana Production Notes

Before real swaps:

- Use a paid or reliable Solana RPC provider.
- Add wallet connection support.
- Simulate transactions before sending.
- Show network fees, slippage, route, and confirmation state.
- Never place private keys in frontend code or public env vars.

## External Services And API Keys

- Google OAuth is required for sign-in.
- PostgreSQL is required for Prisma.
- A Solana RPC provider is recommended before real swap execution.
- Neon can be used as the PostgreSQL provider.
- Supabase is optional unless you choose Supabase PostgreSQL.
- Anthropic and OpenAI keys are not used by the current code.

## Deployment Checklist

- `npm run build` passes locally.
- `npx prisma migrate deploy` runs against production database.
- Google OAuth callback URLs are configured.
- `NEXTAUTH_SECRET` is a strong random value.
- Production domain is set in `NEXTAUTH_URL`.
- Runtime logs are checked after first sign-in.
