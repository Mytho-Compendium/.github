# Commit Message Conventions

A commit message should always respect the following format:

**[GCR-XXX][COMPONENT] type: description**

- **GCR-XXX** is the Ticket ID (from the Notion ticket), always between **[]** and in **Uppercase**.

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

- **description** must start with an imperative verb (Create, Setup, Fix, Add, Update, etc.), must be **Capitalized**, and should be concise, ideally under 72 characters to keep it readable in any Git client.
