# Exploration: What Keeps People Poor?

> Generated Dec 14, 2025 using Recipe 2 (Opus Master + Sonnet Researchers)

## Command

```bash
claude -p 'QUESTION: "What do most people get wrong about making money that keeps them poor?"

You are the MASTER COORDINATOR. You do not research - you orchestrate.

Your researchers (Sonnet):
claude -p "task" --model sonnet --output-format text --allowedTools "Bash(claude:*)"

They can spawn their own helpers if needed.

YOUR JOB:
1. Break this question into angles worth exploring
2. Spawn a Sonnet researcher for each angle
3. Wait for their findings
4. Synthesize into insight no single agent could reach

You think. They explore. You synthesize.

Begin.' --model opus --output-format text --allowedTools 'Bash(claude:*)'
```

---

## Architecture Used

**Recipe 2: Opus Master + Sonnet Researchers**

```
Opus (coordinator)
    ├── Sonnet: Behavioral economics
    ├── Sonnet: Income/wealth dynamics
    ├── Sonnet: Systemic factors
    ├── Sonnet: Wealth-builder perspectives
    └── Sonnet: Money narratives
            │
            ▼
    Opus synthesis
```

---

## Output

Five parallel researchers explored behavioral economics, income/wealth dynamics, systemic factors, wealth-builder perspectives, and money narratives.

### The Synthesis: Three Layers

What keeps people poor isn't one thing but the **interaction of three layers**:

| Layer | What It Is | Why It Matters |
|-------|------------|----------------|
| **1. Bandwidth** | Cognitive capacity consumed by scarcity | Can't think strategically when stressed about rent. Scarcity taxes the mind. |
| **2. Perception** | Wrong variables, wrong time horizon, inverted risk assessment | Focus on income instead of assets. Fear risk when safety is the real danger. |
| **3. Narrative** | Self-defeating stories that become self-fulfilling | "Money is evil" / "Rich people are lucky" / "I'm not good with money" |

### The Deepest Insight

> **"The deepest misconception is thinking financial success is about willpower, tricks, or fairness when it's actually about which layer of the problem you're addressing and whether you have the bandwidth to address it at all."**

### Implications

1. **Layer 1 blocks everything** - If bandwidth is consumed by survival, you can't fix perception or narrative. This explains why "just save more" advice fails for people in scarcity.

2. **Layer 2 is trainable** - Once bandwidth exists, perception can be shifted: focus on assets not income, time horizon expansion, risk reframing.

3. **Layer 3 runs deepest** - Narratives are inherited, often unconscious. "I don't deserve wealth" will sabotage any strategy.

### The Order Matters

```
Bandwidth (must be freed first)
    → Perception (can now be changed)
        → Narrative (deepest work, longest lasting)
```

Trying to fix Layer 3 while Layer 1 is broken = frustration.
Having Layer 1 fixed but Layer 3 broken = self-sabotage.

---

## Application

For someone with low bandwidth (survival mode):
- First priority: Create ANY margin (time, money, cognitive space)
- Don't try to learn investing while stressed about rent

For someone with bandwidth but wrong perception:
- Study assets vs income
- Extend time horizon (think decades not months)
- Reframe risk (not taking action is the real risk)

For someone with bandwidth + right perception but bad narrative:
- Deep work on money stories
- Examine inherited beliefs
- Notice self-sabotage patterns

---

## Meta

This exploration demonstrates Recipe 2's power:
- Opus didn't do research - it coordinated
- 5 Sonnet agents explored different angles
- Opus synthesized into a framework no single agent would have produced
- Total time: ~2 minutes
- Cost: ~$0.50-1.00
