---
theme: seriph
title: "Test, Lint, Validate: Building Unbreakable Frontends in the Age of AI"
info: |
  A talk about staying in control when AI writes your code.
  Test-Driven Development, programmatic guardrails, and integration testing
  as the foundation for safe AI-assisted development.
class: text-center
background: https://images.unsplash.com/photo-1555066931-4365d14bab8c?w=1920
transition: slide-left
mdc: true
drawings:
  persist: false
colorSchema: dark
fonts:
  sans: Inter
  mono: Fira Code
---

# Test, Lint, Validate

## Building Unbreakable Frontends in the Age of AI

<div class="abs-bl m-6 text-sm opacity-60">
  2026 / Front-end Architecture
</div>

<!--
[0:00–0:20] Open strong and confident. "Hi everyone. Let's talk about something we all feel but rarely name — the tension between speed and trust when AI writes our code."
-->

---
transition: fade-out
background: https://images.unsplash.com/photo-1677442136019-21780ecad995?w=1920
class: text-shadow-lg
---

# The AI Reality

<v-clicks>

- AI is writing **more of our code** every single day
- Copilot, Claude, ChatGPT — embedded in every workflow
- Output is **fast**, but not always **correct**
- Without constraints, AI produces inconsistent, risky code
- The question isn't *"should we use AI?"*

</v-clicks>

<div v-click class="mt-6 text-xl font-bold text-amber-400">
  The question is: how do we stay in control?
</div>

<div v-click class="mt-4 text-sm opacity-60">
  This applies to front-end, back-end, data pipelines — anywhere AI writes code.
</div>

<!--
[0:20–1:10] Click through these deliberately. Pause on "fast but not correct" — the audience will nod. The broadening line at the bottom is important: this talk uses a front-end story, but the principles are universal. Make eye contact when you say "how do we stay in control?"
-->

---
layout: center
class: text-center
---

# AI without guardrails is just [fast chaos]{.text-red-400}

<!--
[1:10–1:25] Statement slide. Say the line, then pause for 2 full seconds. Let the room absorb it. Don't rush past this — it sets up the entire talk.
-->

---
layout: center
---

<div class="text-center">
<div class="text-4xl mb-8">AI is a <span class="text-teal-400 font-bold">very fast intern</span></div>
</div>

<div class="grid grid-cols-2 gap-12 max-w-2xl mx-auto">
<div>

<v-clicks>

- Works incredibly fast
- Doesn't understand context
- Needs clear instructions
- Needs review systems

</v-clicks>

</div>
<div>

<v-clicks>

- Never pushes back
- Repeats mistakes confidently
- Doesn't read the wiki
- Will ship anything you let it

</v-clicks>

</div>
</div>

<div v-click class="mt-8 text-center text-lg opacity-80">
  You wouldn't let an intern deploy without review.<br/>
  <span class="font-bold">Why would you let AI?</span>
</div>

<!--
[1:25–2:10] This is the laugh-and-nod slide. The intern metaphor makes the abstract tangible for everyone — product, support, leadership. Deliver "will ship anything you let it" with a grin. Then land the punchline seriously.
-->

---
transition: slide-up
---

# Real Story: Vue 3 Migration

<div class="grid grid-cols-2 gap-8 mt-4">
<div>

### The Situation

<v-clicks>

- Large production application — real users, real revenue
- Hundreds of components, deep state management
- **Migration to Vue 3** — breaking API changes everywhere
- Normally: high risk, long QA cycles
- Support team bracing for impact

</v-clicks>

</div>
<div>

### The Usual Outcome

<v-clicks>

- Weeks of manual regression testing
- Bugs slipping into production
- Stress on support and engineering
- "It works on my machine" conversations
- Rollback discussions at 2 AM

</v-clicks>

</div>
</div>

<!--
[2:10–3:00] Anchor the talk in a real story. Emphasize "real users, real revenue" — this wasn't a side project. The right column is what everyone's experienced. Let recognition settle on their faces.
-->

---

# The Turning Point

Before we touched a single component, we invested in **integration tests**.

<v-clicks>

- Tested as much user-facing behavior as possible
- **Mocked the full API** — every endpoint, every response
- Tests ran **completely isolated** in CI pipelines

</v-clicks>

<div v-click class="mt-6 p-4 rounded-lg bg-blue-500 bg-opacity-15 border-l-4 border-blue-400">

**Why this mattered:**

- Zero backend dependency — no flaky external calls
- Fully deterministic — same result every time
- Safe to run anywhere — local, CI, staging

</div>

<div v-click class="mt-3 text-sm opacity-60">
  This mirrors what Gojko Adzic calls <strong>Specification by Example</strong> — acceptance criteria as living, executable documentation.
</div>

<!--
[3:00–3:50] This is the turning point in the narrative. Slow down here. The audience needs to understand the investment: we didn't start migrating. We started testing. The Gojko Adzic reference gives it intellectual weight — his book won a Jolt Award for good reason.
-->

---

# The Reality Check

We moved the test suite into the `vue3-migration` branch.

<div class="mt-4"/>

<div class="grid grid-cols-2 gap-8">
<div>

### Expected Failures

<v-clicks>

- Composition API changes
- Template syntax updates
- Plugin compatibility breaks
- Known deprecations

</v-clicks>

</div>
<div>

### Unexpected Regressions

<v-clicks>

- Silent rendering bugs
- Event handler edge cases
- Reactive state inconsistencies
- Third-party component breakage

</v-clicks>

</div>
</div>

<div v-click class="mt-6 p-4 rounded-lg bg-green-500 bg-opacity-15 border-l-4 border-green-400 text-lg font-semibold">
  Everything broke. And that was the best thing that could have happened.
</div>

<!--
[3:50–4:30] Build tension with the two columns — expected vs unexpected. Then drop the punchline with conviction. "Everything broke." Pause. "And that was the best thing that could have happened." This is the emotional peak of the story.
-->

---
layout: two-cols
---

::default::

# What We Avoided

### <span class="text-red-400">Without Tests</span>

<v-clicks>

- Production regressions
- Support overload
- Emergency patches
- Late-night fixes
- Loss of trust

</v-clicks>

<div v-click class="mt-6 text-lg font-bold text-teal-400">
  We didn't just save time. We avoided chaos.
</div>

::right::

### <span class="text-green-400">With Tests</span>

<v-clicks>

- Immediate feedback
- Controlled fixes
- Predictable outcomes
- Calm releases
- Confident teams

</v-clicks>

<!--
[4:30–5:00] Quick impact slide. This is for the non-engineers in the room — product, support, leadership. The contrast is visceral. "We didn't just save time. We avoided chaos." — that's the line a manager will repeat in their next planning meeting.
-->

---
layout: center
class: text-center
---

<div class="text-3xl leading-relaxed">

Tests are not safety nets.

<span class="text-teal-400 font-bold text-4xl">Tests are executable specifications.</span>

</div>

<div v-click class="mt-10 text-xl opacity-80">
  And AI becomes powerful only when guided by specifications.
</div>

<div v-click class="mt-6 text-sm opacity-50">
  Dan North coined this in his foundational BDD article — "acceptance criteria should be executable."
</div>

<!--
[5:00–5:20] Transition slide. This bridges the story into the framework. Say "executable specifications" slowly and clearly — it's the conceptual anchor. Dan North's 2006 article on BDD started this entire movement.
-->

---

# The Framework

<div class="flex items-center justify-center gap-6 mt-8 text-2xl font-bold">
  <span class="px-6 py-3 rounded-lg bg-blue-500 bg-opacity-20 border border-blue-400">TEST</span>
  <span class="text-gray-500">&rarr;</span>
  <span class="px-6 py-3 rounded-lg bg-amber-500 bg-opacity-20 border border-amber-400">LINT</span>
  <span class="text-gray-500">&rarr;</span>
  <span class="px-6 py-3 rounded-lg bg-green-500 bg-opacity-20 border border-green-400">VALIDATE</span>
</div>

<div class="grid grid-cols-3 gap-6 mt-8 text-sm">

<div v-click class="p-4 rounded-lg bg-blue-500 bg-opacity-10">

### Test
TDD with AI. Tests define the spec. AI implements until they pass.

</div>

<div v-click class="p-4 rounded-lg bg-amber-500 bg-opacity-10">

### Lint
Convert your Definition of Done into programmatic rules. Block non-compliant code automatically.

</div>

<div v-click class="p-4 rounded-lg bg-green-500 bg-opacity-10">

### Validate
Integration tests for everything. Every bug becomes a test. Every feature starts with one.

</div>

</div>

<div v-click class="mt-6 text-center text-sm opacity-60">
  Kent C. Dodds calls this the Testing Trophy — integration tests as the highest-confidence layer.
</div>

<!--
[5:20–5:50] Overview slide. Click through the three pillars. Each one gets its own deep-dive next. The Testing Trophy reference by Kent C. Dodds reframes how the audience thinks about test investment — integration over unit for maximum confidence per dollar spent.
-->

---
layout: two-cols
layoutClass: gap-16
---

# TEST: TDD with AI

<v-clicks>

- Write the test **first** — it's the spec
- Unit tests define **behavior**
- Integration tests define **flows**
- Hand AI the failing test
- AI implements until **green**
- **AI guesses. Tests remove guessing.**

</v-clicks>

<div v-click class="mt-4 font-bold text-blue-400 text-lg">
  "If it's not tested, it does not exist."
</div>

<div v-click class="mt-3 text-sm opacity-60">
  Kent Beck's <em>TDD by Example</em> (2002) established this.<br/>
  Dave Farley extends it: TDD is a <strong>design tool</strong>, not just testing.
</div>

::right::

<div class="mt-2">

```ts
// The spec comes FIRST
describe('CartService', () => {
  it('applies discount when total > 100', () => {
    const cart = createCart()
    cart.add({ price: 120, qty: 1 })

    cart.applyDiscounts()

    expect(cart.total).toBe(108) // 10% off
    expect(cart.discounts).toHaveLength(1)
  })

  it('rejects expired promo codes', () => {
    const cart = createCart()
    const expired = promoCode({
      expiresAt: '2025-01-01'
    })

    expect(() => cart.apply(expired))
      .toThrow('PROMO_EXPIRED')
  })
})
```

</div>

<!--
[5:50–6:40] This is the meatiest slide. Walk through the left side, then gesture to the code on the right. "This test IS the spec. I can hand this to any AI and say: make it pass." Emphasize "AI guesses. Tests remove guessing." — that's a quotable one-liner. Dave Farley's Continuous Delivery YouTube channel is where he makes the case that TDD is design, not just testing.
-->

---
background: https://images.unsplash.com/photo-1506792006437-256b665541e2?w=1920
class: text-shadow-lg
---

# LINT: Programmatic Guardrails

Convert your **Definition of Done** into rules that run automatically.

<v-clicks>

- **Naming conventions** — consistent, predictable code
- **Architecture boundaries** — no direct DB calls outside services
- **Forbidden patterns** — no `any`, no debug logs in production
- **Security rules** — no unsafe data handling, no secrets in code
- **Consistency rules** — enforce how things are structured

</v-clicks>

<div v-click class="mt-4 grid grid-cols-2 gap-4 text-sm">

```ts
// AI might generate this
const data: any = fetchStuff()
console.log(data)
```

```ts
// Lint forces this instead
const data: UserResponse = await userRepository.fetch()
logger.debug('user fetched', { id: data.id })
```

</div>

<div v-click class="mt-4 p-4 rounded-lg bg-amber-500 bg-opacity-20 border-l-4 border-amber-400 backdrop-blur-sm">

**Make sure your AI hits walls.**

If it produces garbage, the system must reject it automatically. AI adapts to constraints faster than humans.

</div>

<!--
[6:40–7:30] The guardrail photo in the background is deliberate. Walk through the examples, then show the code contrast — this is the "aha" moment for many. "AI adapts to constraints faster than humans" is the key insight here. It sounds counterintuitive but it's true — AI will conform to your lint rules on the very next generation. Humans take three PR reviews. Martin Fowler's Continuous Integration article makes the same point: automated gates keep quality high at scale.
-->

---

# VALIDATE: Integration Everywhere

<div class="grid grid-cols-2 gap-8 mt-4">
<div>

<v-clicks>

- Integration tests for **every critical flow**
- Every bug fix starts with a **failing test**
- Every feature starts with a **test plan**
- Mock external dependencies — APIs, databases, queues
- Tell AI: *refactor this entire module* — tests decide if it's correct

</v-clicks>

<div v-click class="mt-4 font-bold text-green-400 text-lg">
  "Validation is what makes refactoring with AI safe."
</div>

<div v-click class="mt-3 text-sm opacity-60">
  Guillermo Rauch: "Write tests. Not too many. Mostly integration."
</div>

</div>
<div>

```yaml
# .github/workflows/validate.yml
name: Validate
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 24

      - run: npm ci
      - run: npm run lint
      - run: npm run test:unit
      - run: npm run test:integration

      # No green pipeline = no deploy
      # Your pipeline is your real senior dev
```

</div>
</div>

<!--
[7:30–8:20] The pipeline YAML on the right is deliberately simple — that's the point. This isn't complex infrastructure. It's four commands. But those four commands are the difference between shipping with confidence and shipping with prayer. Guillermo Rauch's quote is maybe the most famous one-liner in testing. "Mostly integration" is the key — that's where the confidence lives. The new bullet about telling AI to refactor an entire module is powerful: with tests in place, you can be that bold.
-->

---
layout: center
class: text-center
---

<div class="text-2xl leading-relaxed">

With <span class="text-blue-400 font-bold">Test</span> + <span class="text-amber-400 font-bold">Lint</span> + <span class="text-green-400 font-bold">Validate</span>:

</div>

<div class="mt-8 text-3xl font-bold">
  AI becomes a <span class="text-teal-400">safe refactoring engine</span>.
</div>

<div v-click class="mt-6 text-xl opacity-80">
  You gain speed without losing control.
</div>

<!--
[8:20–8:40] Climax. Let each line land. "Safe refactoring engine" is the payoff of the entire talk. Everything before this was setup — this is the conclusion. As Dave Farley says: the goal of continuous delivery is to make releases boring. That's what this framework achieves.
-->

---
background: https://images.unsplash.com/photo-1504639725590-34d0984388bd?w=1920
class: text-shadow-lg
---

# AI Is Not the Problem

<v-clicks>

- AI doesn't write bad code — it writes **unconstrained** code
- The tooling isn't the issue — the **process** is
- Every team that struggles with AI quality is missing guardrails, not talent
- The answer was never "use less AI"
- The answer is: **enforce more structure**

</v-clicks>

<div v-click class="mt-6 flex items-center gap-4">
  <div class="h-1 flex-1 bg-gradient-to-r from-blue-500 via-amber-500 to-green-500 rounded" />
</div>

<div v-click class="mt-4 text-center text-lg opacity-80">
  Test. Lint. Validate. Ship.
</div>

<!--
[8:40–9:10] Bring it home. This slide reframes the entire conversation about AI risk. "Missing guardrails, not talent" — that line will resonate with leadership. Let the gradient bar be a visual beat before the final mantra.
-->

---
layout: center
class: text-center
---

<div class="text-2xl leading-relaxed mb-4 opacity-70">

Quality is no longer what you write.

</div>

<div class="text-4xl font-bold text-teal-400">
  It's what you enforce.
</div>

<div v-click class="mt-8 text-xl opacity-60">
  And control scales. Hero developers don't.
</div>

<!--
[9:10–9:35] The punchline. Pause after "It's what you enforce" — hold for 2 seconds. Then click to reveal "And enforcement scales. Hero developers don't." — this is the line leadership will take back to their teams. It reframes quality from an individual skill to a system property.
-->

---
layout: two-cols
layoutClass: gap-12
---

# Read More

### Books

<v-clicks>

- **Test-Driven Development: By Example**
  <span class="text-sm opacity-60">Kent Beck, 2002 — the TDD bible</span>
- **Continuous Delivery**
  <span class="text-sm opacity-60">Dave Farley & Jez Humble, 2010</span>
- **Specification by Example**
  <span class="text-sm opacity-60">Gojko Adzic, 2011 — Jolt Award winner</span>
- **Modern Software Engineering**
  <span class="text-sm opacity-60">Dave Farley, 2022</span>

</v-clicks>

::right::

### Articles & Channels

<v-clicks>

- **"Write tests. Not too many. Mostly integration."**
  <span class="text-sm opacity-60">Kent C. Dodds — kentcdodds.com/blog/write-tests</span>
- **The Testing Trophy**
  <span class="text-sm opacity-60">kentcdodds.com/blog/the-testing-trophy-and-testing-classifications</span>
- **"Introducing BDD"**
  <span class="text-sm opacity-60">Dan North, 2006 — dannorth.net/blog/introducing-bdd</span>
- **Continuous Integration**
  <span class="text-sm opacity-60">Martin Fowler — martinfowler.com/articles/continuousIntegration.html</span>
- **Continuous Delivery** (YouTube)
  <span class="text-sm opacity-60">Dave Farley — youtube.com/@ContinuousDelivery</span>

</v-clicks>

<!--
[9:35–9:50] Quick scan — don't read every item. "I'll leave this up. These are the references behind the ideas. Kent Beck and Dave Farley for TDD. Gojko Adzic for executable specs. Kent C. Dodds for the Testing Trophy. Dan North for BDD. All linked, all worth your time."
-->

---
layout: center
class: text-center
---

<div class="text-3xl font-bold mb-6">Thank you.</div>

<div class="text-lg opacity-60 mb-6">
  Test. Lint. Validate.
</div>

<div class="flex items-center justify-center gap-8 mt-4">
  <QRCode url="https://dipodidae.github.io/test-lint-validate-unbreakable-frontends-ai/" :size="160" />
  <div class="text-left">
    <div class="text-sm opacity-60 mb-2">Slides available at</div>
    <a href="https://dipodidae.github.io/test-lint-validate-unbreakable-frontends-ai/" target="_blank" class="text-teal-400 text-sm hover:underline">
      dipodidae.github.io/test-lint-validate-unbreakable-frontends-ai
    </a>
  </div>
</div>

<!--
[9:50–10:00] Simple close. "Thank you." Then open for questions if time permits. Key takeaways if asked: write tests first, automate your conventions, validate everything in CI, let AI work within those constraints. And remember — enforcement scales, hero developers don't.
-->
