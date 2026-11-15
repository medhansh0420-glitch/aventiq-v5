# AventIQ V4 — scroll-led Next.js prototype

## Correct Vercel / Next.js root structure

The repository root is the project root. In Vercel, set **Root Directory** to `./`.

```text
package.json
tsconfig.json
next.config.mjs
next-env.d.ts
app/
  page.tsx
  layout.tsx
  globals.css
DiscoverSection.tsx
MentorMarketplace.tsx
ConsultationHub.tsx
OpportunityCommunity.tsx
PublicTrustCommunity.tsx
ScrollEffects.tsx
OpportunityCard.tsx
opportunities.ts
types.ts
useSavedOpportunities.ts
```

The App Router entry points are at `app/page.tsx` and `app/layout.tsx`. Do not move `app/` into `src/` unless you move the whole project structure consistently.

## Run locally

```bash
npm install
npm run dev
```

Production build:

```bash
npm run build
```

## Included

- Editorial, scroll-led homepage with sticky navigation, section reveal transitions, responsive layouts and reduced-motion support.
- Existing opportunity discovery UI and the supplied `opportunities.ts` data retained unchanged.
- Mentor marketplace, portfolio form and consultation-room prototype retained with explicit demo limitations.
- Worldwide public-profile, trust and community showcase. Empty ratings state is intentional: no ratings or reviews are fabricated.
- Root-level `app/` structure compatible with the Vercel Root Directory set to `./`.

## Critical: what is and is not globally functional

This ZIP is a front-end prototype. It does **not** yet provide real worldwide user accounts, public profile publishing, shared reviews/comments, verified consultation completion, reporting queues, moderation dashboards, spam prevention or review authenticity checks. Existing localStorage-based interactions are browser-local and must not be represented as global or verified.

To make the worldwide requirements production-functional, connect a shared backend and authentication provider (for example Supabase or an equivalent service), then implement:
- authenticated users and explicit per-field/profile visibility controls;
- public read policies only for fields explicitly marked public;
- private storage for email, phone, payment, private messages and consultation URLs;
- consultation records with server-side completion status before a verified review can be submitted;
- one review per eligible completed consultation, immutable audit timestamps and public reviewer-profile links based on public profile settings;
- moderation states (`pending`, `approved`, `rejected`), report queues, rate limits, spam controls and moderator roles;
- database-backed average rating and review count calculated only from approved reviews;
- server-side authorization and row-level security; never trust client-side flags for identity or completion.

No database credentials, auth provider configuration or moderation service were included in the uploaded ZIP, so those cross-user capabilities cannot honestly be enabled by changing front-end files alone.

## Vercel

- Framework preset: Next.js
- Root Directory: `./`
- Build command: `npm run build`
- Install command: `npm install`
