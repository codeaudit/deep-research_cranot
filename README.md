# Deep Research

**Turn any question into multi-agent exploration.**

```
                              ┌─────────────────┐
                              │  YOUR QUESTION  │
                              └────────┬────────┘
                                       │
                                       ▼
                              ┌─────────────────┐
                              │  ORCHESTRATOR   │
                              │    (Claude)     │
                              └────────┬────────┘
                                       │
                    ┌──────────────────┼──────────────────┐
                    │                  │                  │
                    ▼                  ▼                  ▼
             ┌────────────┐     ┌────────────┐     ┌────────────┐
             │ Researcher │     │ Researcher │     │ Researcher │
             │    (1)     │     │    (2)     │     │   (...)    │
             └─────┬──────┘     └────────────┘     └─────┬──────┘
                   │                                     │
              ┌────┴────┐                           ┌────┴────┐
              ▼         ▼                           ▼         ▼
           ┌─────┐   ┌─────┐                     ┌─────┐   ┌─────┐
           │ Sub │   │ Sub │        ...          │ Sub │   │ Sub │
           └─────┘   └─────┘                     └─────┘   └─────┘

                         Agents spawn as many
                       sub-agents as needed (∞)

                                   │
                                   ▼
                              ┌─────────┐
                              │SYNTHESIS│
                              └─────────┘
```

*Multi-agent exploration*

```bash
./deep-research.sh "Why do smart people make bad decisions?"
```

Each agent autonomously decides: *break it down further* or *answer directly*.
Researchers run **in parallel**. Unlimited depth. Results flow back up into synthesis.

---

## Quick Start

```bash
git clone https://github.com/Cranot/deep-research.git
cd deep-research
chmod +x deep-research.sh

# Run it
./deep-research.sh "Your question here"
```

**Requires:** [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code)

---

## Example Reports

Real outputs from actual runs:

| Question | Config | Result |
|----------|--------|--------|
| [What makes great software architecture?](examples/software-architecture.md) | sonnet + haiku | 6 dimensions identified |
| [What is the key to learning fast?](examples/learning-fast.md) | sonnet + haiku | 5-principle framework |
| [Why do people self-sabotage?](examples/self-sabotage.md) | sonnet | Psychological deep-dive |
| [What makes people buy vs just admire?](examples/buy-vs-admire.md) | opus | Purchase psychology |

---

## Options

```bash
# Default: Opus orchestrator + Sonnet researchers
./deep-research.sh "Your question"

# Fast & cheap: Sonnet + Haiku
./deep-research.sh -m sonnet -r haiku "Your question"

# With web search (for current events)
./deep-research.sh --web "Latest developments in AI agents"

# Maximum depth: Sonnet + Sonnet (researchers can spawn more)
./deep-research.sh -m sonnet -r sonnet "Complex topic"
```

| Flag | What it does | Default |
|------|--------------|---------|
| `-m, --model` | Orchestrator model | opus |
| `-r, --researcher` | Researcher model | sonnet |
| `-w, --web` | Enable web search | off |

**Note:** Haiku researchers answer directly and won't spawn sub-researchers. Use `-r sonnet` if you want deeper recursion.

---

## Model Combinations

| Config | Depth | Speed | Cost | Best for |
|--------|-------|-------|------|----------|
| `-m opus -r sonnet` | Deep | Slow | $$$ | Best quality |
| `-m sonnet -r sonnet` | Deep | Medium | $$ | Good balance |
| `-m sonnet -r haiku` | Shallow | Fast | $ | Quick answers |

Costs vary by question complexity and depth. Budget accordingly.

---

## Output

Reports save automatically to:
```
reports/YYYY-MM-DD-your-question-slug/SYNTHESIS.md
```

---

## How It Works

The magic is one flag: `--allowedTools "Bash(claude:*)"`

This lets Claude spawn more Claude instances. Each instance gets the same "DNA":

```
Before answering, ask: are there multiple angles worth exploring?
- If YES → spawn sub-agents IN PARALLEL, wait for all, synthesize
- If NO → answer directly
Bias toward exploring. Go deep, not shallow.
```

Each agent spawns researchers for different angles:
```bash
claude -p "sub-question-1" --model sonnet ...
claude -p "sub-question-2" --model sonnet ...
claude -p "sub-question-3" --model sonnet ...
# collect all results, then synthesize
```

Recursive by nature. Each agent can spawn more. The tree grows until questions become atomic.

---

## Built by

[AgentsKB](https://agentskb.com) - Pre-researched knowledge for AI agents

## License

MIT
