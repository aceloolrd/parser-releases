# Customer acceptance scenarios

These files are intentionally separate from the production channel.

Selector scenarios:

- `selectors-v3.json` — valid newer config; client should accept and cache it.
- `selectors-old-v1.json` — valid but older config; client must not downgrade a newer LKG.
- `selectors-invalid.json` — invalid/unsupported config; client must keep its current LKG.

Application-update scenarios are generated automatically when a production GitHub Release is
published:

- `<version>-full-only.json` — no patch is offered, so the updater must use the full ZIP.
- `<version>-patch-fallback.json` — patch metadata has an intentionally wrong patch SHA-256;
  the updater must reject the patch and automatically use the valid full ZIP.
- `<version>-optional.json` — the same release with `mandatory=false`.

The default production files `selectors.json` and `latest.json` are never intentionally broken
for acceptance tests.
