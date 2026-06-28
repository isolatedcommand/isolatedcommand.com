---
title: "Isolated Command Volunteer Management System"
description: "Volunteer operations, reimagined on the edge."
draft: false
image: "images/logo.png"
bg_image: "images/logo.png"
series: []
information:
  - label: "Name"
    info: "Isolated Command Volunteer Management System (VMS)"
  - label: "Type"
    info: "Project"
  - label: "Team Members"
    info: "Conan ZHANG"
  - label: "Live System"
    info: "<a href=https://volunteer.isolatedcommand.com/dashboard/>Click Here</a>"
  - label: "Stack"
    info: "Cloudflare Workers · D1 · Hugo · Zero Trust"
  - label: "GitHub"
    info: "<a href=#>Click Here</a>"
---

## Isolated Command Volunteer Management System

### Volunteer Operations, Reimagined on the Edge

Spreadsheets, group chats, and "who's coming to the event again?" — that's how
most volunteer programmes are run. **VMS** replaces all of it with a single,
secure platform where managers create events, volunteers sign themselves up,
hours are tracked, rewards are calculated, and recognition letters are generated
at the click of a button.

Built end-to-end on a fully serverless Cloudflare stack.

---

## The Problem We Saw

Coordinating volunteers is deceptively hard:

- **Sign-ups live everywhere** — forms, messages, and memory — and nobody has a
  single source of truth.
- **Double bookings and duplicates** creep in the moment more than one person
  helps manage the list.
- **Hours and recognition** are tracked manually, so volunteers rarely get the
  credit (or the letters) they've earned.
- **Access control** is an afterthought — everyone can see and edit everything.

We wanted one clean system that handles the whole lifecycle: from creating an
event to handing a volunteer a polished certificate of service.

---

## What We Built

A complete volunteer management platform with two clear roles:

- **Volunteers** can browse and join events, log the hours for events they've
  signed up for, manage their own profile, give feedback, and export a
  personalised recognition letter.
- **Volunteer Managers** get everything above, plus the ability to create and edit events,
  assign volunteers, record attendance for anyone, broadcast notifications, run
  the rewards engine, and even query the database directly through a guarded SQL
  console.

Every action is permission-checked on the server, so the rules hold no matter
what the interface shows.

---

## Highlights

- **Role-based access control** — a clean split between volunteers and managers,
  enforced on every endpoint.
- **Self-service events** — volunteers join and leave events themselves, with
  duplicate sign-ups blocked at the database level.
- **Smart attendance** — per-event maximum hours and submission deadlines stop
  bad data before it lands.
- **Rewards engine** — hours are converted into points using configurable rules,
  recalculated in seconds.
- **Live dashboard** — real-time metrics, announcements, and a volunteer
  leaderboard.
- **Recognition letters** — a one-click, professionally formatted PDF certificate
  of service, generated on the fly.
- **Database console** — managers can run ad-hoc SQL safely, with dangerous
  operations blocked.

---

## How It's Built

VMS runs entirely on Cloudflare's edge — no traditional servers to maintain:

- **Frontend** — a Hugo static site delivered globally.
- **Authentication** — Cloudflare Zero Trust with single sign-on; users are
  verified before they ever reach the application.
- **Backend** — a single Cloudflare Worker exposing a REST API, handling all
  business logic, access control, and PDF generation.
- **Database** — Cloudflare D1 (SQLite), with a schema normalised to Third
  Normal Form across 13 tables.

The result is a system that's fast everywhere, secure by default, and costs
almost nothing to run.

---

## The Database Behind It

At its heart, VMS is a data-driven platform. The schema is normalised to **3NF**
across **13 tables**, with `volunteers` and `events` as the core entities and an
`allocations` bridge table enforcing a one-sign-up-per-event rule. Integrity is
protected by primary and foreign keys, `CHECK` constraints, and validation
triggers — so the data stays clean even when it's edited directly.

---

## See It Live

ICVMS is deployed and running. Take a look at the volunteer dashboard:

<a
  href="https://volunteer.isolatedcommand.com/dashboard/"
  target="_blank"
  rel="noopener noreferrer"
  style="display:inline-block;padding:12px 18px;border-radius:10px;border:1px solid #ddd;text-decoration:none;"
>
  Open the Isolated Command Volunteer Management System
</a>

> Access is protected by Cloudflare Zero Trust. Get in touch if you'd like a
> guided walkthrough or a demo account.