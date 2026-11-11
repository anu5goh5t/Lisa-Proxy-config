# Lisa-Proxy-config

Shared Shadowrocket routing and DNS configuration for the Lisa VLESS + REALITY service.

## Files

- `shadowrocket.conf`: shared routing, policy groups, and DNS behavior. It contains no user credentials.
- Each user imports their own private 3X-UI **standard SUB** subscription separately.

## Per-user setup

1. Import your own 3X-UI standard SUB URL in Shadowrocket.
2. Rename that subscription entry to exactly `Lisa-Proxy`. This is only a local display name inside Shadowrocket.
3. Import the remote configuration using the raw URL of `shadowrocket.conf`.
4. Tap the configuration and choose **Use Config**.
5. Set **Home > Global Routing > Config**.
6. In the `🚀 节点选择` policy group, choose the desired node if more than one is present.

All users share the same configuration URL. Each user must keep their own private subscription URL and credentials.

## Routing intent

- LAN/private networks: DIRECT.
- Apple and iCloud: Apple policy group, DIRECT by default.
- Microsoft: Microsoft policy group, DIRECT by default.
- Google and Telegram: proxy.
- Steam download CDN: DIRECT.
- Steam Store/community/chat: proxy.
- China domain ruleset: DIRECT.
- Generic international proxy ruleset and final fallback: proxy.
- AdvertisingLite ruleset: REJECT by default, with a manual DIRECT override available.

The generic proxy rule is deliberately placed after the China ruleset. No GEOIP-CN rule is used, avoiding broad IP-only decisions for shared/CDN addresses.

## DNS intent

- DIRECT domains: DNSPod DoH.
- Default DNS override: Cloudflare DoH via the selected proxy.
- VPS node hostname: DNSPod DoH, so the node address can resolve before the tunnel is established.
- System DNS fallback is disabled.

Shadowrocket resolves proxy-routed destination domains on the proxy side by default. The exact resolver observed by a DNS-leak test must still be verified on the target iPhone and network.

## Security

Never commit UUIDs, SUB IDs, full subscription URLs, REALITY private keys, client passwords, or other credentials to this public repository.

## Validation status

Version 0.2.0 is a test draft. The remote ruleset file paths have been checked for existence in the upstream Blackmatrix7 repository. The configuration still requires compilation and real-device testing in Shadowrocket before wider distribution.
