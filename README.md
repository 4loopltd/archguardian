# ArchGuardian
### The AI Architectural Linter for Modern Codebases

**[Live Site & Demo](https://archguardian.4loop.co.uk/)**

ArchGuardian is a proposal for a new category of developer tooling:  
**a per‑repository micro‑model that understands your project’s architecture, patterns, and intent — and protects it from drift, rot, and inconsistency.**

Traditional linters enforce syntax.  
Static analysis enforces safety.  
**ArchGuardian enforces architecture.**

---

## 🚨 The Problem

Modern codebases — especially large or legacy ones — suffer from:

- **Architectural drift:** AI generates code that "works" but doesn't *fit*.
- **Inconsistent patterns:** Different agents and developers introduce different approaches.
- **Context limits:** Even the best models only see a slice of the repo.
- **Review overload:** Senior engineers spend time policing patterns instead of building.

As AI adoption accelerates, these problems are getting worse, not better.

---

## 🧠 The Solution: A Per‑Repo Micro‑Model

ArchGuardian proposes a **small, repo‑specific AI model** that:

- Lives at the root of your repository (`.project-model/`)
- Understands your architecture, patterns, and conventions
- Evolves with every PR via **LoRA fine-tuning**
- Rebuilds itself on a schedule to avoid drift
- Exposes a clean API via **MCP** for any agent (Copilot, Claude, Cursor, etc.)

This model becomes the **architectural memory** of your project.

---

## 🏗️ How It Works

### 1. **A micro‑model per repository**
Small enough to train locally (e.g., Llama-3.2-3B).  
Large enough to encode patterns, naming, and architecture.

### 2. **LoRA updates on PR merge**
A GitHub Action fine‑tunes the model on:
- Changed files
- Surrounding context
- PR description
- Review comments

### 3. **Scheduled rebuilds**
Nightly/weekly jobs rebuild the model from scratch to prevent drift.

### 4. **MCP / API interface**
Agents query the model for:
- Pattern detection
- Impact analysis
- Architectural guidance
- Canonical implementation suggestions

---

## 🔧 Example Interactions

**“Where is OAuth implemented in this repo?”**  
ArchGuardian:
- Library: Spring Security
- Pattern: Custom middleware
- Entry point: `AuthConfig.java`
- Used in: gateway, user-service, audit-log
- Canonical flow: Pattern E

**“What modules are impacted if I change UserDTO?”**  
ArchGuardian returns a dependency map.

**“Is this PR consistent with our existing event handler pattern?”**  
ArchGuardian performs architectural linting.

---

## 🧩 Why GitHub Is the Perfect Home

GitHub already owns:
- Repos
- PR lifecycle
- Actions compute
- Copilot
- IDE integrations

A per‑repo model is a **GitHub‑native concept**.  
Training is **client‑side**, so it’s economically viable.

---

## 🔐 Security Model

- Models stored per repo
- No cross‑tenant training
- No centralised model sharing
- Training happens locally or on self‑hosted runners
- Full enterprise control

---

## 📚 Documentation

- [The Problem](docs/problems.md)
- [The Solution](docs/solutions.md)
- [Architecture](docs/architecture.md)
- [Model Lifecycle](docs/model-lifecycle.md)
- [MCP Interface](docs/mcp-interface.md)
- [GitHub Actions](docs/github-actions.md)
- [Roadmap](docs/roadmap.md)

---

## 📣 Contributing

This project is currently a **proposal**.  
Feedback, discussion, and collaboration are welcome.

---

## 📄 License

MIT
