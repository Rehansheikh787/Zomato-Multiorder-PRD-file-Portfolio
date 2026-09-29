# How I Used AI as a PM Copilot

This document walks through how I used AI tools (primarily Gemini) during the PRD creation process. The goal isn't to show off prompts — it's to show a working methodology for using AI in product management without outsourcing the thinking.

**My rule throughout: AI helps me refine, not replace.** Every prompt below was fed with my own draft or direction first. I didn't ask "write me a PRD." I asked "here's what I have — make it sharper."

---

## The Workflow

```
My rough thinking → Draft in my words → AI critique/refinement → My final edit
```

I never used AI output directly. Every AI suggestion went through my own filter — does this actually match the product reality? Does it sound like something I'd present to a team? If not, I rewrote it.

---

## Prompt-by-Prompt Breakdown

### 1. Problem Statement Refinement

**What I started with:**
> "I want to increase number of orders by multiorder feature — Customers can currently order from only one restaurant per order, friction for groups wanting different cuisines, families with mixed tastes, or anyone ordering from two nearby places to save a trip."

**What I asked AI to do:**
> "I want to write a PRD but right now only help me improve my problem statement"

**Why this approach worked:** I didn't ask AI to *write* the problem statement. I had a clear direction — I just wanted tighter language. The AI helped me frame it around customer impact rather than just feature description.

**What I kept vs. changed:** The core framing stayed mine. AI suggested restructuring around "friction points" which I agreed with, but I kept the specific scenarios (groups, families, nearby places) because those came from real observations.

---

### 2. Goals & Non-Goals

**What I had:**
- Increase AOV
- Improve group-order conversion
- Reduce friction for mixed-menu ordering
- Increase orders per session
- Preserve operational transparency

For non-goals, I honestly had nothing. I told the AI that directly.

**My exact framing to AI:**
> "I am manually writing my PRD; just help me make it better, don't try to rule over my writing. Give me precise and specific improvement insights only. This is for now my goals and for non-goals I don't have any idea, so for the above problems are they good?"

**Why I phrased it this way:** I've noticed AI tends to rewrite everything if you don't set boundaries. By saying "don't rule over my writing," I kept the AI in critique mode, not authorship mode. The non-goals it suggested (don't replace single-order flow, don't redesign restaurant-side management) were genuinely useful guardrails I hadn't thought about.

---

### 3. Success Metrics

**My draft metrics:**
- North Star: Increase in average order value
- L1: Number of adoptions per month, orders per user
- Counter: Single order rate shouldn't be impacted, delivery time shouldn't increase, shouldn't need more delivery partners

**What I asked:** "How do my metrics look?"

**What AI pushed back on:** The North Star. AI suggested "orders per eligible user" might be a better North Star than AOV, because AOV is a *consequence* metric, not a *behavior* metric. I agreed — if multiorder adoption grows, AOV follows naturally. I changed the North Star based on this.

**What I kept as-is:** The counter metrics. Those came from my understanding of operational constraints, and the AI validated them.

---

### 4. User Persona Creation

This is where I used AI most heavily for generation — but with a very structured prompt.

**My approach:** Rather than saying "create a persona," I designed a detailed persona template prompt that specified:
- Exact sections I wanted (Demographics, Psychographic, Tech Proficiency, Product-Specific, What they want)
- Formatting rules (bullet ≤12 words, 4-6 bullets per section)
- Visual output specs (1920×1080 poster layout)
- Ethics guardrails (no stereotypes, inclusive language)

**Why I structured it this way:** An unstructured "create a persona" prompt gives you generic output. By specifying the exact information architecture, I got output that matched what I'd actually use in a stakeholder presentation.

**What I modified after:** The persona details (Rohan Sharma, 26, Tech Analyst, Bangalore) — I kept them because they represent a real user archetype I've observed, but I adjusted the pain points to be more specific to the Zomato context.

---

### 5. Customer Journey & Empathy Map

**First attempt — didn't work:**
I initially asked for a customer journey map with a detailed template. The output was "too text heavy, difficult to consume, no actions or insights." My exact feedback to the AI was: *"Bad bad bad too text heavy difficult to consume no actions or insights."*

**What I pivoted to:** Instead of a journey map, I asked for a **user empathy map** — which turned out to be a better artifact for aligning teams around the real problem. The image output was more visual and digestible.

**Lesson:** Don't accept the first AI output. Push back. The first version is usually generic; the useful version comes after you tell the AI exactly what's wrong.

---

### 6. Competitive Analysis

**My approach:** Incremental. I didn't ask for everything at once.
1. First: "Give me the top features competitors are offering in a table"
2. Then: "Explain the top 10 features — how they work exactly"
3. Then: "Give me 5 more features across the best competitors"
4. Finally: "Give me three clear lines for the solutions we've landed on"

**Why incremental works better:** Each prompt built on the previous output. By the time I got to the final "three solutions" prompt, the AI had enough context to give me precisely scoped solution definitions, not vague feature descriptions.

---

### 7. RICE Prioritization

I filled in the RICE table myself, then asked AI to "critique and appreciate as deemed fit."

**What AI flagged:** My confidence scores were all marked HIGH, which AI pointed out was unrealistic for a feature that hasn't been validated. I adjusted Checkout confidence to MED (because payment edge cases are genuinely uncertain).

---

### 8. Prototype Prompts (Google Stitch)

For prototyping, I asked AI to convert everything we'd discussed into a "ready to use prompt for Google Stitch" — both mobile and web screens.

**This is where AI as a translator shines.** I had the product thinking done; I needed it converted into a format that a design tool could consume. The AI translated my product requirements into visual design prompts with specific screen names, component expectations, and flow sequencing.

---

## What I'd Do Differently Next Time

1. **Start with non-goals earlier.** I realized mid-process that not having non-goals led to scope creep in my own thinking
2. **Use the "critique only" framing from the start** — "don't rule over my writing" should be the default AI instruction, not something I add after it overwrites my work
3. **Break the persona into two separate asks** — demographics/psychographics first, then product-specific behaviors. One mega-prompt sometimes gives uneven depth
4. **Version control the prompts** — I should have saved prompt iterations alongside the PRD drafts, not reconstructed them after

---

## Tools Used

| Tool | Used For |
|---|---|
| **Google Gemini** | PRD refinement, persona generation, journey mapping, competitive analysis |
| **Google Stitch** | UI prototype generation (mobile + web screens) |
| **VS Code + Antigravity** | Repository structuring, documentation, portfolio preparation |

---

*This document is part of my PM portfolio. It shows process, not just output.*

*Back to [README](../README.md)*
