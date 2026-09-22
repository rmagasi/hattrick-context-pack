# Match tactics and orders

Core section of the hattrick skill, loaded on demand. Deeper tables live in the other `references/` files it points to.

## How Ratings Work
- **Midfield** = ball possession → drives chance distribution
- **Attack** (left/central/right) = chance quality in that sector
- **Defence** (left/central/right) = ability to stop attacks in that sector
- Possession formula: `BP% = Midfield_A / (Midfield_A + Midfield_B)`
- Real probability of getting an open chance: `a³ / (a³ + b³)` where a, b are the two midfield ratings (verified vs Live data; the older a²/2b² devblog formula is less accurate at scale).
- Real attack-vs-defence conversion (per nickarana's Live data): `P = 0.92 × a^3.5 / (a^3.5 + d^3.5)`, where ratings should be reduced by **−0.75** vs the displayed match-report values (so a displayed 12 vs 13.5 → use 11.25 vs 12.75).
- Midfield is the most important sector — but possession above ~65–70% gives **diminishing returns** (per HT-Tasos devblog).

## Chance Distribution
- **15 ordinary chances per match**: 5 exclusive to team A, 5 exclusive to team B, 5 open (allocated by midfield ratio).
- Plus extraordinary chances from **Special Events** (and corners count as SEs).
- Free kicks (direct + indirect) and penalties are counted as **ordinary** chances, not SEs.
- Live data distribution (nickarana, ~900k matches):

| Chance type | % regular time |
|-------------|---------------:|
| Central | 35.96% |
| Right | 25.49% |
| Left | 25.47% |
| Direct FK | 5.96% |
| Indirect FK | 4.12% |
| Penalty | 2.41% |
| Long Shot (non-tactic) | 0.59% |

- In **extra time** the ME generates ~1/2/1 chance distribution (1 exclusive A, 2 open, 1 exclusive B).
- Each cycle has 6 phases in order: Special Event → Chance → Counter Attack (if missed) → Yellow/Red Card → Injury → Team Confusion.

## Formations Overview

**Critical convention to internalize**: the "defense" number in a Hattrick formation name is the total of CDs + WBs combined, NOT a CD count. Wing backs are defenders. A "5-3-2" is 3 CDs + 2 WBs, a "3-5-2" is 1 CD + 2 WBs (the 3 = 1 + 2). Setting "3 CDs and zero WBs" in a 3-5-2 leaves both flanks defensively naked and is essentially never correct.

| Formation | Defender split (CD + WB) | Mid split (W + IM) | FW | Strengths | Weaknesses | Best Counter |
|---|---|---|---|---|---|---|
| 4-4-2 | 2 CD + 2 WB | 2 W + 2 IM | 2 FW | Balanced, versatile | Nothing dominant | Exploit weak spots |
| 3-5-2 | 1 CD + 2 WB | 2 W + 3 IM | 2 FW | Strong midfield | Weaker central defence | Pack midfield, attack centre |
| 4-5-1 | 2 CD + 2 WB | 2 W + 3 IM | 1 FW | Strong midfield + defence | Weak attack | Dominate & wait |
| 5-3-2 | 3 CD + 2 WB | 0 W + 3 IM | 2 FW | Rock solid defence | Weak attack, abandoned wing | Attack wings, use OCD |
| 4-3-3 | 2 CD + 2 WB | 0 W + 3 IM | 2 W-FW + 1 FW | Very strong attack | Weak midfield | Win possession |
| 3-4-3 | 1 CD + 2 WB | 2 W + 2 IM | 2 W-FW + 1 FW | Very strong attack | Weak midfield, weak defence | Win possession or lose |
| 5-5-0 | 3 CD + 2 WB | 2 W + 3 IM | 0 FW | LS-tactic specialist, control | No forwards = LS-only attack | Pressing teams nullify LS |

**Formation experience**: Teams build XP in formations they use repeatedly — using an unfamiliar formation carries a penalty. Stick to 1-2 formations long-term.

**Formation XP accumulation** (per Dutch HT thread, validated):
- 1 game (90 min) of a fresh formation: Poor → Passable
- 2 games: Passable → Excellent
- 3 games: Excellent → Formidable
- 4 games: Formidable → Outstanding
- Each 10 minutes of play = 1 block of XP. Each game, all formations lose 1 block (1/3 of low levels: Poor→Solid; 1/6 of high levels: Excellent/Formidable/Outstanding which are "double levels").
- The starting formation also loses 1 block at game start before it gains its 9 blocks.
- **No XP gains in extra time.**

## Tactics (6 available)
- **Normal**: No tactic, default. 99% of games. No skill requirement.
- **Pressing (PR)**: Reduces total attacks for both teams. Powered by all players' defending. Use vs strong attack opponents. Causes accelerated stamina drop on your team.
- **Counter Attack (CA)**: Gives up midfield in exchange for bonus counter-attack chances on opponent missed chances. CA level powered by `0.017272 × Σ[Form × (2×Passing + Defending)] + 1.042313` for the defenders. **Passing counts double** vs Defending. Strong defence required. **Note**: the old `10.8 × ca/ra` conversion formula is wrong — actual conversion barely varies with ratings (per nickarana's Live data, see `references/tactics-detail.md`).
- **Attack in Middle (AiM)** & **Attack on Wings (AoW)**: Powered by passing — `Tactic Level = (Σ Passing of outfield players) / 5 − 2`. Redirects attacks; opponent sector defence weakened. Since Oct 2021, both have a guaranteed minimum of attacks dedicated to the chosen tactic, addressing earlier complaints that they were too random.
- **Long Shots (LS)**: Extra scoring chances via long-range attempts. `LS Tactic Level = 1.66 × avg(Scoring) + 0.55 × avg(Set Pieces) − 7.6`. Penalties: −5% midfield, −2.7% attack. Since Oct 2021, Pressing teams have a guaranteed minimum chance of pressing away an LS attempt.
- **Play Creatively (PC)**: Unpredictable players get boosted specials. Niche use.

## Individual Player Orders & Positions
Each pitch position has 3–5 order variants — these are **codes you'll see in HO/Foxtrick**:
- GK
- WB / WBN, WBO, WBD, WBTM (towards middle)
- CD / RCD, LCD, CDO, CDTW (towards wing)
- IM / IMN, IMO, IMD, IMTW
- W / WN, WO, WD, WTM (towards middle)
- FW / DF (defensive forward), FTW (forward towards wing), TDF (technical DF)

Tactical Assistant unlocks extra order slots (1 per TA level, max +5).

→ See `references/position-contributions.md` for full skill-contribution percentages of every position/order combination.

## Team Spirit & Confidence
- **Team Spirit (TS)**: Directly affects midfield rating.
- **Confidence**: Affects goals scored per chance.
- PIC (Play It Cool) = maintains TS, use when result doesn't matter.
- MOTS (Match of the Season) = boosts TS significantly, but disables pullback/match dynamics — use for a must-win.
- Changing formation lowers TS slightly.

**TS × Attitude × Midfield matrix:**
| TS Level | PIC | Normal | MOTS |
|----------|----:|-------:|-----:|
| Paradise on Earth | 122% | 142% | 162% |
| Walking on clouds | 116% | 135% | 154% |
| Delirious | 110% | 128% | 146% |
| Satisfied | 104% | 121% | 138% |
| Content | 98% | 114% | 130% |
| Calm | 92% | 107% | 122% |
| Composed | 87% | 100% | 113% |
| Irritated | 81% | 93% | 105% |
| Furious | 75% | 86% | 97% |
| Murderous | 63% | 72% | 81% |

**Home/away/derby/tactic midfield coefficients:**
| Situation | Coef |
|-----------|-----:|
| Playing Normal & Away | 100% |
| Playing CA | 93% |
| Playing at Home | 119.892% |
| Derby (away team only) | 111.493% |
| Playing PIC | 83.945% |
| Playing MOTS | 111.49% |

Coefficients multiply. Example: Home + MOTS = 1.19892 × 1.1149 = 133.67%. Home + PIC + CA = 1.19892 × 0.83945 × 0.93 = 93.6%.

**Derby = same region** (Rules 04). The "Derby" coefficient above is NOT NT-only - it applies to ANY club match where both teams are from the same Hattrick region (e.g., two Pest-region teams in Hungary). The home team still gets the full 119.892% home advantage, the away team additionally gets the 111.493% derby boost (roughly half of the home advantage). Games played on neutral ground do NOT trigger the derby bonus even if the stadium is in the region of one of the teams.

**New Confidence system (May 2024):**
- Effects are slower and depend on more factors.
- Goals matter, but **fan expectations**, **coach leadership**, and **staff psychologist** also factor in.
- Confidence updates daily (background → visible drift), not directly after match.
- Sept 2024 tweak: Starting TC raised from 4.5 to 5.0; can no longer lose TC after a win even if opponent scored multiple goals.

**Underestimation / overconfidence** (May 2025 update):
- Risk depends on points/position gap, confidence level, attitude.
- **PIC triples the underestimation risk.**
- Only MOTS fully prevents underestimation.
- Triggered above ~Decent/Strong confidence; can drop midfield up to 70%.
- Risk and impact were both slightly reduced in May 2025 to compensate for new confidence system letting teams stay high-confidence longer.
- **First-3-rounds exception (Rules 11):** underestimation can ONLY occur in league/series matches, and NEVER in the first three rounds of a season. So no risk to plan around in S77 weeks 1-3 (or equivalent), the standings have not stabilised enough for the engine to flag a "weaker opponent".
- **Half-time recovery (Rules 11):** if you ARE being underestimated, the team partially recovers at half-time depending on the score:
  - Trailing at HT → **full** recovery (100% of the underestimation penalty removed)
  - Tied at HT → **2/3** recovery
  - Leading by exactly 1 goal → **1/3** recovery
  - Leading by 2+ goals → no recovery (you stay underestimating, because the lead "confirms" the bias)
- **Half-time pep-talk (Rules 11):** the coach can additionally pull a team out of a bad first half via a half-time "tongue lashing", reduces confusion / disorganisation events that appeared in H1. This is a separate mechanic from underestimation recovery, but the two can stack in the same half-time window. Magnitude scales with coach Leadership.

## Match Dynamics
- Team 2 goals ahead: **−9% attack, +7.5% defence per goal of lead** (latest official numbers; older "−6.25/+5%" values were superseded).
- Cap: lead difference of 8 goals; effects don't increase further.
- Each goal pulled back reverses one increment.
- **Disabled** during MOTS, National Cup final, World Cup final, HT Masters final, last league round of the season.

## Specialties in Matches
- **Technical**: Extra scoring chance in normal weather; can beat Head defenders in SE.
- **Quick**: Extra scoring on counter-attacks; extra defending vs counter-attacks. Stops Quick SEs if positioned opposite the attacker.
- **Head**: Extra scoring in rain; countered by Technical.
- **Powerful**: Extra scoring in sunny weather; +10% Defending in man marking calc.
- **Unpredictable**: Random positive or negative special events; +8% on highest skill in MM calc.
- **Support**: Boosts nearby teammates' contributions (also has a flop / disorganization risk).
- **Resilient** (formerly Regainer): Heals faster, less severe injuries, skill drops kick in slightly later.

## Disorganization & Negative Experience
**Performance vs disorganization level:**
| Level | Performance |
|-------|------------:|
| Solid | 95–98% |
| Passable | 89–94% |
| Inadequate | 83–88% |
| Weak | 76–82% |
| Poor | 66–75% |
| Wretched | ≤65% |

- Disorganization can occur at **any minute** during the match.
- Negative experience event: ratings drop as in disorganization. Captain's contribution: leadership ×3, experience ×2 (vs ×1 for other players). The default-chosen captain is not always optimal.
- **No** negative experience message in League/Friendly matches — only Cup, ladder, tournament, play-off, and NT matches.

## Substitutions (sub priority by position)
| Position | Sub 1 | Sub 2 | Sub 3 | Sub 4 | Sub 5 |
|----------|-------|-------|-------|-------|-------|
| GK | GK | DEF | IM | W | FW |
| DEF | DEF | IM | W | FW | GK |
| IM | IM | DEF | W | FW | GK |
| W | W | FW | IM | DEF | GK |
| FW | FW | W | IM | DEF | GK |

- Designated primary backup goes in first; if gone, designated backup; if gone, the auto-fallback above.
- The "extra dude" (5th bench expansion) is used last automatically — keep him for tactical flexibility.
- Since Feb 2025: substitutes can be assigned **individual orders for entry** (offensive/defensive/normal/towards-wing/towards-middle for that position). New "Advanced Conditions" allow conditional subs based on which on-field player gets injured.

## Weather (May 2024 onward)
The forecast for tomorrow is **deterministic** — what you see is what you get. Set lineup confidently the day before.

| Weather | Frequency |
|---------|----------:|
| Rain | 15.92% |
| Overcast | 34.44% |
| Partially cloudy | 34.30% |
| Sunny | 15.35% |

Extreme weather (Rain/Sunny) is roughly half as common as the middle two states (~1/6 each).

→ See `references/tactics-detail.md` for ratings formulas, CA Live-data tables, LS conversion table, and AOW/AIM mechanics
→ See `references/match-engine-deep.md` for chance-distribution stats, SE frequencies, PNF/PDIM/TDF formulas, man marking logistic formula, corner scoring probabilities, important-skills-per-SE table

---

## Key Insights from the Hattrick Developer Blog

These are confirmed, official mechanics published by the HT dev team:

**Chance Distribution:**
- Max 10 normal chances per team per match (5 exclusive + 5 shared).
- Ball possession above ~65–70% gives **diminishing returns** — investing in attack/defence may be better than chasing more midfield above this threshold.
- Open chance formula: `P(A wins) = Midfield_A³ / (Midfield_A³ + Midfield_B³)`

**Special Events:**
- SE frequency scales with number of specialty players — mixing specialty types (e.g., 3 Quick + 3 Unpredictable) generates more SEs than 6 of one type.
- The 2017 SE framework introduced 3 unique combos: PNF, PDIM (Sitting Midfielder), TDF (Trequartista).
- Stacking 2 of same combo type: −4% each, 3 of same: −7.5% each.

**PNF (Powerful Normal Forward):**
- Triggers after a **missed** normal chance: 10% (1 PNF) / 16% (2) / 20% (3).
- Playmaking vs central defenders' Defending, then Scoring vs GK.
- Trade-off: loses Defensive Forward's midfield contribution bonus.

**Man Marking:**
- Logistic formula: `penalty = defending^3.5 / (defending^3.5 + highest_skill^3.5)`
- At equal skills → 50% penalty to target, well-played MM = +1.5–2pp win probability.
- Marker loses 50% contribution (opposite sector) or 65% (all other cases). 10% if target doesn't appear at all.

**Corners:**
- Head specialty players massively improve corner conversion: 1 Header vs 4 = 4% score, 6 vs 4 = 61%.
- Corner to Anyone also uses receiver's Scoring vs keeper's GK.

**Resilient (ex-Regainer):**
- Skill drop kicks in at slightly higher age — underrated specialty for long-term value.
