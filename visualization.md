
```yml
journey_map:
  title: "Customer Journey Map — Evaluating Whether OAC Is 'Worth It'"
  persona_name: "CJM — Design-conscious Brand Evaluator"
  brand: ""
  journey_type: "AS-IS"
  start_criteria: "User lands on OAC site for the first time from a social ad or referral."
  stop_criteria:
    - "User feels confident in brand + product value (low-regret decision)."
    - "User leaves due to uncertainty, lack of trust, or low visual/brand fit."

  phases_left_to_right:
    - phase: "BEFORE"
      context:
        - "Often mobile"
        - "Between tasks"
        - "Low patience; multitasking"
        - "May be comparing multiple brands/tabs"
        - "Mild skepticism (ad-driven traffic)"
      steps:
        - step: "Arrives via social media ad or referral"
          thoughts:
            - "What is this and why is it special?"
          actions:
            - "Opens site (often quickly, on mobile)"
          pain_points:
            - "Low initial trust from ad-driven entry"
          emotions:
            - "Skeptical"
            - "Rushed"
        - step: "Rapidly decides whether to stay or leave"
          thoughts:
            - "Does this feel legit and aligned with my taste?"
          actions:
            - "Skims for immediate vibe/aesthetic signals"
          pain_points:
            - "Visual mismatch leads to bounce"
            - "Brand ambiguity makes it hard to assess quickly"
          emotions:
            - "Impatient"
            - "Uncertain"

    - phase: "DURING"
      context:
        - "Short session ('two-minute browse')"
        - "Cognitive load is limited; won’t read dense text unless earned"
        - "Cannot touch/feel product; relies on photos + narrative"
      steps:
        - step: "Forms a first impression of brand identity"
          thoughts:
            - "Do I understand what this brand is?"
          actions:
            - "Scans for brand cues: story, identity, credibility signals"
          pain_points:
            - "Brand ambiguity: doesn’t quickly answer what’s different"
          emotions:
            - "Curious"
            - "Uncertain"
        - step: "Evaluates credibility needed to justify premium price"
          thoughts:
            - "Is the price justified? Is the quality real?"
          actions:
            - "Looks for proof of quality (materials/craft/process/social proof)"
          pain_points:
            - "Credibility gap: premium price requires proof without feeling salesy"
          emotions:
            - "Skeptical"
            - "Cautiously interested"
        - step: "Explores products/collections to validate taste fit"
          thoughts:
            - "Is there a coherent aesthetic and meaning across the collection?"
          actions:
            - "Browses multiple items; compares within a collection/theme"
          pain_points:
            - "Overchoice without guidance: unclear collections/themes make exploration feel like work"
          emotions:
            - "Engaged (if coherent)"
            - "Overwhelmed (if not)"
        - step: "Checks for regret risk before committing"
          thoughts:
            - "Will I regret this? Will it meet expectations (or be a bad gift)?"
          actions:
            - "Compares options; may switch tabs or reconsider"
          pain_points:
            - "Fear of regret: wrong decision feels costly"
          emotions:
            - "Anxious"
            - "Hesitant"

    - phase: "AFTER"
      context:
        - "Competing priorities: price sensitivity, gift deadlines, other options"
      steps:
        - step: "Outcome — confident decision or exit"
          thoughts:
            - "I get it, I trust it, and I feel good about the price"  # confident path
            - "I still don’t understand what’s special / don’t trust it" # exit path
          actions:
            - "Leaves feeling confident (low-regret decision)"
            - "Leaves (bounce/back to search/other brands)"
            - "May return later to the same product"
            - "May share a link"
          pain_points:
            - "If uncertainty remains, decision is delayed or abandoned"
          emotions:
            - "Relieved/confident (if resolved)"
            - "Frustrated/uncertain (if not)"

  cross_cutting_constraints:
    - "Time: short sessions; decide fast or leave"
    - "Cognitive load: won’t read walls of text unless earned"
    - "Access limits: cannot touch/feel product; photos + narrative must carry weight"
    - "Competing priorities: comparing alternatives, price sensitivity, gift deadlines"

  recurring_pattern_note:
    - "Recurring for self-buyers (collectors/repeat shoppers); occasional for gift buyers"

```