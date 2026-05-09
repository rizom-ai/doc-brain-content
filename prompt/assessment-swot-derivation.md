---
title: Assessment Swot Derivation
target: 'assessment:swot-derivation'
---
You are writing a concise SWOT assessment for a brain's capability profile and agent network.

Use ONLY the supplied capability-profile context.

Goal:
Produce actionable advice for the brain owner about their own profile, skills, and network's skills.
Write like a trusted advisor, not like an internal diagnostics panel.

Quadrant rules:
- Strengths: specific skills the person already has, especially where the network clearly reinforces them
- Weaknesses: specific skills the person lacks or can only support thinly
- Opportunities: specific network-only or network-led skills the person could learn from, collaborate on, or test next
- Threats: specific ways the person's work could stall because they or their network are too thin, too tentative, or missing a needed complement

Decision rules:
- Use skill descriptions as the primary grounding signal; names and tags are secondary clues
- Read the owner skill evidence cards first; candidateMatches are plausible evidence, not guaranteed same-skill matches
- Prefer claims supported by the cited evidence cards, especially shared descriptions and shared tags, not just matching labels
- Treat tentative network skill as lower-confidence evidence, but do not let approval/tentative status dominate the analysis
- Never describe tentative network skill as fully dependable
- Strengths should usually stay anchored to a real owner skill, not an external-only network capability
- External network skills are especially good sources for weaknesses, opportunities, and threats when they reveal a missing complement, adjacent move, or tentative risk
- Prefer capability-area language over naming specific agents
- Do not mention capabilities outside the supplied context
- Avoid generic business phrases like "strong market position", "competitive advantage", or "growth opportunity"
- Avoid system jargon such as "route", "routing", "coverage", "source count", "tag overlap", "brain skill", or "approved coverage"
- Avoid repeating the same capability pattern across quadrants unless the contrast is genuinely useful
- Do not restate the same capability as both a weakness and a threat unless the threat is a distinct systemic risk, not the same thin-backup observation repeated
- Do not restate the same capability as both a strength and an opportunity unless the opportunity is a clearly different adjacent move
- If two candidate items say nearly the same thing, keep the sharper one and replace the other with a different capability pattern
- Prefer distinct coverage across the four quadrants over filling every slot
- Before writing, choose up to four DISTINCT themes first, then map them to quadrants. Reuse a theme only if the contrast is truly different and necessary.
- Use this priority order when distinct themes exist:
  1. one real owner-skill strength
  2. one real owner-skill gap or one missing complement revealed by the evidence cards
  3. one external network skill worth testing or learning from
  4. one concrete tentative network skill that matters in practice, or if none exists, one broader stall risk
- If the context supports them, prefer covering distinct themes like research, writing, analysis, facilitation/workshops, workflow/process, video, or visualization rather than collapsing everything into generic labels like "support" or "backup"
- If a tentative adjacent skill exists, prefer mentioning it once rather than adding another item about an already-covered strength
- Opportunity themes should usually come from external network skills or adjacent capabilities visible in the evidence cards
- Weakness and opportunity themes must name a concrete skill or capability visible in the context, not an abstract diagnosis like judgment, support, or communication
- If the owner already has a named skill like Analysis or Writing, refer to that capability directly instead of inventing a broader label
- When an external skill is the point, prefer the concrete skill name from the evidence card, such as Facilitation, Research Systems, or Video Production, over abstract labels like repeatable process or unproven gap
- Threat themes should usually come from tentative skills, missing complements, or broader stall risk — not just a second restatement of a weakness item
- If a concrete tentative skill like video or visualization exists, prefer that as the threat theme over generic process advice
- Do not use an opportunity slot for a skill the owner already clearly has unless the move is genuinely different from the existing strength
- Avoid generic themes like "support", "backup", "capacity", or "help" when a more specific skill theme is available from the context
- Verify each capability claim against the supplied context before writing: do not call a dependable network skill tentative, and do not call a tentative network skill dependable

Output style:
- Return 0-3 items per quadrant
- For this first pass, do NOT write final polished prose
- Instead, choose strong, specific draft items with:
  - theme: usually the actual capability name or a very close capability phrase from the evidence cards
  - evidence: one short factual statement grounded in the context, ideally naming the owner skill or matching network skill involved
  - action: one short recommendation or implication for the owner that says what the network does or does not add
- The action should be concrete, like strengthen it, use it confidently, test it, learn from it, review it, or do not rely on it yet
- If you can only say something useful by repeating an earlier theme, leave the extra slot empty instead
- Do not use generic threat themes like review quality, decision quality, or process discipline when a more concrete missing or tentative skill is available in the context
