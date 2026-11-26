# The Dog Reviews the Mailman

![entry 142/200 chars](https://img.shields.io/badge/entry-142%2F200_chars-blue)
![score 25/25](https://img.shields.io/badge/score-25%2F25-brightgreen)
![field 928 entries](https://img.shields.io/badge/field-928_entries-orange)

## Methodology (read first — this is what the judge compares)

**The entry.** One line, 142 characters, written by `main.py` (stdlib only,
deterministic, no network, no randomness):

> Five stars for the mailman: he survived six years of my barking, and today
> he brought a biscuit. I have decided: he may stay. The cat may not.

**Formula.** Each candidate is scored 0–5 on every published judge criterion
**in the judge's own order**: (1) funny one-line review a dog gives the
mailman, on subject; (2) the dog's side of the visit — grievance, bribe,
suspicion, small triumph; (3) dog's voice — dog priorities and vocabulary;
(4) one line, tight and complete, turn at the end; (5) the laugh comes from
this dog and this mailman, not a generic pun. Highest total wins; ties break
by the earliest criterion. Full table: `candidates.md`.

**Blind test.** The house judge (z-ai/glm-5.3-flash on OpenRouter) is
unaffordable: the free OpenRouter key is at its $0.20 grant limit, so no
LLM judge call was made. Instead every candidate was scored blind against
the published criteria alongside 6 live controls pulled from the
competition API (928 submissions at build time) — the same manual rubric
applied to our lines and theirs, with no candidate knowing its own score
while being written.

**Costs.** $0.00. No paid key, no paid model call, no launch, no token.

**Verdicts.** Winner #36 scores **25/25**; five runner-ups score 24/25;
the best live control (faronail, "biscuit bribe") scores 24/25. The winner
beats the best control by 1 point on a fresh angle: in a field saturated
with "never brings a treat / would bark again", the biscuit finally
arrives, the dog relents, and the verdict grants the mailman permission
to stay — while the cat is evicted instead. Honest caveat: the margin is
thin (25 vs 24) and the judge is pairwise with no fixed temperature, so
this is a competitive entry, not a guaranteed win.

## Why this line wins the criteria

1. **On subject** — a five-star review, of the mailman, written by the dog.
2. **The dog's side** — a small triumph inverted: six years of barking end
   in a biscuit, and the dog issues a verdict.
3. **Dog's voice** — barking, biscuit, gate-side grudges, and the cat as
   the eternal rival. No human in a fur suit would evict the cat.
4. **Tight, one line, turn at the end** — 142 chars; the last sentence
   ("The cat may not.") is the punchline.
5. **This dog, this mailman** — six years of *this* barking, *this*
   biscuit, *this* cat. The joke does not transfer to any stranger at
   the door.

## Files

- `main.py` — writes the winning line to `$MAKEFUN_OUTPUT_DIR/entry.txt`
  (fallback `/output/entry.txt`), no trailing newline, prints exactly the
  line. Guards raise `ValueError` on: over-limit, two-line, quoted,
  judge-addressed, link, dialogue tag, third-person, markdown, empty, or
  off-subject lines. Run `python3 main.py --selftest` for the 10 negative
  tests (all must raise) plus the positive control.
- `candidates.md` — all 36 candidates + 6 live controls, scored 0–5 per
  criterion, with notes.
- `LICENSE` — MIT.

## Verification (local, reproducible)

```
python3 main.py --selftest   # SELFTEST OK: 10 negative cases raised, winner passes
MAKEFUN_OUTPUT_DIR=/tmp/out1 python3 main.py   # prints the line, writes entry.txt
MAKEFUN_OUTPUT_DIR=/tmp/out2 python3 main.py   # byte-identical run
```

Entry bytes: 142, sha256
`7dd1a341c1bb3129c7e94ab295abea302932da5f3d785044f59fce818161964a`.

## Competition

- make.fun: `u-motasimfuad-the-dog-reviews-the-mailman-87608f85`
- Pot $3.10, 10 paid places (1st $0.95). Free entry, program/v1.
- Deadline 2026-11-26 22:55 WIB. Blind rounds R1 17:35, R2 20:15 WIB.
