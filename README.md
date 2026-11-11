# Lisa-Proxy-config

Centralized Shadowrocket DNS and routing configuration.

## Files

- `shadowrocket.conf`: shared routing and DNS configuration. It contains no user credentials.
- Each user must separately import their own 3X-UI SUB subscription in Shadowrocket.

## Import procedure

1. Add the user's own 3X-UI standard SUB subscription in Shadowrocket.
2. Set the subscription display name to `Lisa-Test` for test accounts or `Lisa-Proxy` for production accounts.
3. Import the raw URL of `shadowrocket.conf` from **Config > +**.
4. Select the downloaded configuration and choose **Use Config / Compile Config**.
5. Set **Home > Global Routing > Config**.

## Security

Never commit UUIDs, SUB IDs, subscription URLs, REALITY private keys, client passwords, or other credentials to this public repository.

## Status

The current configuration is a test draft. Validate DNS behavior, rule-set download, Apple/Microsoft policy selection, Steam routing, and the final default route on a real Shadowrocket device before production rollout.
