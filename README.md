# Keystone

**Multi-Tenant Identity & Access Management Platform**

Keystone is an enterprise-oriented IAM backend for SaaS applications. It provides a centralized system for managing users, organizations, memberships, invitations, roles, permissions, sessions, and security events while enforcing strict isolation between tenants.

## What It Does

- **Multi-tenancy** — Organizations act as isolated tenants, with users able to belong to multiple organizations.
- **Authentication** — Secure user registration, login, JWT-based authentication, refresh tokens, and session management.
- **Role-Based Access Control** — Organizations can define custom roles and granular permissions rather than relying on hardcoded user types.
- **Team Management** — Invite teammates, assign roles, manage memberships, and revoke access.
- **Session Management** — Track active sessions and remotely revoke individual sessions or all sessions for a user.
- **Rate Limiting** — Redis-backed rate limiting protects authentication and sensitive API endpoints from abuse.
- **Audit Logging** — Security-sensitive actions are recorded for organizational visibility and accountability.
- **API Access** — Organizations can create and revoke scoped API keys for programmatic access.
- **OIDC** — Support for external identity providers such as Google and GitHub.

## Architecture

```text
Client
  │
  ▼
Node.js / TypeScript API
  │
  ├── Authentication
  ├── Authorization / RBAC
  ├── Tenant Isolation
  ├── Session Management
  ├── Rate Limiting
  └── Audit Logging
  │
  ├───────────────┐
  ▼               ▼
PostgreSQL       Redis
```

Every protected request follows the general flow:

```text
Authenticate → Resolve Tenant → Verify Membership
→ Check Permission → Execute Tenant-Scoped Operation
```

This ensures that authentication, authorization, and tenant isolation are enforced server-side rather than relying on the frontend.

## Tech Stack

- **Backend:** TypeScript, Node.js, Express
- **Database:** PostgreSQL, Prisma
- **Caching & Infrastructure:** Redis
- **Authentication:** JWT, OAuth 2.0 / OIDC
- **Frontend:** React
- **Testing:** Jest, Supertest
- **Deployment:** Docker, GitHub Actions

## Why Keystone?

Keystone is designed to explore the engineering challenges behind production SaaS infrastructure rather than simply implementing basic authentication.

The project focuses on:

- Multi-tenant database design
- Secure authentication and authorization
- Fine-grained RBAC
- API design and validation
- Distributed rate limiting
- Session and credential management
- Security auditing
- Defense-in-depth application security

> **Keystone provides the identity, access, and security foundation that a multi-tenant SaaS application can build upon.**

🚧 **Status:** In active development