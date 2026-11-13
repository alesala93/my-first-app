---
paths:
  - "src/app/api/**"
  - "src/lib/supabase*"
  - "src/proxy.ts"
  - "supabase/**"
---

# Backend Development Rules

These rules describe the template default (Supabase). If the Tech Stack in CLAUDE.md names a different backend, apply the same principles to it: access control, input validation, indexes, bounded queries.

## Database (Supabase)
- ALWAYS enable Row Level Security on every table
- Create RLS policies for SELECT, INSERT, UPDATE, DELETE
- Add indexes on columns used in WHERE, ORDER BY, and JOIN clauses
- Use foreign keys with ON DELETE CASCADE where appropriate
- Never skip RLS - security first

## API Routes
- Validate all inputs using Zod schemas before processing
- Always check authentication on the server. With Supabase: server client from `@supabase/ssr` (session in cookies, refreshed in `src/proxy.ts`), identity verified with `supabase.auth.getClaims()`. Never trust `getSession()` in server code
- Return meaningful error messages with appropriate HTTP status codes
- Use `.limit()` on all list queries

## Query Patterns
- Use Supabase joins instead of N+1 query loops
- Cache rarely-changing data with the `use cache` directive (needs `cacheComponents: true` in `next.config.ts`; it replaces `unstable_cache` in Next.js 16). Read `node_modules/next/dist/docs/01-app/01-getting-started/08-caching.md` before enabling it
- Always handle errors from Supabase responses

## Security
- Never hardcode secrets in source code
- Use environment variables for all credentials
- Validate and sanitize all user input
- Use parameterized queries (Supabase handles this)
