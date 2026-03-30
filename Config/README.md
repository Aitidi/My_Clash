# Config

## Files

- `my_config.ini` — remote rule generator / subscription config
- `dns_config.yaml` — local Clash Verge Rev DNS override for Fake-IP environments

## Telegram media fix for OpenClaw

If Telegram images/files fail to download inside OpenClaw while using Clash Verge Rev with Fake-IP enabled, do **both** of the following:

1. In Clash Verge Rev, make sure local DNS override is enabled:

```yaml
enable_dns_settings: true
```

This lives in local `verge.yaml` on the machine and is **not** part of the generated subscription itself.

2. Use `dns_config.yaml` from this folder so Telegram domains are excluded from Fake-IP:

- `telegram.org`
- `*.telegram.org`
- `t.me`
- `*.t.me`
- `telegram-cdn.org`
- `*.telegram-cdn.org`

## Why

Without the DNS override actually being enabled, Telegram domains may still resolve into Clash Fake-IP space (`198.18.0.0/16`), which can break OpenClaw media downloads.

## After changing

- Restart Clash Verge Rev / Mihomo core
- Restart OpenClaw Gateway
- Re-test Telegram image upload/download
