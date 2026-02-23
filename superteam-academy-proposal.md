# Superteam Academy LMS dApp — MVP Technical Submission

## 1) Product scope (MVP in 2 weeks)
A production-oriented LMS for Solana builders with:
- Course modules + lesson progression
- Embedded coding exercises (sandboxed)
- XP/streak/achievement engine
- On-chain completion credential issuance (Anchor)
- Multilingual surface (EN/PT/ES)

## 2) Proposed architecture
- **Frontend:** Next.js + TypeScript + Tailwind
- **Backend API:** Fastify/Node with PostgreSQL
- **Auth:** Wallet + email fallback
- **On-chain layer:** Anchor program for credential NFTs/badges + achievement proofs
- **Indexing:** Helius/webhook ingestion to keep learner credential state in sync
- **Analytics:** PostHog + custom event schema

## 3) Data model (core)
- users(id, wallet, locale, created_at)
- courses(id, slug, language, difficulty)
- lessons(id, course_id, order, content_md)
- attempts(id, user_id, lesson_id, score, runtime_sec)
- streaks(user_id, current_streak, last_active_day)
- achievements(id, key, metadata)
- user_achievements(user_id, achievement_id, awarded_at, tx_sig)

## 4) On-chain program (Anchor)
- `initialize_user_profile`
- `record_lesson_completion`
- `award_achievement`
- `mint_course_credential`

Account constraints:
- deterministic PDA per (user, course)
- signer checks for update authority
- replay protection via completion nonce

## 5) Milestones
### M1 (Days 1-3)
- Repo setup, CI, schema, auth, course browsing
### M2 (Days 4-7)
- Lesson runner + progress tracking + XP
### M3 (Days 8-11)
- Anchor program integration + credential mint path
### M4 (Days 12-14)
- Localization + analytics + hardening + docs

## 6) Security/reliability
- strict input validation (zod)
- idempotent completion writes
- transaction retry/backoff and signature confirmation
- abuse controls for XP farming

## 7) Deliverables
- Public repo with setup scripts
- Architecture decision record (ADR)
- Demo walkthrough + seed data
- Test plan + known limitations

## 8) Why this can win
- concrete architecture, not vague ideation
- production constraints addressed (state sync, anti-abuse, reliability)
- scoped MVP with clear milestone cadence
