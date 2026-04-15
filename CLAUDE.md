# ReferMe Platform

## Stack
React Native 0.74+ + Expo SDK 51 | Fastify 4.x | MySQL 8.0 | Redis 7.x | BullMQ 5.x | Socket.io 4.x | AdminJS 7.x | Nginx 1.24 | Ubuntu 22.04 | Hetzner CX31

## Sub-Agent Routing Rules

**Parallel** (ALL conditions met):
- 3+ independent tasks, no shared state, clear file boundaries

**Sequential** (ANY condition triggers):
- Tasks have dependencies → pass prior output as context
- Shared files or state risk

**Background**:
- Research/analysis not blocking current work

## Phase Sequence
1. PRD → FSD → Architecture → UX Wireframes (sequential)
2. co-founder-overseer gates Phase 2
3. security-engineer (baseline) + database-architect (schema) in parallel
4. Backend modules in parallel: backend-member + backend-moderator + backend-super-admin + payment-gateway-developer + integration-developer
5. Frontend: frontend-developer
6. QA: qa-tester
7. Parallel: technical-writer + user-training-writer + mobile-release-manager + devops-engineer
8. Final gate: co-founder-overseer launch readiness review

## Hard Constraints (co-founder-overseer enforces)
- Approved stack only — no AWS RDS, no Vercel, no premium managed services
- Infra cost <= ₹8k/month Year 1 (Hetzner CX31 @ ₹980/mo)
- No scope beyond BRD v2.0
- 60% ping completion rate = north star metric
- Trust score: positive-only, no penalties
- Broadcasting stages: 0-24h, 24-72h, 72h+
- Connector earns 50%, platform 40% , Moderator earns 10%— integer paise only, no floats
- Contact reveal in-app only after ping acceptance
- Light mode: deferred post-launch
- Ship fast over perfection

## Business Rules (all agents must follow)
- Ping price auto-assigned by industry category (₹75-₹500)
- Credits purchased via Razorpay — 1 credit = 1 ping send
- 7-day outcome window before payout releases
- Trust Score: 0-5.0 stars, positive events only
- OTP login only — no passwords
- AES-256 encryption for contact details at rest
- Contact details decrypted only after ping acceptance

## Agent File Boundaries

| Agent                     | Owns (write)                                                        | Reads                                       | Never touches                                |
|---------------------------|---------------------------------------------------------------------|---------------------------------------------|----------------------------------------------|
| product-manager           | docs/PRD.md, docs/FSD.md, docs/reviews/                             | ALL (read)                                  | src/, backend/, database/, infra/            |
| product-architect         | docs/architecture/                                                  | ALL (read)                                  | src/, backend/, database/, infra/            |
| co-founder-overseer       | docs/reviews/                                                       | ALL (read)                                  | Any application code                         |
| ux-designer               | src/screens/, src/components/, docs/wireframes/                     | docs/PRD.md, docs/FSD.md                    | src/store/, src/api/, backend/, database/    |
| frontend-developer        | src/                                                                | docs/wireframes/, backend/schemas/          | backend/, database/, infra/                  |
| mobile-release-manager    | app.json, eas.json, .github/workflows/mobile*                       | src/, infra/                                | backend/, database/, src/ (code changes)     |
| backend-member            | backend/modules/auth/, member/, ping/, broadcast/, connect/, chat/, trust/, middleware/ | database/schema/, backend/plugins/ | src/, moderator/, admin/, payments/, infra/ |
| backend-moderator         | backend/modules/moderator/                                          | database/schema/, backend/plugins/          | src/, other backend modules, infra/          |
| backend-super-admin       | backend/modules/admin/                                              | backend/modules/ (read), database/          | src/, infra/                                 |
| payment-gateway-developer | backend/modules/payments/, credits/, plugins/razorpay/              | database/schema/, backend/plugins/bullmq/   | src/, other backend modules, infra/          |
| integration-developer     | backend/plugins/fcm/, whatsapp/, socket/, workers/, modules/notification/, modules/search/ | database/schema/, backend/plugins/bullmq/ | src/, database/migrations/, infra/ |
| database-architect        | database/                                                           | docs/architecture/, backend/modules/ (read) | src/, backend/modules/, infra/               |
| security-engineer         | docs/security/                                                      | ALL (read)                                  | Never writes application code                |
| devops-engineer           | infra/, .github/workflows/                                          | backend/, database/, docs/architecture/     | src/, backend/modules/, database/migrations/ |
| qa-tester                 | tests/, docs/qa/                                                    | ALL (read)                                  | Never writes application code                |
| technical-writer          | docs/api/, docs/architecture/, README.md, CHANGELOG.md             | ALL (read)                                  | Never writes application code                |
| user-training-writer      | docs/user-guides/                                                   | docs/wireframes/, src/screens/              | backend/, database/, infra/                  |
