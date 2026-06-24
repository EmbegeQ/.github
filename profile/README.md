# Welcome to EmbegeQ

## About EmbegeQ

EmbegeQ is not a traditional PHP framework. The modern PHP landscape is rapidly shifting away from the shared-nothing, stateless architecture of PHP-FPM towards long-running, stateful worker processes utilizing engines like FrankenPHP, RoadRunner, and Swoole.

EmbegeQ is built from the ground up to operate within these highly optimized stateful worker loops, solving the problems of memory leaks, state bleeding, and bootstrapping bottlenecks through its **PSR Bridge Architecture**. Instead of reinventing HTTP logic or ORMs, EmbegeQ acts as a highly optimized, memory-safe Integration Layer (Glue) that strictly enforces a Dual-Scope memory model while wrapping industry-standard PHP libraries.

## Key Principles & The Dual-Scope Memory Model

To achieve extreme performance without memory leaks, EmbegeQ splits its dependency injection container into two strict scopes:

- **The Application Scope (Boot Phase)**: Instantiated exactly once when the worker process starts. Lives in RAM indefinitely for configuration registries, database pools, and stateless services.
- **The Request Scope (Loop Phase)**: Created precisely when a new HTTP request enters the worker loop, and explicitely destroyed when the response is emitted. Prevents state bleeding between users.

EmbegeQ relies heavily on PHP Standard Recommendations (PSR) including PSR-3, PSR-7, PSR-11, PSR-14, and PSR-15 to ensure a fully decoupled and robust ecosystem.

## Core Packages & Ecosystem

Our ecosystem is composed of granular, purpose-built packages.

### Priority 1: Core Systems
- **[embegeq/framework](https://github.com/EmbegeQ/framework)**: The core PSR-15 Middleware Dispatcher and Dual-Scope Container kernel.
- **[embegeq/embegeq](https://github.com/EmbegeQ/embegeq)**: The Application Skeleton and foundation for end-user applications.

### Priority 2: Security & Authentication Bridges
- **[embegeq/grendel](https://github.com/EmbegeQ/grendel)**: API JWT Authentication.
- **[embegeq/lawang](https://github.com/EmbegeQ/lawang)**: End-user Authentication Scaffolding.
- **[embegeq/lawangsewu](https://github.com/EmbegeQ/lawangsewu)**: OAuth2 Client integration.
- **[embegeq/gerbang](https://github.com/EmbegeQ/gerbang)**: OAuth2 Server integration.

### Priority 3: Real-time Infrastructure
- **[embegeq/toa](https://github.com/EmbegeQ/toa)**: WebSocket Server integration utilizing Workerman.

## Documentation & Architecture

Before proposing architectural decisions or writing new features, please consult the global [ROADMAP.md](https://github.com/EmbegeQ/documents/blob/main/ROADMAP.md) inside the `documents` repository.

We enforce a Strict English Policy for all textual output, documentation, commit messages, and issues.
