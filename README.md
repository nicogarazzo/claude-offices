# Claude Offices

Create specialized teams of AI agents ("offices") for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) with structured quality pipelines.

Based on the **Soul + Skills architecture** from [Hermes Agent](https://github.com/NousResearch/hermes-agent) by Nous Research, adapted to work natively with Claude Code's skill and sub-agent system. Each agent gets a **Soul** modeled after real-world domain experts, and every office enforces a 2-round production + critique pipeline.

## How it works

```
Round 1:  Agent A (produces) → Agent B (produces) → Agent C (produces)
Critique: [A critiques] + [B critiques] + [C critiques]   ← parallel
Round 2:  Agent A (rewrites) → Agent B (refines) → Agent C (final verdict)
```

No deliverable leaves an office without at least 2 rounds.

## The Soul + Skills pattern

Inspired by Hermes Agent's five-pillar architecture, Claude Offices adapts two core concepts to Claude Code's native primitives:

**Soul**: Each agent has a persistent identity based on a real domain expert. Not just a role description, but a codified methodology, personality traits, and principles extracted from that expert's actual work. A translation agent doesn't just "translate", it operates as Eugene Nida applying dynamic equivalence theory.

**Skills as Offices**: Each office is a Claude Code Skill that acts as a dispatcher. When invoked, the skill orchestrates its sub-agents through the 2-round pipeline, handling routing, critique rounds, and final delivery.

| Hermes Agent concept | Claude Offices equivalent | Claude Code primitive |
|---|---|---|
| Soul (identity) | Agent `.md` body | Sub-agent system prompt |
| Skills (procedures) | Office `SKILL.md` | Claude Code Skill |
| Profiles (isolation) | Agent frontmatter | `~/.claude/agents/` |
| Kanban (orchestration) | 2-round pipeline | Skill dispatcher logic |

## Quick start

```bash
git clone https://github.com/nicogarazzo/claude-offices.git
cd claude-offices
./swarm install

# Restart Claude Code to detect new skills and agents
```

After installing, you get:
- `/oficina-creator` skill: describe an office in natural language, it researches expert figures and generates everything
- `/oficina-copywriting` skill: a complete B2B copywriting pipeline (included as example)
- `./swarm` CLI: manually create and manage offices

## Creating offices

### Option 1: Natural language (recommended)

In any Claude Code session after installing:

```
/oficina-creator

"Create an office for translating technical docs from English to Spanish"
```

The skill will:
1. **Research** the best domain experts to model each agent (e.g., Eugene Nida for dynamic equivalence, Edward Sapir for cultural review, Umberto Eco for editorial precision)
2. **Present** the selected figures with justification and ask for confirmation
3. **Generate** agents with rich Souls based on those experts' real methodologies
4. **Install** everything and confirm the office is ready

### Option 2: CLI

```bash
./swarm new-office oficina-research "Deep research and analysis"
./swarm add-agent oficina-research analyst "Primary research and data gathering"
./swarm add-agent oficina-research synthesizer "Connects findings into insights"
./swarm add-agent oficina-research critic "Validates methodology and conclusions"

# Edit each agent's .md file to customize the Soul, then:
./swarm install
```

## CLI reference

| Command | Description |
|---------|-------------|
| `./swarm new-office <name> "desc"` | Create a new office with pipeline template |
| `./swarm add-agent <office> <agent> "desc"` | Add an agent with Production + Critique modes |
| `./swarm remove-agent <office> <agent>` | Remove an agent |
| `./swarm list` | Show all offices, agents, and install status |
| `./swarm install` | Copy everything to `~/.claude/` |
| `./swarm uninstall` | Remove from `~/.claude/` |
| `./swarm sync` | Update routing table in Claude's memory |

## Project structure

```
claude-offices/
  swarm                          # CLI tool
  templates/
    office-skill.md              # Office template (2-round pipeline)
    agent.md                     # Agent template (Soul + 2 modes)
  skills/
    oficina-creator/SKILL.md     # Natural language creator with expert research
  offices/
    oficina-copywriting/         # Example office
      SKILL.md                   # Dispatcher skill
      agents/
        jordan-belfort.md        # First draft (high energy sales)
        emma-stratton.md         # Punchy filter (anti-jargon)
        ogilvy.md                # Final review (precision + elegance)
  docs/
    index.html                   # Visual documentation
```

## Architecture

```
User describes office in natural language
    ↓
/oficina-creator researches best domain experts
    ↓
Generates Soul per agent (based on real expert methodology)
    ↓
Creates SKILL.md (dispatcher) + Agent .md files
    ↓
Installs to ~/.claude/skills/ and ~/.claude/agents/
    ↓
Office available as /oficina-<name> in any Claude Code session
    ↓
When invoked, runs 2-round pipeline:
  Round 1 (produce) → Cross-critique (parallel) → Round 2 (rewrite + verdict)
```

## Example: Copywriting Office

The included `oficina-copywriting` demonstrates the full pattern:

- **Jordan Belfort**: First draft writer. High-energy sales copy using AIDA, PAS, BAB frameworks. In critique mode, evaluates sales force and urgency.
- **Emma Stratton**: Punchy filter. Kills jargon, enforces short sentences, demands specificity. In critique mode, scores punch, clarity, and residual jargon.
- **Ogilvy**: Final reviewer. Validates claims, checks persuasive structure, issues verdict. In critique mode, evaluates persuasive arc, claim precision, and elegance.

Pipeline: Jordan drafts → Emma filters → Ogilvy reviews → All 3 critique in parallel → Jordan rewrites with feedback → Emma re-filters → Ogilvy approves.

## Credits

- Architecture inspired by [Hermes Agent](https://github.com/NousResearch/hermes-agent) by [Nous Research](https://nousresearch.com/). Their Soul + Skills + Memory architecture provided the conceptual foundation. Claude Offices adapts the Soul (persistent agent identity) and Skills (procedural knowledge) patterns to work natively with Claude Code's sub-agent and skill system.
- Built for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) by [Anthropic](https://anthropic.com/).

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- macOS or Linux (bash 4+)
- No other dependencies

## License

MIT
