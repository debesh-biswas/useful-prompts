# Audit App for 20 Security Risks

**Use when:** you want an AI coding agent to check your app against 20 common, real-world security holes and fix only what you approve
**Inputs:** `{{APP_DESCRIPTION_AND_STACK}}`, e.g. "Recipe sharing app. Next.js 15 on Vercel, Supabase (Postgres + auth + storage), Stripe."
**Works with:** coding agents that can read your code (Claude Code, Cursor, Codex). DNS, hosting and provider settings are handed back to you as exact settings to check.

## Prompt

```
My app is: {{APP_DESCRIPTION_AND_STACK}}

Audit my app against the 20 security risks below.

Rules:
- The audit is read-only. Report on all 20 before changing anything.
- Fix only the ones I approve, one at a time, and run the project's checks (lint, typecheck, test, build) after each.
- Don't install anything, don't change or rotate any keys, and don't touch production without asking me first.
- Never print a secret's value in your report. Say where it is (file:line or commit), not what it is.
- Some items are DNS, hosting or provider settings, not code. For those, tell me the exact setting and where to find it, and I'll check it.
- Don't commit unless I ask.

For each of the 20, report:
- Applies: yes / no / can't tell from here.
- Evidence: the file:line, config, or dependency version that shows it.
- Severity: critical / high / medium / low.
- Fix: what would change, in one or two lines.

Start with a summary table of everything that applies, sorted by severity.

The 20:

Authentication & accounts (defence in depth: no single check guards anything important)
1. Auth checked only in Next.js middleware [Next.js]. CVE-2025-29927 lets a crafted header skip middleware. Check the Next.js version (patched: 12.3.5, 13.5.9, 14.2.25, 15.2.3 or later) and check authorization in the route or server action too, not only in middleware.
10. A weak or hardcoded JWT secret [code]. Use a long random secret from the environment, pin the expected algorithm (reject "none"), and verify the signature on every request.
12. No email verification on signup [code, provider]. Verify the email before the account can be used, and don't silently merge a later social login into an unverified account.
20. Login, signup and reset that leak which emails exist [code]. Return the same generic response (same message, status code and similar timing) whether or not the account exists.

Never trust the client (all input is hostile until the server checks it)
4. Price trusted from the browser [code, payments]. The client sends a product id and quantity; the server looks up the price, computes the total and creates the payment.
14. Server-side fetches of user-given URLs [code, AWS]. Don't fetch user-supplied URLs from inside your network; if you must, allowlist hosts and block private and metadata IPs. Require IMDSv2 on AWS.
15. User input reaching filesystem paths [code]. Don't pass user input to file APIs; map it to an id or resolve and check the path stays inside the allowed folder. Keep the server and its software patched.
16. Reset links built from the Host header [code]. Build password-reset links and every other emailed link from a configured base URL, never from the request's Host header.
19. Redirects built from user input [code]. Only allow relative paths or destinations on an allowlist.

Least privilege (grant the minimum access, keep everything private by default)
3. Open storage or database rules [Firebase, Supabase, S3]. Buckets private, row/storage policies scoped to the owner, signed URLs for sharing. Tighten rules before deploy.
6. A database reachable from the internet [hosting]. Nothing bound to a public interface without auth; database on a private network behind the app. Confirm a backup exists and has been restored at least once.
9. An AI feature with too much access [AI features]. Least access it needs, no secrets in its instructions, treat page and user text as untrusted, and require human approval before anything it can't undo.

Abuse limits (cap the blast radius of automated attacks)
5. Login with no defence against credential stuffing [code, provider]. Rate-limit per account and per IP, turn on a breached-password check, and offer MFA.
8. Send endpoints with no limit [SMS, email]. Rate-limit anything that sends an SMS or email per recipient and per IP, add a delay between sends, and cap which countries you send to.
11. Race conditions on limits [code, database]. For one-time codes, promo codes, balances and quotas, make the check and the update one atomic database step (conditional update, unique constraint, or transaction with a row lock).

Nothing private ships (deploy only what the public should see)
2. The .git folder served in production [hosting]. Deploy built output only and block /.git. Search the git history for keys ever committed and list them for me to rotate.
17. Source maps shipped to production [build]. Don't publish production source maps (or upload them privately to your error tracker), and check what a package contains before publishing it.
13. DNS records pointing at deleted services [DNS]. List subdomains (CNAME/A records) that point at services I may have removed, for me to check and delete.

Browser & supply chain
7. Third-party scripts loaded from a CDN [code]. List every external script; self-host or pin with Subresource Integrity, and drop abandoned ones.
18. No framing protection [hosting, code]. Send Content-Security-Policy: frame-ancestors 'self' (and X-Frame-Options: DENY or SAMEORIGIN for older browsers).
```

## Why each one matters

1. **Middleware-only auth:** CVE-2025-29927 (CVSS 9.1) let one header skip Next.js middleware. Vercel advises not relying on middleware alone.
2. **Exposed .git:** Intruder scanned 3.5M hosts and found 28,000 exposed repos, including live Stripe and AWS keys.
3. **Open storage:** Tea's unprotected Firebase bucket leaked about 72,000 images, including selfies and photo IDs.
4. **Client-side price:** Stripe's docs say to recalculate amounts on the server and never trust client totals.
5. **Credential stuffing:** Verizon's DBIR puts it at a median 19% of all authentication attempts.
6. **Open database:** the 2020 "Meow" attack script wiped almost 4,000 databases in a weekend.
7. **CDN scripts:** cdn.polyfill.io, embedded on 100,000+ sites, was caught injecting malware (Sansec).
8. **SMS pumping:** bots flood "text me a code" endpoints and you pay per message (Twilio).
9. **AI access:** OWASP LLM01 says prompt injection can leak system prompts and reach functions users shouldn't, and no defence is foolproof.
10. **Weak JWT secret:** a guessable secret can be brute-forced from a wordlist and used to forge any user's token (PortSwigger).
11. **Race conditions:** simultaneous requests can redeem a one-time code many times or push a balance below zero (PortSwigger).
12. **Account pre-hijacking:** a USENIX study found at least 35 of 75 popular services vulnerable.
13. **Dangling DNS:** Silent Push found 16,000 dangling subdomains and automated taking over 4,000 of them.
14. **SSRF:** a fetched URL can hit the cloud metadata service and return instance credentials. IMDSv2 blocks most of these (AWS).
15. **Path traversal:** `../` can read arbitrary files. Apache's CVE-2021-41773 was critical.
16. **Host header poisoning:** a changed Host header can deliver the reset token to the attacker's domain (PortSwigger).
17. **Source maps:** a published npm source map exposed nearly 2,000 TypeScript files of Claude Code's source.
18. **Clickjacking:** your page is framed invisibly so visitors click your buttons by mistake (OWASP).
19. **Open redirects:** links on your domain forward users to phishing pages under your domain's trust (OWASP).
20. **Account enumeration:** different responses let anyone test which emails have accounts. OWASP says to respond the same way either way.
