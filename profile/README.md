<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./assets/lendara-logo-light.svg">
    <img src="./assets/lendara-logo-dark.svg" alt="Lendara" width="220">
  </picture>
</p>

<h1 align="center">Lendara</h1>

<p align="center"><b>Local money in, private USDC out, on Stellar.</b></p>

<p align="center">
Open infrastructure for Latin America: an embeddable local-currency → USDC on-ramp, and a compliance layer that turns that deposit into a private balance.
</p>

<p align="center">
  <a href="https://lendara-monorepo-fixh.vercel.app"><b>Lendara</b></a> ·
  <a href="https://lendara-monorepo-fixh.vercel.app/docs"><b>Lendara Docs</b></a> ·
  <a href="https://lendara-shield.duckdns.org/en"><b>Shield Demo</b></a> ·
  <a href="https://lendara-shield.duckdns.org/en/docs"><b>Shield Docs</b></a>
</p>

---

## What we build

### Lendara: the on-ramp

An embeddable **ARS / CLP / CRC → USDC** on-ramp (Argentina, Chile, Costa Rica), like a checkout for Stellar. A project gets an API key, embeds a widget in a few lines, and its users pay in local currency and receive USDC. Any SEP-24 wallet can use it with no extra code.

The public **sandbox** is a real anchor on testnet with simulated fiat rails and test cards, so you can test every path, failures included.

[Repo](https://github.com/Lendara-Org/Lendara-monorepo) · [Try the demo app](https://lendara-monorepo.vercel.app) · [Quickstart](https://lendara-monorepo-fixh.vercel.app/docs/en/quickstart)

### Lendara Shield: private payments

*Private payments, built into wallets and anchors.*

The reference implementation of the **Shield Protocol**, an open compliance layer for [Stellar Private Payments](https://developers.stellar.org/docs/build/apps/privacy). A deposit made through any SEP-24 anchor lands as a **private balance**, and the user's address **never appears on-chain**. Shield acts as the pool's ASP (allow-list / block-list). The integrator decides who is eligible, and an auditor holding the view key can still see everything.

[Repo](https://github.com/Lendara-Org/lendara-shield) · [Live demo](https://lendara-shield.duckdns.org/en) · [API reference](https://lendara-shield.duckdns.org/api-reference.html)

---

## How they fit together

```
User pays in local currency ──► Lendara (SEP-24 anchor) ──► USDC ──► Shield ──► private balance in the pool
                                                                       │
                                                           user's address never on-chain
```

Shield talks to Lendara only through SEP-1, SEP-10 and SEP-24, so it works with **any** SEP-24 anchor.

---

## Integrate your way

| You are… | Use |
|---|---|
| An app or dApp | Lendara API with [`@lendara/ramp`](https://www.npmjs.com/package/@lendara/ramp) (server) and [`@lendara/widget`](https://www.npmjs.com/package/@lendara/widget) (browser) |
| A Stellar wallet | Lendara's standard SEP-1 / SEP-10 / SEP-24 endpoints, home domain `lendara-monorepo-fixh.vercel.app` |
| A wallet or anchor adding privacy | Shield's REST API ([`openapi.yaml`](https://github.com/Lendara-Org/lendara-shield/blob/develop/openapi.yaml)) and the [Shield Protocol draft](https://github.com/Lendara-Org/lendara-shield/blob/develop/docs/protocol/shield-protocol.md) |

---

## Tools

| Tool | Description |
| :--- | :--- |
| [Developer dashboard](https://lendara-monorepo-fixh.vercel.app/dashboard) | Create a project and get a test API key |
| [Demo app](https://lendara-monorepo.vercel.app) | A sample app that integrates the Lendara widget |
| [Shield web app](https://lendara-shield.duckdns.org/en) | Onboard, deposit (ramp or direct), private wallet, audit view |
| [Shield API reference](https://lendara-shield.duckdns.org/api-reference.html) | Interactive reference generated from `openapi.yaml` |

> ⚠️ **Testnet only.** No real money moves. Stellar Private Payments is a developer preview with unaudited contracts.
