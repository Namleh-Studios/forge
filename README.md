# Namleh Forge

> Auth, billing, multi-tenancy, MCP. Done. Cloudflare-deployed for ~$0/mo.

Two frontends, full API, agent-ready MCP server, the gotchas already fixed. The work an experienced dev would do anyway, skipped.

**[See the live demo →](https://namlehforge.dev)** &nbsp; **[Buy Forge — $149](https://namlehforge.dev#pricing)**

---

## What's in the box

- **Frontends:** Next.js 15 + SvelteKit 2 (identical features, pick or ship both)
- **Backend:** Hono on Cloudflare Workers
- **Auth:** Supabase (OAuth + email + magic links + multi-org)
- **Database:** Supabase Postgres with Drizzle ORM and RLS
- **Payments:** Stripe Checkout + Customer Portal + webhook → DB sync
- **Email:** Resend + verified-domain transactional flows
- **AI:** Anthropic Claude streaming chat with per-plan usage limits, OpenAI adapter included
- **MCP:** Cloudflare Workers MCP server with bearer-key auth and 6 read-only domain tools — your app is agent-ready day one
- **UI:** Tailwind v4 with a dark-first design system

## What's NOT in the box

- Yet another Vercel template
- Yet another Next-only stack
- Yet another setup-hell 30-page README

## What's it cost to run?

Running on free tiers, Forge will carry your SaaS to ~50,000 active users for **$0/month**. Beyond that, ~$25/mo when Supabase Pro kicks in.

| Service | Free tier | Cost beyond |
|---|---|---|
| Cloudflare Workers | 100k req/day | $5/mo for 10M |
| Supabase | 500MB DB, 50k MAU | $25/mo Pro |
| Stripe | No fixed cost | 2.9% + 30¢/sale |
| Resend | 3k emails/mo | $20/mo for 50k |
| Anthropic | Pay per token | ~$0.01-0.03/chat |

## What you actually skip

Sign up for the [demo](https://namlehforge.dev), poke around — it's a working SaaS. Sign-in flow, member invites, role permissions, Stripe checkout to upgrade your org, billing portal, agent-ready MCP. The kind of plumbing that takes 3 weeks to wire correctly the first time.

`pnpm forge:setup` provisions Cloudflare Workers, Stripe products + webhook, Supabase auth config, and a www → apex redirect rule in about a minute. From clone to live deploy in under 30 minutes if your provider accounts are ready.

## Why "AI-native"?

The chat module isn't just a wrapper. The **MCP server** ships configured with bearer-token auth (HMAC-keyed, not raw SHA-256), per-org rate limits, and 6 domain tools (`whoami`, `get_organization`, `list_members`, `list_conversations`, `get_conversation`, `get_usage`). Plug your buyers' apps into Claude Desktop or any MCP client out of the box.

Most boilerplates haven't caught up to MCP yet. This one is built around it.

## Stack decisions, made

We made the boring decisions so you don't have to argue about them in a Discord:

| Decision | Choice | Why |
|---|---|---|
| Cloud | Cloudflare | Cheapest free tier, edge-everywhere, zero cold-start |
| Auth | Supabase | Free, OAuth + email + magic, JWKS verification |
| DB | Postgres (Supabase) | Real RLS, real joins, real production option |
| ORM | Drizzle | Type-safe, edge-compatible, doesn't fight you |
| Payments | Stripe (default) + Lemon Squeezy adapter | Most flexibility, MoR option for VAT |
| AI | Anthropic Claude (default) + OpenAI adapter | Better model, simple swap |
| Frontend | Next + Svelte | Both work; pick at deploy time |

Swap any of these — the integrations are clean. But the defaults are good defaults.

## Buy

**Single price: $149.** One developer, unlimited projects, lifetime updates. No subscription. EU buyers waive the 14-day refund right at checkout.

**[→ Buy Forge for $149](https://namlehforge.dev#pricing)**

## Compare

| | Forge | ShipFast | Supastarter | Makerkit |
|---|---|---|---|---|
| Price | **$149** | $199 | $299 | $299–799 |
| Cloud | Cloudflare | Vercel | Vercel | Vercel/AWS |
| Frontends | Next + SvelteKit | Next | Next | Next/Remix |
| MCP server | ✅ included | ❌ | ❌ | ❌ |
| Free-tier cap | ~50k MAU | ~1k MAU | ~50k MAU | ~5k MAU |
| Setup time | ~30 min | ~1 hour | ~2 hours | ~3 hours |
| Setup automation | ✅ | partial | ✅ | partial |

## License

Commercial single-developer license. Use on any number of your own projects, modify freely. Don't redistribute the source as a competing template.

## Built by Namleh Studios

Solo-founder boilerplate, shipped after building the same plumbing on three different SaaS attempts and getting tired of it. [namlehstudios.com](https://namlehstudios.com)

Questions: hello@namlehforge.dev. Async only, no calls.
