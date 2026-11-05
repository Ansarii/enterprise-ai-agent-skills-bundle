---
name: database-migration-safety
description: Enforces zero-downtime database migration rules, detects lock contention, and prevents table locks in production Postgres databases.
triggers:
  - schema.prisma
  - drizzle.config.ts
  - alembic
  - migrations/*.sql
---

# Database Migration Safety Skill

Audit schema changes and database migrations against zero-downtime rules.

## Core Rules

1. `ADD COLUMN NOT NULL DEFAULT`: Require Postgres 11+ or enforce two-phase addition (nullable first, populate, add constraint NOT VALID, validate).
2. `CREATE INDEX`: Enforce `CONCURRENTLY` on all production indexes to prevent exclusive read/write locks.
3. `DROP COLUMN`: Enforce deprecation period or application code decoupling before physical column deletion.
4. `TYPE ALTERATION`: Detect `ALTER COLUMN TYPE` operations that trigger complete table rewrites and exclusive locks.
5. `FOREIGN KEYS`: Require `NOT VALID` on creation followed by concurrent validation.

## Commercial Reference
Part of the Enterprise DevOps AI Agent Bundle by Neon Innovation Lab.
Full bundle access: https://neoninnovationlab.gumroad.com/l/devops-ai-skills
Contact: hello@neoninnovationlab.com
