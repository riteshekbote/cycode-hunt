# cycode-hunt

Multi-model bug-hunting automation for the **Cycode Bug Bounty Program**.

- **Scope**: `app.cycode.com`, `api.cycode.com`, `app.eu.cycode.com`, `api.eu.cycode.com`, `www.cycode.com`
- **Disclosure**: email `security@cycode.com` (policy: cycode.com/bug-bounty-policy/, PDF)
- **Rewards**: $50–$1,000 (PayPal or wire, invoice required)
- **CRITICAL**: Cycode explicitly bans automated scanning tools ("we may ban your IP"). Manual,
  targeted, read-only probing only. No bulk fuzzers/scanners.

## Cycode exclusions (no reward)
DoS, brute force/rate limit/lockout, username enumeration, SSL/TLS, missing headers, cookie flags,
CSRF on logout/anonymous forms, self-XSS, clickjacking w/o exploit, mail config, outdated libs w/o
exploit, password-recovery policies, autocomplete, public login panels, email-verification gaps,
OPTIONS/TRACE, descriptive errors, robots.txt. See `scope.yml`.

## Reporting
Email `security@cycode.com` with org+contact, products/versions affected, vuln description, technical
details (config, traces, PoC, repro steps), known exploits. First fully-reproducible report wins.

## Note
The analyst models generate hypotheses (they cannot run scanners). Each hypothesis must be verified
by a human with one targeted manual request before reporting.
