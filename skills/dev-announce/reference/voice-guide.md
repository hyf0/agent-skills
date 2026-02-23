# Voice Guide

## Core Principles

- **Never oversell.** Understated confidence throughout. "very slightly faster", "improves memory usage a little" -- let the numbers do the bragging.
- **Self-critique is a superpower.** "I still think 5% is way too high" -- publicly admitting something isn't good enough yet builds massive credibility.
- **Honest about limitations.** "Unfortunately, there doesn't seem to be an OS-level API..." -- no excuses, just facts.
- **Credit others.** @mention contributors, credit upstream projects ("a Zig port of the popular `md4c` library").
- **Define jargon inline.** "'blurred' here means did it send the terminal escape sequence for unfocus" -- respects the reader without being condescending.
- **Mix serious and playful.** Technical use cases alongside "when you want to iMessage a .html file".
- **Be genuine.** If it reads like an ad or a press release, rewrite it. The tweet should sound like a real person talking to other developers.

## Tone Calibration

| Situation | Tone | Example |
|---|---|---|
| Big improvement (5x+) | Let the number speak, no exclamation marks | "Before: 115s / After: 15s (7x faster)" |
| Small improvement | Explicitly hedge | "improves memory usage a little" |
| Incomplete work | Honest self-critique | "I still think 5% is way too high" |
| Team contribution | Generous credit | "thanks to @contributor" |
| Upstream dependency | Respectful attribution | "a Zig port of the popular `md4c` library" |
| Platform limitation | Matter-of-fact | "Unfortunately, there doesn't seem to be an OS-level API for this" |
| Future plans | Casual tease | "We'll likely add X later" |

## Words to Avoid

- "Excited", "thrilled", "proud" -- corporate voice
- "Blazingly fast", "revolutionary", "game-changing" -- hype words
- "Check out our blog" -- the tweet is the content
- "What do you think?", "RT if" -- engagement bait
- "Just shipped" -- too casual/startup-bro
- Em dashes -- use commas, periods, or conjunctions instead
- "No X, no Y, just Z" constructions (e.g., "No config changes. Just faster.")
- Starting sentences with bare past participles ("Optimized...", "Reduced...", "Improved...")
- Dependency version references ("Bumped X to v2", "Upgraded Y")
- Awkward specificity ("all 8 benchmarks", "across 16 files")

## Words That Work

- "In the next version of" -- reliable opener
- "You can:" -- direct, empowering
- "This is useful when" -- practical framing
- "Previously X. Now Y." -- progress framing
- "X faster", "reduces Y by Z%" -- numbers as the argument
- "thanks to @name" -- crediting

## AI Tells to Avoid

These patterns are easy tells that an AI wrote the tweet. Avoid all of them:

- Em dashes everywhere
- "No X, no Y, just Z" or "No X. No Y. Just Z."
- Bare past participle openers ("Optimized...", "Reduced...", "Improved...")
- Overly precise counts that don't add meaning ("all 8 benchmarks" vs "across our benchmarks")
- Ranges when a peak number is clearer ("3-9%" vs "up to 9%")
- Dense paragraphs without line breaks (unreadable in tweet form)
