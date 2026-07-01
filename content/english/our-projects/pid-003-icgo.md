---
title: "Isolated Command Go System (ICGo)"
description: "A free, open-source URL shortener on Cloudflare's edge — generally available, built by DevComm."
draft: false
image: "images/logo.png"
bg_image: "images/logo.png"
series: []
information:
  - label: "Name"
    info: "Isolated Command Go System (ICGo)"
  - label: "Type"
    info: "Open-Source Community Project · Edge Infrastructure"
  - label: "Maintained by"
    info: "Isolated Command Developer Community (DevComm)"
  - label: "Team Members"
    info: "Conan ZHANG"
  - label: "Live System"
    info: "<a href=https://go.isolatedcommand.com>go.isolatedcommand.com</a>"
  - label: "Stack"
    info: "Cloudflare Workers · Workers KV · Hugo · Cloudflare Access · Wrangler"
  - label: "GitHub"
    info: "<a href=https://github.com/isolatedcommand/Go>github.com/isolatedcommand/Go</a>"
---

## Isolated Command Go System (ICGo)

### A free, open URL shortener on the edge

**ICGo** is Isolated Command's URL shortening platform, served at
`go.isolatedcommand.com/<name>`. It is **open source** and **generally available**:
anyone can shorten a link and browse the public directory, with no account required.
Maintainers manage links behind Cloudflare Access.

It runs **entirely on Cloudflare Workers and Workers KV** — no origin server, no
database, no virtual machines. Every request is handled at Cloudflare's global edge,
so redirects resolve close to the user, worldwide.

---

## Why We Built ICGo

As Isolated Command grew, we needed a branded, reliable, self-managed way to share
links for documentation, repositories, events, forms and community resources — without
handing our traffic to a third-party shortener.

ICGo began as internal infrastructure. It is now an **open community project of
DevComm**: a small, auditable codebase anyone can read, self-host or contribute to,
while remaining cheap to run and fast everywhere.

---

## Architecture

One Worker does three jobs: it serves the static site, exposes a JSON API, and
redirects short codes — reading and writing link records in Workers KV.

```text
Browser ─▶ Cloudflare Edge ─▶ Worker
                                 │
        ┌────────────────────────┼──────────────────────────┐
        ▼                        ▼                           ▼
   /api/*  →  JSON API    path in KV  →  302 redirect    else  →  static site / 404
                          (+ click analytics)
```

Static pages (home, search, docs, admin) are a Hugo build on the **Publisher** theme,
served by the Worker's assets binding before the Worker runs. Everything else is a KV
lookup: a match is a `302` redirect with a click counted; a miss falls through to `404`.

---

## Security

Every destination is validated **before** it is stored, so an unsafe or policy-violating
link can never be saved or served:

- **Scheme allow-list** — only `http:` / `https:`; `javascript:`, `data:`, `file:`,
  `blob:`, `chrome:`, `edge:`, `about:`, `mailto:` and `ftp:` are rejected.
- **SSRF protection** — blocks `localhost`, internal hostnames, and private / loopback /
  link-local IP ranges (IPv4 and IPv6), plus redirect loops back to the shortener.
- **Content blocklists** — editable JSON lists of blocked domains and keywords, matched
  against the host, path and query.
- **HTTPS only** and **rate limiting** — creation is capped per client IP, storing only
  *hashed* identifiers; repeated abuse is logged.
- **Admin behind Cloudflare Access** — the `/admin` console and admin API require a
  Zero Trust login, and the Worker verifies the Access JWT (signature, `iss`, `aud`, `exp`)
  on every request. The public API is read + create only.

---

## What's Delivered

| Capability | Status |
| --- | --- |
| Branded short links (random or custom codes) | ✅ |
| Public, searchable link directory | ✅ |
| Click analytics (count, created, last accessed, status) | ✅ |
| Link expiration | ✅ |
| JSON REST API (create / search / admin) | ✅ |
| URL validation, SSRF protection & content blocklists | ✅ |
| Per-IP rate limiting & abuse logging | ✅ |
| Admin console (edit / disable / delete) via Cloudflare Access | ✅ |
| Editable JSON configuration (no code change) | ✅ |

---

## Technology Stack

| Layer | Technology | Purpose |
| --- | --- | --- |
| Runtime | Cloudflare Workers | Routing, validation, redirects and API at the edge |
| Storage | Workers KV | Link records + searchable metadata |
| Front end | Hugo + Publisher theme | Static site (home, search, docs, admin) |
| Auth | Cloudflare Access (Zero Trust) | Admin authentication, verified by the Worker |
| Deployment | Wrangler + esbuild | Build & deploy; config bundled into the Worker |

---

## Open Source

ICGo is developed in the open by **DevComm**. The code, security model and
configuration are all public — fork it, self-host it on your own domain, or send a pull
request. Issues and contributions (a blocklist entry, a hardening, a docs fix, a feature)
are welcome on [GitHub](https://github.com/isolatedcommand/Go).

Full documentation — architecture, security, API and a self-hosting guide — lives at
[go.isolatedcommand.com/docs](https://go.isolatedcommand.com/docs/).

---

## Roadmap

- QR-code generation for any short link
- Per-maintainer roles and audit logging
- A visual analytics dashboard
- Per-user custom domains

---

## Conclusion

ICGo shows how a modern serverless architecture can replace traditional infrastructure
for a real, public service. By combining Cloudflare Workers with Workers KV — and adding
a proper security model, an admin console behind Cloudflare Access, and open,
community-maintained code — Isolated Command runs a fast, globally distributed URL
platform that is cheap to operate, safe to expose, and free for everyone to use.
