---
bg_image: images/logo.png
description: A lightweight, serverless URL shortening platform built on
  Cloudflare Workers and Workers KV.
draft: false
image: images/logo.png
information:
- info: Isolated Command Go System (ICGo)
  label: Name
- info: Internal Infrastructure Project
  label: Type
- info: Conan ZHANG
  label: Team Members
- info: "`<a href=https://go.isolatedcommand.com>`{=html}go.isolatedcommand.com`</a>`{=html}"
  label: Live System
- info: Cloudflare Workers · Workers KV · TypeScript · Wrangler
  label: Stack
- info: "`<a href=#>`{=html}Coming Soon`</a>`{=html}"
  label: GitHub
title: Isolated Command Go System (ICGo)
---

# Isolated Command Go System (ICGo)

The **Isolated Command Go System (ICGo)** is Isolated Command's
self-hosted URL shortening platform. Every short link follows the
format:

    https://go.isolatedcommand.com/<name>

It is built entirely on **Cloudflare Workers** and **Workers KV**,
allowing requests to be processed from Cloudflare's global edge network
with minimal latency.

------------------------------------------------------------------------

# Why We Built ICGo

As Isolated Command grew, we needed a branded, reliable and self-managed
way to share links for documentation, GitHub repositories, events, forms
and community resources.

Instead of relying on third-party URL shorteners, ICGo gives us complete
ownership of our infrastructure while remaining lightweight and
inexpensive to operate.

------------------------------------------------------------------------

# Architecture

``` text
                    Isolated Command Go System (ICGo)

                    +----------------------+
                    |    User Browser      |
                    +----------+-----------+
                               |
                               | HTTPS Request
                               v
                    +----------------------+
                    |  Cloudflare Edge POP |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    | Cloudflare Worker    |
                    | Redirect Logic       |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    |     Workers KV       |
                    | URL Mapping Store    |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    | Target Website       |
                    +----------------------+
```

The Worker extracts the requested slug, queries Workers KV, and
immediately returns an HTTP redirect.

------------------------------------------------------------------------

# Request Flow

  Step   Component         Action
  ------ ----------------- ----------------------------------------
  1      User              Visits `go.isolatedcommand.com/github`
  2      Cloudflare Edge   Routes request to nearest POP
  3      Worker            Extracts the slug
  4      Workers KV        Looks up the destination URL
  5      Worker            Returns HTTP 301/302 redirect
  6      Browser           Opens the destination

``` text
User
 │
 ▼
Cloudflare Edge
 │
 ▼
Cloudflare Worker
 │
 ▼
Workers KV
 ├── Found ─────► HTTP Redirect
 └── Not Found ─► HTTP 404
```

------------------------------------------------------------------------

# Workers KV

Workers KV stores simple key-value mappings.

  Slug        Destination
  ----------- ------------------------------------
  github      https://github.com/isolatedcommand
  discord     https://discord.gg/...
  docs        https://isolatedcommand.com/docs
  volunteer   https://forms.office.com/...

------------------------------------------------------------------------

# Technology Stack

  Layer        Technology           Purpose
  ------------ -------------------- ------------------------
  Runtime      Cloudflare Workers   Execute redirect logic
  Storage      Workers KV           Store mappings
  Language     TypeScript           Worker implementation
  Deployment   Wrangler             Deploy updates
  Network      Cloudflare Edge      Global delivery

------------------------------------------------------------------------

# Traditional vs Serverless

  Traditional URL Shortener   ICGo
  --------------------------- ------
  Virtual Machine             ❌
  Web Server                  ❌
  Database Server             ❌
  Load Balancer               ❌
  Manual Scaling              ❌
  Cloudflare Workers          ✅
  Workers KV                  ✅
  Global Edge                 ✅

------------------------------------------------------------------------

# Benefits

-   Fast edge execution
-   Global availability
-   Automatic scaling
-   HTTPS by default
-   Low operational cost
-   Minimal maintenance
-   Branded URLs

------------------------------------------------------------------------

# Deployment

``` text
Developer
   │
   ▼
Git Repository
   │
   ▼
Wrangler Deploy
   │
   ▼
Cloudflare Workers
   │
   ▼
Cloudflare Global Edge
   │
   ▼
Users Worldwide
```

------------------------------------------------------------------------

# Future Roadmap

-   Analytics dashboard
-   QR code generation
-   REST API
-   Link expiration
-   Authentication
-   Role-based access control
-   Audit logging
-   Custom domains

------------------------------------------------------------------------

# Conclusion

ICGo demonstrates how a modern serverless architecture can replace
traditional infrastructure for lightweight services. By combining
Cloudflare Workers with Workers KV, Isolated Command has built a fast,
scalable and globally distributed URL management platform that is simple
to maintain while providing complete ownership over our branded links.
