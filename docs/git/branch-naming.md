# Git Branch Naming Conventions

A Git branch should always respect the following format:

**type/GCR-XXX-component-title-of-the-ticket**

- **type** is always **Lowercase** and is always followed by a **/**. Allowed values, no others:
  - feat
  - fix
  - chore
  - docs
  - refactor
  - learning
  
- **GCR-XXX** is the Ticket ID (from the Notion ticket), always **Uppercase** and followed by a **-**.

- **component** is always **Lowercase** and followed by a **-**. Allowed values, no others:
  - init
  - android
  - ios
  - kmp
  - postgresql
  - ktor
  - llm
  - ci
  - cloud
  - design
  - firebase

- **title-of-the-ticket** is the ticket title (from the Notion ticket), in **Lowercase** with each word separated by a **-**.

Examples:
- feat/GCR-7-design-atoms-layer
- refactor/GCR-2-android-multi-module-architecture
- feat/GCR-6-llm-truthfulness-skill

To avoid:
- feature/new-graph
- bugfix/auth
- update-stuff
- GCR-4-branch
- postgresql-work

## Why These Choices?

**type** is placed first to make filtering and reviewing easier: branches are naturally grouped by intent in any Git client or CI interface. All feature branches appear together, all fixes together, and so on.

**component** is **Lowercase** here whereas **COMPONENT** is **Uppercase** on tickets. On a ticket list, uppercase inside brackets creates visual contrast. On a branch name, there are no brackets, so uniform lowercase keeps it clean.

Everything is **Lowercase** with **-** as separator, which is Git-friendly: branch names with uppercase letters or special characters can cause issues depending on the OS or tooling.

The only exception to **Lowercase** is the Ticket ID. The **GCR-XXX** reference is the direct bridge to the Notion ticket, making traceability immediate from the branch name alone.

## Technology Exploration Branches

The **learning** type is specifically for technology exploration and experimentation branches. These branches test, migrate, and compare alternative technologies to the default stack.

### Use Cases for Learning Branches

- **Library exploration**: testing alternatives to default libraries (e.g. Realm vs Room, Koin vs Hilt)
- **Technology migration**: migrating from one technology to another
- **Benchmarking**: comparing performance or features between different implementations
- **Educational experiments**: learning new patterns or approaches

### Format

**learning/GCR-XXX-component-technology-purpose**, using the same **component** values defined above (not limited to android, any repo can use a learning branch with its own component).

### Examples

- learning/GCR-15-android-realm-migration
- learning/GCR-30-ktor-graphql-exploration
- learning/GCR-31-llm-embedding-model-comparison

### Key Principles

- **Default stack first**: the main codebase always uses Google's recommended libraries (Retrofit, Room, Hilt, etc.).
- **Isolated exploration**: each learning branch explores one specific technology in isolation.
- **No merge to main**: these branches are experimental and should not be merged into the main branch unless a formal ADR is created to change the default stack.
- **Documentation**: findings and comparisons should be documented in ADRs or separate documentation pages.
