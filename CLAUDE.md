# ReferMe Platform

## Stack
React Native + Expo | Fastify 4.x | MySQL 8.0 | Redis 7.x | BullMQ | Socket.io | Nginx 1.24 | Ubuntu 22.04 | Hetzner/Utho VPS

## Sub-Agent Routing Rules

**Parallel dispatch** (ALL conditions must be met):
- 3+ independent tasks with no shared state
- Clear file boundaries with no overlap
- Example: database-architect + ux-designer + security-engineer can run in parallel

**Sequential dispatch** (ANY condition triggers):
- Tasks have dependencies (pass prior output as context)
- Shared files or state risk (merge conflict risk)
- Unclear scope (need to understand before proceeding)

**Background dispatch**:
- Research and analysis tasks not blocking current work
- Results not needed immediately

## Phase Sequence

1. **Requirements & Design** → product-manager (PRD) → product-manager (FSD) → product-architect (architecture) + ux-designer (wireframes) in parallel
2. **Strategic Gate** → co-founder-overseer reviews Phase 1 outputs before proceeding
3. **Security + DB** → security-engineer (baseline) + database-architect (schema) in parallel
4. **Backend Development** → parallel: backend-member + backend-moderator + backend-super-admin + payment-gateway-developer + integration-developer
5. **Frontend Development** → frontend-developer (uses UX wireframes + API structure)
6. **Testing** → qa-tester (test plans + execution)
7. **Docs & Release** → parallel: technical-writer + user-training-writer + mobile-release-manager + devops-engineer

## Hard Constraints (co-founder-overseer enforces)
- Approved stack only — no AWS RDS, no Vercel, no premium managed services
- Infra cost ≤ ₹8k/month Year 1
- No scope beyond BRD v2.0 — defer everything else
- 60% ping completion rate = north star metric
- Trust score: positive-only, no penalties
- Broadcasting staging: 0-24h, 24-72h, 72h+
- Light mode: deferred post-launch
- Ship fast over perfection

## Agent Model Assignment
- co-founder-overseer → claude-opus-4-6 (strategic decisions)
- All other agents → claude-sonnet-4-6 (cost-optimized)
- Override subagent model: export CLAUDE_CODE_SUBAGENT_MODEL="claude-sonnet-4-6"
