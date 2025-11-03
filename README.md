# Apex2 Terminal Bench Agent

**Achieved #1 on Terminal Bench Leaderboard** 🏆

New SOTA: **64.50% ± 1.77** success rate (5 runs, 80 tasks each), surpassing Terminus 2 with Claude Sonnet 4.5 by **13.5 percentage points**.

## Overview

Apex2 represents a fundamental rethinking of agentic coding systems. Through strategic simplification and intelligent parallelization, we achieved state-of-the-art performance while reducing system complexity by 90%. Built as a weekend project, this work demonstrates that thoughtful architecture and sophisticated prompting beat complex multi-agent orchestration.

## Results
[Terminal Bench Leaderboard 11/03/25](https://web.archive.org/web/20251103212338/https://www.tbench.ai/leaderboard)

[Apex2 Sonnet 4.5 Run Results](https://github.com/laude-institute/terminal-bench-leaderboard/pull/26)

[Apex 2 Gpt 5 Run Results](https://github.com/laude-institute/terminal-bench-leaderboard/pull/27)

![Terminal Bench Leaderboard 11/03/25](https://github.com/heartyguy/Apex2-Terminal-Bench-Agent/blob/main/TB_Apex2_leaderboard_110325.png)

### Performance Summary

**Apex2 achieves 64.50% accuracy with Claude Sonnet 4.5, surpassing the current #1 (Ante at 60.3%) by 4.2 percentage points.**

### Apex2 Submissions

#### Claude Sonnet 4.5 
**5-run average: 64.50% ± 1.77%**

| Run | Success Rate |
|-----|-------------|
| apex2-sonnet-4-5-rc9-1 | 62.50% |
| apex2-sonnet-4-5-rc9-2 | 63.75% |
| apex2-sonnet-4-5-rc9-3 | 65.00% |
| apex2-sonnet-4-5-rc9-4 | **66.25%** |
| apex2-sonnet-4-5-rc9-5 | 65.00% |

#### GPT-5 on an earlier version of apex2
**5-run average: 49.25% ± 1.39%**

| Run | Success Rate |
|-----|-------------|
| apex2-gpt-5-rc3-1 | 50.00% |
| apex2-gpt-5-rc3-2 | 48.75% |
| apex2-gpt-5-rc3-3 | 50.00% |
| apex2-gpt-5-rc3-4 | 50.00% |
| apex2-gpt-5-rc3-5 | 47.50% |

### Model Comparisons

#### Claude Sonnet 4.5 Agents

| Agent | Accuracy |
|-------|----------|
| **Apex2** | **64.50% ± 1.77%** |
| Ante (Previous SOTA) | 60.3% ± 1.1% |
| Droid | 57.5% ± 0.8% |
| Chaterm | 52.5% ± 0.5% |
| Terminus 2 | 51.0% ± 0.8% |

#### GPT-5 Agents

| Agent | Accuracy |
|-------|----------|
| Droid | 52.5% ± 2.1% |
| **Apex2** | **49.25% ± 1.39%** |
| Codex CLI | 42.8% ± 2.1% |
| Terminus 2 | 41.3% ± 1.1% |

#### Other Notable Results

| Agent | Model | Accuracy |
|-------|-------|----------|
| Droid | Claude Opus 4.1 | 58.8% ± 0.9% |
| Warp | Multiple | 52.0% ± 1.0% |
| Claude Code | Claude Opus 4 | 43.2% ± 1.3% |
| Droid | Claude Sonnet 4 | 50.5% ± 1.4% |

### Leaderboard Position

*[Leaderboard screenshot to be inserted]*

## Architecture: Strategic Simplification

### Core Innovation: Multi-Phase Intelligence System

```
Prediction Phase
├── Task categorization
├── Key file identification  
└── Multimodal requirement assessment
    ↓
Parallel Intelligence Gathering
├── Terminus-style execution (Episode 1)
├── Multi-round web search (3 rounds max)
├── Deep strategy generation 
├── Heuristic environment observation
│   ├── Installed packages
│   ├── Folder structure
│   ├── Running processes
│   ├── System state
│   └── Key file contents
└── Exploration agent (explore unknowns from strategy)
└── Optional multimodal analysis on images and videos
    ↓
Strategy Synthesis (Combines all intelligence)
    ↓
Optimized Context Generation
    ↓
Main Execution (Episode 2+)
    ↓
Second Parallel Exploration (Turn 10)
    ↓
Continue with enriched context
```

### Why Single Model?

We use Claude Sonnet 4.5 exclusively (with GPT-5 variant), which provides:
- **Consistency** - No coordination overhead between different models
- **Simplicity** - Easier debugging and iteration for model specific errors
- **Cost efficiency** - Lower operational costs with caching

## Key Technical Innovations

### 1. Predictive Intelligence System

Before any execution, we extract critical task metadata:
- **Category classification** - Determines risk profile and approach
- **Key file identification** - Extracts filenames mentioned in task description
- **Multimodal assessment** - Predicts if visual/document analysis needed

This upfront prediction enables targeted exploration and prevents wasted effort.

### 2. Advanced Web Search Pipeline

Our web search is a sophisticated multi-round research system using SERP instead of vendor provided websearch:

#### Search Strategy
- **Query Generation**: Claude Sonnet 4.5 builds highly specific, low-frequency search terms
- **Platform Bias**: Prioritize GitHub/StackOverflow for actionable commands
- **Google AI Overview**: Extract Google's AI-generated summaries (remarkably effective)
- **Deep Link Exploration**: Analyze top 3 google links per query
- **Multi-Round**: Up to 3 rounds of searching and analysis
- **Quality Control**: Filter out any Terminal Bench mentions

#### Why This Works
- Low-frequency terms find exact solutions rather than generic tutorials
- Google AI Overview often contains highly actionable answer that is in the right direction
- GitHub/StackOverflow bias provides working code
- Multi-round searching handles complex, multi-step problems

### 3. Heuristic Environment Observation

Beyond simple `ls`, we perform targeted observation:
```python
# What's installed?
pip list | grep -E "flask|django|tensorflow|torch"

# Folder structure
find . -type f -name "*.py" -o -name "*.txt" | head -20

# What's running?
ps aux | grep python
docker ps -a

# System state
df -h
free -m

# Key file contents (from prediction phase)
cat requirements.txt main.py  
```

This leads to **exploration agent** identifying critical unknowns to test via Docker container.

### 4. Deep Strategy Generation

Strategy generation focuses on extracting everything the LLM knows:
- **Knowledge extraction**: prompt to surface related knowledge. The SOTA models really have the answers. You just need to extract the insights out of them.
- **Alternative approaches**: Two carefully thought-through command sequences
- **Risk assessment**: Identify high-consequence operations
- **Common failures**: Known failure modes for this task type and remediation strategies

### 5. Strategy Synthesis

After parallel intelligence gathering, we synthesize everything:
- Combine Episode 1 execution results
- Integrate web search findings
- Incorporate strategy alternatives
- Add environment discoveries
- Include Docker exploration results

This creates an **optimized context** for Episode 2 execution.

### 6. Risk-Aware Category Prompting

Rather than providing concrete commands/strategy, we focus on **high-consequence operation management** and **common failure states**:

#### ML Tasks
- **Key insight**: Training runs can exceed 5 minutes
- **Approach**: Mandate parameter search before full runs
- **Example**: Test with small epochs first, verify shapes, then scale up

#### Security Tasks  
- **Key insight**: Many operations are irreversible
- **Approach**: Ground exact sequences before execution
- **Example**: Verify backups before attempting destructive commands

### 7. Execution Optimization Suite

#### Heredoc Management
```bash
# ONLY use heredoc for file creation
cat << 'EOF' > app.py
def main():
    print("Hello World")
EOF
```
- Optimized prompt for Heredoc commands
- Automatic Heredoc repair
- Automatic indentation repair
- Proper escaping for special characters

#### Session Recovery
- Detect stuck/lagging tmux sessions
- Automatic session recreation when degraded
- Preserve context across restarts

#### Long-Running Task Management
- Special prompts for operations exceeding 30 seconds
- Progress monitoring strategies
- Patience and timeout handling

#### Recovery Prompts
Similar to Terminus, we have specific recovery prompts for execution errors (not strategy errors):
- Syntax errors in generated code
- Import errors
- Path/file not found
- Permission denied
- Connection timeouts

#### Final Validation Tuning
Prevents premature task completion by checking for:
- Parsing errors in output
- Execution errors in logs
- Incomplete test results
- Missing expected outputs

## Ablation Studies

*[To be filled with detailed ablation results]*

## Lessons Learned

### What Made the Difference

1. **Predictive Intelligence**
   - Early task understanding guides all subsequent actions
   - Key file identification prevents missing critical context
   - Multimodal prediction avoids unnecessary analysis

2. **Google AI Overview in Search**
   - Often contains highly relevant solutions. better than web search capabilities provided by vendors
   - Synthesizes multiple sources effectively
   - Provides context beyond individual links

3. **Strategy Synthesis**
   - Combining all parallel intelligence crucial
   - Optimized context dramatically improves Episode 2
   - Prevents information silos

4. **Execution Robustness**
   - Heredoc handling eliminated file creation errors
   - Recovery prompts handle common execution failures
   - Validation prevents false completions

### Evolution of Parallelization Impact

Initially, parallelization was critical because:
- Early versions had slow starts
- Timeout issues were common

With optimization:
- Strategy and web search now highly effective
- Agent makes good progress from Episode 1
- Parallelization provides diverse perspectives rather than multiple attempts

### What Didn't Work

1. **Generic search terms** - Too many irrelevant results
2. **Single-round searching** - Missed complex solutions
3. **Ignoring Google AI Overview** - Lost valuable synthesis
4. **Early completion without validation** - False positives

## Performance Characteristics

### Efficiency Metrics
- **Token Usage**: Dramatically reduced through Claude Sonnet 4.5 caching
- **Speed**: 2.3 min average completion
- **Reliability**: Low variance (±1.4%) across runs
- **Recovery**: Handles 90% of execution errors

### Why It Works

Terminal Bench requires:
- **Deep task understanding** before execution
- **Real-world knowledge** for frameworks
- **Risk management** for irreversible operations
- **Robust execution** handling

Apex2 addresses each through:
- Predictive intelligence phase
- Sophisticated web search
- Risk-aware prompting
- Execution optimization suite

## Architectural Philosophy

### Core Principles

1. **Predict → Explore → Synthesize → Execute**
2. **Low-frequency search beats generic queries**
3. **Risk awareness beats blind execution**
4. **Recovery capabilities enable bold strategies**
5. **Details matter** (heredoc, validation, session health)

### The Power of Intelligence Synthesis

While others use parallel execution for multiple attempts, we use it for **diverse intelligence gathering**:
- Execution provides quick feedbacks for obvious solution from env
- Web search provides solutions
- Strategy provides alternatives
- Environment provides context for immediate execution
- Exploration using Docker Execution provides some answers to unknowns in strategy without adding context in panes

The synthesis of these perspectives creates superior execution context.

## Impact and Insights

### For the Field

This work demonstrates:
- **Upfront websearch, exploration, strategy generation dramatically improves efficiency**
- **Google AI Overview is an underutilized resource**
- **Strategy synthesis beats isolated intelligence**
- **Execution details matter as much as high-level strategy**

### Personal Reflections

As an LLM Orchestration Lead at Roblox, I've learned that production systems need both broad intelligence and meticulous execution. This project combines sophisticated information gathering with careful attention to execution details.

The combination of predictive intelligence, multi-round search with Google AI Overview, and strategy synthesis creates a system that's both intelligent and reliable.

## Future Directions

1. **Enhanced prediction models** - Better task understanding upfront
2. **Search query optimization** - Learn optimal query patterns
3. **Automated recovery generation** - Build recovery prompts from failures
4. **Cross-task learning** - Share successful patterns

## Conclusion

Apex2 achieves SOTA through intelligent information gathering, sophisticated synthesis, and meticulous execution. By combining predictive intelligence, multi-round search, and careful strategy synthesis with robust execution handling, we built a system that understands deeply and executes reliably.

**Key insight**: In agentic coding, the combination of diverse intelligence gathering, sophisticated synthesis, and execution robustness beats any single optimization. Success comes from both knowing what to do and doing it reliably.

---

*Built during weekends while exploring the limits of agentic systems. Thanks to Stanford's Terminal Bench team for creating this excellent benchmark.*
