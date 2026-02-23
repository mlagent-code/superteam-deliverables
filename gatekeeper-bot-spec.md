# Telegram Intro Gatekeeper Bot for Superteam — Delivery Spec

## Goal
Automate member onboarding in Telegram by enforcing intro requirements before full chat access.

## Core Flow
1. New member joins group.
2. Bot DMs intro form (name, role, location, interests, portfolio link).
3. Bot validates required fields + anti-spam checks.
4. On success, bot assigns "verified" role/tag and posts a concise intro card in channel.
5. On failure/timeout, bot re-prompts and escalates to moderators.

## Features
- Configurable form schema and validation rules
- Spam protection (rate limit, duplicate detection, URL checks)
- Moderator dashboard commands (`/review`, `/approve`, `/reject`)
- Export of approved intros (CSV/JSON)
- Localization support (EN + customizable templates)

## Stack
- TypeScript + Telegraf
- Redis (state + rate limits)
- Postgres (audit logs)
- Dockerized deploy + env-based config

## Deliverables
- Architecture + bot command spec
- DB schema + event model
- Production deployment checklist
- Moderation playbook
