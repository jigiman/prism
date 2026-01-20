# GitHub Copilot Instructions — AI Operating Manual (PromptVault)

This document defines **how AI (GitHub Copilot / Chat)** should behave across
the full software development lifecycle (SDLC) for PromptVault.

It is not only a set of code rules.
It is the **AI operating manual** for Developers, QA Engineers, and Reviewers.

> **Core principle**  
> AI accelerates work, but **human judgment is always the final gate**.
> All code reviews use ralph.auto.pipeline. Fast/deep pipelines are internal behaviors, not user choices.

---

## 1. Global AI Principles (Ralph Mode)

These rules apply **in all modes**, unless explicitly overridden.

When generating, reviewing, or analyzing artifacts:

- Do not assume prior knowledge
- Prefer clarity over cleverness
- State assumptions explicitly
- Call out edge cases and failure modes
- Explain non-obvious decisions
- If information is missing or ambiguous, ask before proceeding
- Correctness is more important than speed

---

## 2. AI SDLC Modes (How AI Should Behave)

AI is used in **different modes** during the SDLC.
Each mode has a different posture and constraints.

### 2.1 PRD / Design Mode

Purpose: clarify intent before implementation.

AI MUST:

- Treat JIRA stories as **incomplete input**
- Enrich requirements without inventing scope
- Surface assumptions, gaps, and open questions explicitly
- Focus on testability and clarity

AI MUST NOT:

- Write production code
- Silently invent requirements
- Optimize or design beyond stated intent

---

### 2.2 Implementation Mode

Purpose: translate approved intent into code.

AI MUST:

- Treat PRD as the source of truth
- Implement only what is specified
- Prefer readable, explicit code
- Preserve backward compatibility unless explicitly stated otherwise

AI MUST NOT:

- Expand scope beyond the PRD
- Refactor unrelated code
- Optimize prematurely

---

### 2.3 Ralph Context Review Mode (Greenfield / Brownfield)

Purpose: self-review before formal review.

AI MUST:

- Explain behavior in plain English
- Make constraints and assumptions explicit
- Identify known risks

AI MUST NOT:

- Chase perfection
- Rewrite large sections unless explicitly asked

---

### 2.4 Ralph Pipeline Mode

Purpose: safety, correctness, and convergence.

AI MUST:

- Execute phases in order (intent → review → failure hunting → fix)
- Surface silent failures and ambiguous behavior
- Fix material issues only
- Converge deliberately (not infinite loops)

AI MUST NOT:

- Require zero remaining issues
- Introduce new scope during fixes

---

### 2.5 QA Validation Mode

Purpose: validate behavior from a user and risk perspective.

AI MUST:

- Focus on user-visible behavior
- Identify test scenarios, edge cases, and regressions
- Highlight untested or risky areas

AI MUST NOT:

- Write product code
- Assume developer intent without evidence
- Treat Ralph output as sufficient validation

---

## 3. Role-Specific Expectations

### Developers

- Use AI to accelerate implementation and understanding
- Remain accountable for correctness and design decisions
- Run Ralph Pipeline for AI-generated or high-risk code

### QA Engineers

- Use AI to design tests, not to write product code
- Validate PRD coverage and regression risk
- Treat AI as an assistant, not an oracle

### Reviewers / Leads

- Use Ralph outputs to guide review discussions
- Focus on risk, not style
- Accept or defer risk explicitly

---

## 4. Stack Overview

### High-Level System Architecture

PromptVault is a **full-stack web application** following **Domain-Driven Design (DDD)** and **Clean Architecture** principles:

- **Frontend**: Single-page application (SPA) built with React and TypeScript
- **Backend**: RESTful API built with ASP.NET Core 10.0
- **Real-time Communication**: SignalR for bidirectional client-server communication
- **Database**: PostgreSQL (production), SQLite (development/testing)
- **Authentication**: JWT-based authentication with refresh tokens
- **API Documentation**: OpenAPI 3.0 / Swagger with Scalar UI

### Backend Technologies

#### Core Framework

- **.NET 10.0 LTS** - Long-term support version of the .NET platform
- **ASP.NET Core 10.0** - Web API framework with controllers and middleware
- **C# 14** - Language features including nullable reference types and pattern matching

#### Architecture Layers

- **PromptVault.Api** - Presentation layer (controllers, middleware, DI configuration)
- **PromptVault.Contracts** - API contracts and DTOs (request/response models)
- **PromptVault.Application** - Application services (commands, queries, validators, mappings)
- **PromptVault.Domain** - Domain layer (aggregates, value objects, domain events, business rules)
- **PromptVault.Infrastructure** - Infrastructure layer (data access, repositories, external services)
- **PromptVault.Core** - Shared kernel (interfaces, constants, exceptions, base classes)

#### Data Access & Storage

- **Entity Framework Core 10.0** - ORM for database operations with LINQ support
- **PostgreSQL 14+** (via Npgsql.EntityFrameworkCore.PostgreSQL 10.0) - Production relational database
- **SQLite** (via Microsoft.EntityFrameworkCore.Sqlite 10.0) - Development and testing database
- **EF Core Migrations** - Code-first schema versioning and deployment automation

#### Authentication & Security

- **ASP.NET Core Identity** - User management, password hashing, and role-based authorization
- **JWT Bearer Authentication** - Stateless authentication with access tokens (15 min) and refresh tokens (7 days)
- **Microsoft.IdentityModel.Tokens 8.15** - Token generation, validation, and signing
- **System.IdentityModel.Tokens.Jwt 8.15** - JWT token handling
- **HtmlSanitizer 9.0** - XSS protection for user-generated content sanitization

#### Real-time Communication

- **SignalR** - WebSocket-based bidirectional real-time updates for journey tracking and admin notifications

#### Email & Messaging

- **MailKit 4.14** - SMTP email sending for user notifications (configurable, disabled in development)
- **RazorLight 2.3** - Email template rendering using Razor syntax

#### Monitoring & Observability

- **Serilog 9.0** - Structured logging with file and console sinks
- **prometheus-net 8.2** - Metrics collection and Prometheus endpoint exposure for monitoring

#### Resilience & Performance

- **Polly 8.6** - Resilience patterns (retry, circuit breaker, timeout) for transient fault handling
- **Connection Pooling** - PostgreSQL connection pooling (5-50 connections) for performance optimization

#### API Documentation

- **Microsoft.AspNetCore.OpenApi 10.0** - OpenAPI 3.0 schema generation
- **Scalar.AspNetCore 1.2** - Interactive API documentation UI (modern Swagger UI alternative)

#### Image Processing

- **SixLabors.ImageSharp 3.1** - Cross-platform image manipulation and processing (avatars, thumbnails)

### Frontend Technologies

#### Core Framework

- **React 18.3** - Component-based UI library with hooks and concurrent features
- **TypeScript 5.x** - Statically typed JavaScript with strict type checking
- **Vite** - Fast build tool with hot module replacement (HMR) and optimized production builds
- **React Router 6.30** - Declarative client-side routing and navigation

#### UI Component Libraries

- **Radix UI** - Headless, accessible component primitives (30+ components: dialog, dropdown, tooltip, etc.)
- **shadcn/ui** - Pre-styled, customizable components built on Radix UI and Tailwind CSS
- **Lucide React 0.462** - Modern icon library with 1000+ SVG icons

#### Styling

- **Tailwind CSS 3.x** - Utility-first CSS framework with JIT compilation
- **PostCSS** - CSS transformation pipeline with autoprefixing
- **tailwindcss-animate 1.0** - Animation utilities and keyframes
- **@tailwindcss/typography 0.5** - Beautiful prose styling for markdown and rich text
- **class-variance-authority 0.7** - Type-safe component variant management
- **clsx 2.1** / **tailwind-merge 2.6** - Utility for conditional and merged class names

#### State Management & Data Fetching

- **TanStack Query (React Query) 5.83** - Powerful server state management with caching, synchronization, and background updates
- **Axios 1.13** - Promise-based HTTP client with interceptors, request/response transformation
- **React Hook Form 7.61** - Performant form state management with minimal re-renders
- **Zod 3.25** - TypeScript-first schema validation for forms and API responses

#### Real-time Communication

- **@microsoft/signalr 9.0** - SignalR client for WebSocket connections and real-time updates

#### Rich Content & Markdown

- **React Markdown 10.1** - Markdown rendering with extensibility
- **remark-gfm 4.0** - GitHub Flavored Markdown support (tables, task lists, strikethrough)
- **React Syntax Highlighter 16.1** - Code syntax highlighting with multiple themes
- **DOMPurify 3.3** - XSS protection for HTML sanitization

#### Data Visualization

- **Recharts 2.15** - Composable React charting library for analytics dashboards
- **Plotly.js 3.3** / **react-plotly.js 2.6** - Interactive scientific charts and graphs

#### Drag & Drop

- **@dnd-kit/core 6.3** - Modern, accessible drag-and-drop toolkit
- **@dnd-kit/sortable 10.0** - Sortable lists with smooth animations

#### Data Tables

- **TanStack Table 8.21** - Headless table library for complex data grids with sorting, filtering, pagination

#### Theme & Appearance

- **next-themes 0.4** - System-aware dark mode and theme switching
- **Embla Carousel 8.6** - Lightweight carousel/slider component

#### Additional UI Components

- **react-day-picker 8.10** - Flexible date picker component
- **react-dropzone 14.3** - File upload with drag-and-drop
- **react-resizable-panels 2.1** - Resizable split panel layouts
- **vaul 0.9** - Drawer/bottom sheet component
- **sonner 1.7** - Beautiful toast notifications
- **cmdk 1.1** - Command palette component (⌘K menu)
- **input-otp 1.4** - OTP (one-time password) input component

#### Developer Experience

- **ESLint 9.32** - Pluggable linting utility for JavaScript and TypeScript
- **Prettier** - Opinionated code formatter
- **TypeScript Compiler** - Type checking and IntelliSense
- **Vite Plugins** - React SWC for fast compilation

### Testing

#### Backend Testing

- **xUnit** - Primary unit and integration testing framework for .NET
- **Entity Framework InMemory** - In-memory database provider for fast testing without external dependencies

#### Frontend Testing

- **Vitest** - Vite-native unit testing framework with Jest-compatible API
- **@testing-library/react 16.3** - React component testing with user-centric queries
- **@testing-library/jest-dom 6.9** - Custom DOM matchers for assertions
- **@testing-library/user-event 14.6** - User interaction simulation
- **Playwright 1.57** - End-to-end browser testing across Chromium, Firefox, WebKit
- **@faker-js/faker 10.1** - Realistic test data generation
- **Vitest UI** - Browser-based test UI for interactive debugging
- **Coverage** - Code coverage reporting via Vitest

### Database & Storage

#### Production

- **PostgreSQL 14+** - Primary ACID-compliant relational database
- **Npgsql** - High-performance .NET data provider for PostgreSQL
- **Connection Pooling** - 5-50 pooled connections for optimal performance

#### Development

- **SQLite** - Zero-configuration file-based database for local development
- **No external database required** - Developers can run the app immediately

#### Testing

- **Entity Framework InMemory** - Fast in-memory database for unit tests

#### Schema Management

- **EF Core Migrations** - Code-first database schema evolution
- **Migration Scripts** - Deployment automation scripts in `backend/deployment/`
- **apply-migrations.sh** - Automated migration application for production deployments

### External Integrations

#### Email Delivery

- **SMTP** - Email delivery via MailKit (configurable, disabled by default in development)
- **Email Templates** - Razor templates for notification emails (embedded resources)

#### Monitoring (Production-Ready)

- **Prometheus** - Metrics scraping endpoint exposed via prometheus-net for monitoring dashboards

### Infrastructure & Deployment

#### Development Environment

- **Vite Dev Server** - Frontend development server with hot module replacement (HMR)
- **Kestrel** - Cross-platform ASP.NET Core development server
- **SQLite** - Local database with no external dependencies
- **CORS** - Configured for localhost development (ports 8080, 5173)

#### Build & Bundling

- **Vite Production Build** - Frontend bundling with code splitting, tree shaking, and minification
- **.NET CLI** - Backend compilation (`dotnet build`, `dotnet publish`)
- **npm/bun** - Frontend package management (bun.lockb present)

#### Deployment Configuration

- **Environment-Specific Settings** - `appsettings.{Environment}.json` for Development/Production
- **Migration Automation** - Shell scripts in `backend/deployment/`
- **PostgreSQL Production** - Production environment uses PostgreSQL with connection pooling
- **CORS Whitelist** - Strict origin control per environment

#### CI/CD

- **Manual Deployment** - Deployment via shell scripts (no automated CI/CD pipeline detected)

### Cross-Cutting Concerns

#### Logging

- **Serilog** - Structured logging with configurable sinks (file, console)
- **Log Levels** - Environment-specific log levels (Debug in development, Warning+ in production)
- **Log Files** - Rolling file logs in `backend/PromptVault.Api/logs/`

#### Security

- **JWT Token Strategy** - Short-lived access tokens (15 min) + long-lived refresh tokens (7 days)
- **Absolute Session Timeout** - 30 days maximum session lifetime
- **Sliding Session Timeout** - 20 minutes of inactivity
- **CORS** - Strict allowed origins whitelist
- **XSS Protection** - HtmlSanitizer for user-generated content
- **SQL Injection Protection** - Parameterized queries via EF Core
- **HTTPS Enforcement** - Production HTTPS redirection (implied)
- **Password Hashing** - ASP.NET Core Identity with secure password hashing

#### Configuration Management

- **appsettings.json** - Base configuration
- **appsettings.{Environment}.json** - Environment-specific overrides
- **Environment Variables** - Override support for secrets and deployment-specific values
- **User Secrets** - Local development secrets (not committed to source control)

#### Performance Optimization

- **Database Connection Pooling** - PostgreSQL pooling (5-50 connections)
- **Async/Await** - Non-blocking I/O throughout the stack
- **EF Core Query Optimization** - Efficient queries with eager loading and projections
- **Frontend Code Splitting** - Vite chunking strategy for optimal load times
- **Bundle Analysis** - Rollup visualizer for bundle size optimization

#### API Versioning

- **No explicit versioning** - Current API is unversioned (v1 implied)

---

## Guiding Rule

> **If it is not in the PRD, it is not a requirement.**

---

## Final Note

AI is a multiplier.  
Accountability remains human-owned.

This document defines **how AI is expected to behave**.  
Prompts define **what AI is asked to do**.
