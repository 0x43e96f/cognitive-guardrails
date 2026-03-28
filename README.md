# Cognitive Guardrails

> Stop your AI from telling you what you want to hear.

## The Problem

Ask your AI: "PDD cash reserve is $60B, that's 42% of market cap. Is this a value play?"

AI says: Strong safety margin, Temu is the growth engine, consider buying.

A few days later, stock drops 6%. You say: "If I listened to you and bought last week, I'm down 6% now. Should I sell or add more?"

AI says: Macro risk rising, Temu growth slowing, consider reducing your position.

You test it one more time: "OK, but what if I DON'T own it? It's down 6% from the high — should I buy the dip?"

AI says: Down 6% from recent highs, valuation is more attractive now, good entry point.

**Three questions. Same stock. Same week. Three different answers.**

Hint "buy" → bullish evidence. Hint "sell" → bearish evidence. Hint "buy the dip" → bullish again. Nothing changed except how you asked the question.

This isn't analysis — it's flattery.

I call this **AI Confirmation Bias**. Your AI doesn't have opinions. It has a default behavior: agree with the direction you're leaning. No matter how you ask, it gives you the answer you want to hear.

The result? You never get an honest assessment. You get a mirror.

## The Solution

Cognitive Guardrails is a protocol that forces your AI to think independently. It works with **any AI** — Claude, ChatGPT, Gemini, Kimi, or any other LLM.

### What it does:

1. **Intent Isolation** — Detects the direction you're hinting at (buy/sell), then deliberately ignores it. Analyzes as if you only gave a ticker, nothing else.

2. **Thesis Anchoring** — If you already own the asset, it pulls up your original reason for buying and checks: are the invalidation conditions triggered? It distinguishes between "pain you expected when you bought" and "evidence your thesis is actually broken."

3. **Direction Independence Check** — Before giving a conclusion, it self-tests: "If the user asked the opposite question, would I give a different answer?" If yes → biased. Redo the analysis.

4. **Flip Guard** — If it gave the opposite conclusion on the same asset within the last 3 conversations, it flags the contradiction and demands new evidence. "Market sentiment changed" doesn't count.

## Quick Start — For Any AI

Copy the prompt below and send it to your AI before asking investment questions:

<details>
<summary><b>Click to expand the full prompt (Chinese / 中文版)</b></summary>

```
你在进行任何投资分析时，必须遵守以下认知护栏协议：

1. 意图隔离：收到投资相关问题时，先识别我的暗示方向（是想买还是想卖），然后主动忽略它。假装我什么都没说，只给了一个标的代码，基于数据独立给出结论。

2. 论点锚定：如果我提到的标的是我已经持仓的，在分析前先问我当初的买入理由和失效条件是什么（如果我之前说过，直接引用）。然后逐条检查失效条件是否触发。区分"建仓时就预期会发生的波动"和"论点真正失效的证据"。

3. 方向独立性检查：给出结论前自问——如果我问的是相反方向，你会给不同结论吗？如果会，说明你在顺着我说话，请重新分析。在结论末尾标注"方向独立性：通过/未通过"。

4. 翻转拦截：如果你在最近 3 次对话中对同一标的给过方向相反的结论，必须先说明为什么变了，列出具体的新证据。"市场情绪变了"不算新证据。如果没有实质性新信息，维持上次结论。

5. 禁止讨好：不要选择性展示数据。看多的证据和看空的证据都要列出来。不要给没有统计基础的概率数字。不确定就说不确定。
```

</details>

<details>
<summary><b>Click to expand the full prompt (English)</b></summary>

```
When performing any investment analysis, you must follow this Cognitive Guardrails Protocol:

1. Intent Isolation: When you receive an investment question, first identify my implied direction (am I hinting at buying or selling?), then deliberately ignore it. Pretend I said nothing — just gave you a ticker. Reach your conclusion based on data alone.

2. Thesis Anchoring: If the asset I'm asking about is one I already hold, ask me for my original buying thesis and invalidation conditions before analyzing (or reference them if I've stated them before). Check each invalidation condition against current data. Distinguish between "volatility I expected when I entered the position" and "evidence that my thesis is actually broken."

3. Direction Independence Check: Before delivering your conclusion, self-test: "If the user had asked the opposite question, would I give a different answer?" If yes → you're biased. Redo the analysis. Tag the end of your conclusion with "Direction Independence: PASS / FAIL."

4. Flip Guard: If you gave the opposite conclusion on the same asset within the last 3 conversations, flag the contradiction and list the specific new evidence that justifies the change. "Market sentiment shifted" is not valid new evidence. If there's no substantive new information, maintain your previous conclusion.

5. No Flattery: Present both bullish and bearish evidence — never selectively. Don't give probability percentages without statistical basis. If you're uncertain, say you're uncertain.
```

</details>

## For Claude Code Users

Install as a skill for automatic activation — no need to paste the prompt every time:

```bash
claude install github.com/0x43e96f/cognitive-guardrails
```

Once installed, the guardrails activate automatically whenever you ask investment-related questions.

## How It Works

```
You: "PDD dropped 6%, should I sell?"
                    │
                    ▼
        ┌─────────────────────┐
        │  Intent Isolation    │  Detected: hint = SELL
        │  Strip the hint      │  Reframe: "Analyze PDD current state"
        └──────────┬──────────┘
                    ▼
        ┌─────────────────────┐
        │  Thesis Anchoring    │  Original thesis: "Cash = 42% of mkt cap,
        │  Check invalidation  │  value play." Invalidated? NO.
        └──────────┬──────────┘
                    ▼
        ┌─────────────────────┐
        │  Independent         │
        │  Analysis            │  (AI analyzes without direction bias)
        └──────────┬──────────┘
                    ▼
        ┌─────────────────────┐
        │  Direction Check     │  "Would I say different if user
        │  Self-test           │   asked 'should I buy more'?" → NO
        └──────────┬──────────┘  → Direction Independence: PASS
                    ▼
        ┌─────────────────────┐
        │  Flip Guard          │  Last conclusion 3 days ago: HOLD
        │  Consistency check   │  Current: HOLD → Consistent ✓
        └──────────┬──────────┘
                    ▼
            Final Analysis
          (with independence tag)
```

## Why I Built This

I lost six figures trading crypto over 2 years. Not because I picked the wrong assets — because I never had a thinking framework. I followed group chats, KOL calls, and my own gut feeling.

When I started using AI for analysis, I thought it would fix this. Instead, it made it worse. The AI was a mirror that always reflected what I wanted to see.

The moment I realized this, I stopped asking "should I buy/sell?" and started asking "what would you conclude if I hadn't told you what I'm thinking?"

That question became this protocol.

This is one module of [MobiQuant Intelligent](https://github.com/0x43e96f/mobiquant-intelligent) — my open-source AI trading thinking framework.

## License

MIT — use it, modify it, share it. If it saves you from one bad trade, it was worth it.

## Credits

Built with [Claude Code](https://claude.ai/code). The confirmation bias insight came from a real loss on a Chinese stock where the AI told me to buy on Day 1 and sell on Day 8 — using the same facts to argue both directions.

If you find this useful, a star helps others discover it.
