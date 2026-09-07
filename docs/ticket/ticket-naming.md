# Ticket Naming Conventions

## Epic Ticket

An Epic Ticket should always respect the following format:

**[MC-XXX] epic: description**

- Prefix **MC-XXX** should always be between **[]** and **Uppercase**.
- **Description** should describe a feature, a user objective, or a technical objective. It should be nominal, not contain any verb, and must be **Capitalized**.

Examples:
- [MC-1] epic: Entity Navigation Flow
- [MC-2] epic: Offline Reading Flow
- [MC-3] epic: Kotlin 2.3 Migration
- [MC-4] epic: KMP Concurrency Model Stabilization

To avoid: [MC-3] epic: Migrate to Kotlin 2.3


## Story Ticket

Story Tickets and Bug Tickets should always respect the following format:

**[GCR-XXX][COMPONENT] type: description**

- Prefix **GCR-XXX** should always be between **[]** and **Uppercase**.

- **COMPONENT** must always be between **[]** and in **Uppercase** (to distinguish it visually from the surrounding text). Allowed values, no others:
  - INIT
  - ANDROID
  - IOS
  - KMP
  - POSTGRESQL
  - KTOR
  - LLM
  - CI
  - CLOUD
  - DESIGN
  - FIREBASE
  
- **type** comes right after **[COMPONENT]** and is always **Lowercase**. Allowed values, no others:
  - feat
  - fix
  - chore
  - doc
  - refactor
  - learning
  
- **description** must start with an imperative verb (Create, Setup, Fix, Add, Update, etc.) and must be **Capitalized**.

Examples:
- [GCR-1][INIT] doc: Write project overview
- [GCR-2][ANDROID] refactor: Migrate Android project to gradle Multi Module
- [GCR-3][CLOUD] chore: Set up Docker container
- [GCR-4][POSTGRESQL] feat: Create relational graph between entities
- [GCR-5][KTOR] fix: Fix authentication timeout
- [GCR-6][LLM] feat: Create Claude Code skill to check content truthfulness
- [GCR-7][DESIGN] feat: Create Atoms Section in Design System
- [GCR-8][KTOR] learning: Complete Ktor fundamentals course

To avoid: [GCR-3][INIT]: Gradle android configuration


## Why These Choices?

For Epic tickets, **MC** (the initials of Mytho Compendium) made sense as a prefix. Epics are the highest level of ticket in the project, the different "bricks" that, once assembled, make the whole MC project.

For Story Tickets and Bug Tickets, drawing on team experience (feature team, squad, the name doesn't matter), the prefix is usually an acronym built from the team name. Working alone on this project, the prefix is built from personal initials instead: **GCR**.

The two prefixes (**MC** vs **GCR**) also serve a subtle purpose: they immediately signal the level of the ticket being looked at, even outside of Notion.
