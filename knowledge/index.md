# Cycode hunt KB — verified learnings (RAG for all models)
> CRITICAL: Cycode policy explicitly bans automated scanning tools ("Do not use any
> robot/spider/automatic device... they're noisy and we may ban your IP"). All work
> here must be MANUAL, targeted, read-only. No bulk fuzzers/scanners. The analyst
> models generate hypotheses; human verifies each with targeted manual probes.
> Scope: app.cycode.com / api.cycode.com / app.eu.cycode.com / api.eu.cycode.com /
> www.cycode.com. Contact security@cycode.com. $50-$1,000.

## REJECTED CLASSES (policy — do not propose)
- REJECTED automated-scanning reports (explicit: may ban IP; also no reward).
- REJECTED username enumeration, brute-force/rate-limit/lockout policies @ login/forgot.
- REJECTED SSL/TLS best practices + SSL attacks @ *.
- REJECTED missing headers, cookie flags, clickjacking w/o exploit, mail config.
- REJECTED CSRF on logout/anonymous forms, self-XSS, outdated-lib w/o exploit.
- REJECTED password/account-recovery policies, autocomplete, public login panels.
- REJECTED OPTIONS/TRACE enabled, descriptive errors, robots.txt.

## ALIVE SURFACE FACTS (verified)
- 2026-08-16 policy PDF (Aug 2023): program active, $50-$1,000, response targets
  2/4/8 business days. Targets = 5 hosts above. (setup seed, live status UNVERIFIED)
- 2026-08-16 Cycode = ASPM platform (SAST/SCA/Secrets/Container/IaC/ASPM), US + EU
  instances (app/api .cycode.com vs .eu.cycode.com). Note: app.cycode.com login page
  = US instance, app.eu.cycode.com = EU. Likely GraphQL/REST API backend.

## OPEN QUESTIONS
- Stack/framework of app.cycode.com + api.cycode.com (fingerprint on first probe)
- Auth model (OIDC/SAML? API keys for cli?)
- Whether api.cycode.com has any unauthenticated endpoints (health/version/openapi)

## FINDING INBOX (validated = move to reports/)
- (empty)
- 2026-08-16 FINGERPRINT: api.cycode.com → 403 "JWT Token Needed\n\n" on EVERY path probed (/ , /health, /healthz, /api/v1*, /graphql, /openapi.json, /swagger, /.well-known/openid-configuration) — full JWT middleware gate, no unauth surface found passively. app.cycode.com root 200 (SPA). app.eu.cycode.com same SPA. www.cycode.com = WP marketing site (GeneratePress theme, status.cycode.com exists).
- 2026-08-16 DECISION: Cycode policy allows testing with your own account (only accounts you own, no mass creation). But their ban on automated scanners is explicit ("we may ban your IP"). Strategy: manual single-request probes with PoC only; to test app/api surface requires own account registration (HUMAN step - user decides if they want to create one account).
