# Aget Framework

**Open-source framework for AI-assisted software engineering agents**

Aget enables developers to create specialized AI agents that collaborate on software projects through discovered patterns rather than rigid commands.

---

## Repositories

### Templates

- **[aget-worker-template](https://github.com/aget-framework/aget-worker-template)** - Template for creating worker agents (action-taking or information-only)

---

## Naming Conventions

- **Aget** - Framework name (proper noun, capitalized)
- **aget-** - Prefix for framework components (lowercase)
- **-AGET** - Suffix for action-taking agents (⚠️ can modify systems)
- **-aget** - Suffix for information-only agents (✅ read-only)

**Examples**:
```
my-github-AGET              # Action-taking: Creates PRs, merges code
my-spotify-analyst-aget     # Information-only: Reports analytics
```

The suffix convention provides visual capability signaling - like `sudo` or `rm -rf`, the capitalized AGET warns of powerful operations.

---

## Philosophy

**Privacy-First**: Framework works fully offline with no telemetry or required sharing.

**Pattern Discovery**: Agents learn from interactions rather than following rigid command structures.

**Incremental Development**: Start with simple capabilities, evolve through use.

---

## Getting Started

1. **Clone the worker template**:
   ```bash
   git clone https://github.com/aget-framework/aget-worker-template my-custom-aget
   cd my-custom-aget
   ```

2. **Initialize your agent**:
   ```bash
   aget init
   ```

3. **Start working**: Wake up your agent and begin collaboration

---

## Documentation

- **Migration Guides**: See individual repository docs
- **Framework Docs**: Coming in v2.4+
- **Community**: Issues and discussions welcome

---

## Framework Version

**Current**: v2.4.0 "Clarity"
- Naming conventions established
- Organizational grouping (`aget_group`)
- Privacy-first architecture foundation

---

## Contributing

Framework is in active development. Contribution guidelines coming in v2.5+.

---

## License

Apache 2.0 (individual repositories may vary - check each repo)

---

*Aget Framework - Discovered patterns, not rigid commands*
