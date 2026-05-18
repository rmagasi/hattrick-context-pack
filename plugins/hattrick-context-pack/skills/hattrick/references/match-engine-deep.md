# Match Engine Deep Reference
## Source: Hattrick Developer Blog (devblog.hattrick.org) + Official Wiki

---

## CHANCE DISTRIBUTION (devblog 2016, HT-Tasos)

### How Normal Chances Work
A match contains **15 normal chance slots** distributed as follows:
- 5 chances exclusive to your team (awarded if you win the midfield battle)
- 5 chances exclusive to your opponent (awarded if they win the midfield battle)
- 5 open/mutual chances — midfield battle decides who wins each one

**Maximum 10 normal chances per team per match.**

Ball possession formula:
`BP% = Midfield_A / (Midfield_A + Midfield_B)`

Open chance formula (probability Team A wins an open chance):
`P = Midfield_A^3 / (Midfield_A^3 + Midfield_B^3)`

### Ball Possession vs Normal Chances (from 1M match simulation, HT-Tasos)
| BP% | Avg Normal Chances | Notes |
|-----|-------------------|-------|
| 50% | ~5 | Equal share |
| 55% | ~6-8 (median) | Half of matches: 6-8 chances |
| 60% | ~7-9 | Increasing range |
| 65% | ~9-10 | Near max; strong advantage |
| 70%+ | Diminishing returns | ~9-10; possession above 65-70% gives very little extra |

**Key insight (official)**: Up to ~65% possession, each extra % is worth pursuing. Above 65-70%, returns diminish significantly — investing in attack/defence sectors may be better than chasing more midfield.

### How a Chance Plays Out
Once a team is awarded a chance, the engine determines:
1. **Where the chance occurs**: Flank (50%: 25% right, 25% left), Middle (35%), Free kick/penalty (15%)
   - ~10% of all chances are direct set pieces, ~5% indirect
2. **Chance conversion**: Attack rating vs Defence rating in the relevant sector (in Hatstats)
   - If your right attack >> opponent's right defence → high conversion probability

### Live data — actual chance type distribution (nickarana, ~900k matches, regular time)

| Chance type | Frequency |
|-------------|----------:|
| Central | 35.96% |
| Right | 25.49% |
| Left | 25.47% |
| Direct FK | 5.96% |
| Indirect FK | 4.12% |
| Penalty | 2.41% |
| Long Shot (non-tactic) | 0.59% |

In **extra time** the distribution shifts: ~1 exclusive chance for team A, ~2 open, ~1 exclusive for team B per the cycle, with central+side chances roughly retaining the same relative proportions.

### Real attack-vs-defence conversion (per nickarana Live data)

```
P(score | chance, ratings a vs d) = 0.92 × a^3.5 / (a^3.5 + d^3.5)
```

Where ratings should be reduced by **−0.75** vs displayed match-report values (so a displayed 12 vs 13.5 → use 11.25 vs 12.75).

This formula matches the observed Live-data distribution far better than the older `0.92 × a^4 / (a^4 + d^4)` from the devblog.

### Real open-chance probability (per nickarana Live data)

```
P(team A wins open chance) = a³ / (a³ + b³)
```

Where a, b are the two midfield ratings. The older `a²/(2b²)` formula from Tasos's 2016 devblog turns out to be inaccurate at scale — the cubic version above matches Live data.

---

## SPECIAL EVENTS FRAMEWORK (devblog 2017/2018, HT-Tasos)

### SE Generation Process (new system from 2017)
1. At match start: Decide if weather SE occurs → select affected player(s)
2. Each SE has initial probabilities, dynamically adjusted based on both teams' lineups
3. If no player has Quick specialty → Quick event probability = 0%, redistributed to others
4. For **Team Goal SEs** (Corner, Experienced Forward, Inexperienced Defender): team with higher midfield has better chance of getting it
5. For **Individual Goal SEs**: midfield doesn't matter — number of specialty players determines probability
6. Same SE can happen more than once, but each repetition is harder to trigger; negative events decrease faster than positive ones

### Special Event Frequency (official HT data, 1M+ matches)
- Unpredictable and Quick events trigger at nearly the same rate
- 2 specialists in both teams: ~0.10 events/match
- 4 specialists in both teams: ~0.29 events/match
- 5 specialists in both teams: ~0.35 events/match
- **Mixing specialties increases frequency**: 3 Quick + 3 Unpredictable players = ~0.47 SE/match (vs 0.42 with 6 of one type)

### Unique Position-Specialty Combos (2017 framework)
Three special combos that have unique effects:

| Combo | Abbrev | Requirements | Effect |
|-------|--------|-------------|--------|
| Technical Defensive Forward | TDF ("Trequartista") | Technical + FW Defensive order | 33% Passing boost on wing attacks; can score vs Head defenders; counter-attack bonus |
| Powerful Normal Forward | PNF | Powerful + FW Normal order | Second chance to score after a missed normal chance |
| Powerful Defensive Inner Midfielder | PDIM ("Sitting Midfielder") | Powerful + IM Defensive order | Can break up opponent attacks using Defending + Stamina |

**Stacking penalty**: Fielding 2 of same type → -4% each; 3 of same type → -7.5% each.

### PNF Mechanics (devblog 2018, HT-Tasos)
- Triggers **right after a missed normal chance** for your team
- Probability: 1 PNF = 10%, 2 PNFs = 16%, 3 PNFs = 20%
- Fight: PNF's **Playmaking** vs sum of opponent **central defenders' Defending**
- If passes defenders → PNF's **Scoring** vs keeper's **Goalkeeping**
- Warning: PNF play is physical → yellow card risk; already-carded PNF plays more carefully
- PNF gives up the extra midfield contribution of a Defensive Forward (trade-off)

### PDIM Mechanics
- Triggers at same probability as PNF (10/16/20% for 1/2/3)
- Uses **Defending** + **Stamina** to press and break up attacks
- Example: Defending 13 vs opponent Scoring 17 → 41% chance to press successfully

### Important Skills per Special Event

A complete reference for which skills matter on each side of every common SE (sourced from the Unwritten Manual #15, post #31 — based on the Dec 2017 ME framework and post-2018 corrections):

| SE | Attacker side | Opposite player side | Receiver | Goalkeeper | Notes |
|----|---------------|----------------------|----------|------------|-------|
| Quick score | Sc | Def | Sc | GK | SE always stopped if opposite player is also Quick |
| Quick pass | Passing | Def* | Sc** | GK | *Avg def rating same side; **Sc of receiver |
| Technical goes around Head | Sc, XP | Def, XP | Sc | GK | |
| Technical CD/WB creates non-tactical CA | Passing | Def* | — | — | *Sum of opp IMs' Defending / 3 |
| Goal Unpredictable long pass | Passing | Def* | Sc** | GK | *Sum of opp IMs' Def/3; **Sc of receiver |
| Goal Unpredictable scores on his own | — | — | Sc | GK | |
| Goal Unpredictable special action | Passing, XP | Def*, XP* | Sc** | GK | *Avg def rating + XP of defenders same side; **Sc of receiver |
| Goal Unpredictable mistake (negative) | Def, XP, GK* | Sc, XP | — | — | *Your GK vs opp Sc |
| Unpredictable own goal | Passing, GK* | — | — | — | *Your GK vs Passing of your FW or W |
| Power Forward (PNF goal) | PM | Def* | Sc | GK | *Def of central defenders |
| Sitting Midfielder (PDIM stop) | Def, Stamina | Sc, Stamina | — | — | |
| Winger to Anyone | W | Def* | Sc** | GK | *Avg def same side; **Sc of receiver |
| Winger to Head | W | Def* | Sc** | GK | *Avg def same side; **Sc of receiver |
| Corner to Anyone | IndSpAtt, SP* | IndSpDef* | Sc** | GK | *Indirect SP attack + bonus/malus of corner taker vs opp Indirect SP defence; **Sc of receiver |
| Corner to Head specialist | IndSpAtt, SP*, Headers** | IndSpDef*, Headers** | — | — | *as above; **your Headers vs opp Headers |
| Experienced Forward scores | XP | Avg XP* | Sc | GK | *Avg XP of opponent team |
| Inexp. Defender causes goal | XP, Def, GK** | Avg XP*, Sc | — | — | *Avg XP of opp team; **Your GK vs opp Sc |
| Tired Defender Mistake | Stamina, GK** | Stamina, Sc | — | — | **Your GK vs opp Sc |

**"Average defence rating of the same side" definitions:**
- FWR / WR / WBR vs WBL, CDL
- FWL / WL / WBL vs WBR, CDR
- All other (central) attackers vs CDL, CD, CDR

**Quick SE defender priority:**

| Attacker | Defender (100% to stop) | Defender (25% to stop) |
|----------|-------------------------|------------------------|
| WR, FW Right | WB Left | CD Left |
| WL, FW Left | WB Right | CD Right |
| IM Right | CD Left | CD Middle, WB Left |
| IM Left | CD Right | CD Middle, WB Right |
| FW Middle, IM Middle | CD Middle | CD Left, CD Right |

If no Quick player to stop the attacker, a random player from the defender line is picked. If no defenders, the queue continues to IMs and Wingers.

### Support Player (rare specialty, introduced 2017)
- When SE triggers for Support player: 20% total boost shared with **nearby players**
- Nearby player proximity map (10% unless noted):
  - Middle FW → Left FW (10%), Right FW (10%)
  - Right/Left FW → Middle FW (10%), Right/Left Winger (10%)
  - Middle IM → Middle CD (10%), Middle FW (10%)
  - Right/Left IM → Right/Left Winger (10%), Right/Left CD (5%), Right/Left FW (5%)
  - Winger → Left/Right FW (10%), Left/Right WB (10%)
  - Middle CD → Left CD (10%), Right CD (10%)
  - Right/Left CD → Middle CD (10%), Right/Left WB (10%)
  - WB → Left/Right CD (10%), Left/Right Winger (10%)
  - GK → Middle CD (10%), Left CD (5%), Right CD (5%)
- Risk: Can also drop team organization instead

### Weather Effects on Specialties
| Weather | Technical | Quick | Powerful | Head |
|---------|-----------|-------|---------|------|
| Sunny | +5% all skills | -5% all skills | +5% all skills | no effect |
| Rainy | -5% all skills | -5% all skills | +5% all skills | favoured (Header events) |
| Normal | favoured (vs Head) | no penalty | no bonus | no bonus |

Note: Quick players never suffer weather penalty in the **first half** in sunny conditions.

### Resilient (formerly Regainer) Specialty
- Injuries are less severe
- Heal faster than other players
- Skill drop kicks in at a **slightly higher age** than other players
- No special match events — purely a durability/longevity bonus

---

## MAN MARKING (devblog Dec 2017, HT-Tasos)

### Who Can Mark / Be Marked
- **Markers**: Defenders, Wingbacks, Inner Midfielders only
- **Targets**: Forwards, Wingers, Inner Midfielders only
- Only **1 man marking order** allowed per match
- Order becomes void if target doesn't play or plays in unmarable position (but can activate later via sub/position change)

### Cost to the Marker
- Marker loses **50% of his skill contribution** if in the "opposite sector" (Def vs FW, WB vs Winger, IM vs IM)
- Marker loses **65% of his skill contribution** in all other cases
- Marker loses **10%** if target doesn't appear
- Marker also loses contribution to tactical ratings (CA, Pressing, etc.) while marking

### Effect on the Target (logistic formula)
`penalty = defending^3.5 / (defending^3.5 + highest_skill^3.5)`

Where `defending` = marker's Defending skill, `highest_skill` = target's highest skill (excluding Set Pieces).

**What this means in practice:**
- Equal skills → 50% penalty to target
- Each skill level of difference → ~6% shift in the penalty
- Outstanding (10) marker vs Titanic (15) target → ~25% penalty to target
- Divine (20) marker vs Titanic (15) target → ~66% penalty to target

### Specialty Modifiers for Man Marking
| Situation | Effect |
|-----------|--------|
| Marker is Powerful | +10% to Defending in MM calculation |
| Marker has no specialty | +5% to Defending in MM calculation |
| Target is Technical | -8% to their highest skill in MM calculation |
| Target is Unpredictable | +8% to their highest skill in MM calculation (harder to mark) |

Note: These specialty bonuses/penalties only apply to the man marking calculation, not to overall match ratings.

### Strategic Value
- A well-played man marking can increase win chances by **1.5-2 percentage points**
- Best used: Strong defensive player marking opponent's key playmaker/scorer
- Risky: Your marker is effectively weakened for the whole match regardless of effect on target

---

## HATTRICK POWER RATING (devblog 2020, LA-Artod / Matteo Dimai)

### What It Is
- Official rating developed by HT team to summarize team strength
- Based on **"Base Power Rating"** = probability of winning + 0.5 × probability of drawing
- Calculated from lineup ratings, not individual player skills in isolation
- **Not transitive** (rock-paper-scissors element): C > B > A doesn't guarantee C beats A

### Tactical Asymmetry Insight
- Balanced teams score predictably in BPR
- Very **asymmetric teams** (e.g., all-attack no-defence) perform worse than BPR suggests vs opponents who target their weak spots
- This confirms: **tactical counter-play matters** in Hattrick — exploit opponent weaknesses

### Using Power Rating for Match Prep
- Compare Base Power Ratings: shows implied win probability with default lineups
- If you can craft a lineup with 70% actual win probability vs a 50% implied probability → good tactical play
- Use Super Replays to calculate specific success probabilities for a known opponent

---

## CORNERS & SET PIECES (devblog 2017/2018, HT-Tasos)

### Corner to Anyone (indirect set piece)
- Your set piecer's SP vs opponent's indirect defending SP
- Plus: Ball receiver's **Scoring** vs keeper's **Goalkeeping**
- Example: SP 12, indirect attacking SP 10 vs opponent's 11, receiver Scoring 13 vs GK 15 → **76% chance to score**
- Even with SP 6 (same other stats): drops to 69%

### Corner to Head
- Same kicker formula as Corner to Anyone
- Instead of Scoring vs GK: total **Headers in your team** vs **Headers in opponent's team**
- Example: SP 12, ind. attacking 10 vs 11, but 1 Header vs 4 opponents → **4%** chance
- With 6 Headers vs 4: rises to **61%**

**Key takeaway**: Head specialty players massively improve corner conversion. A team with 6 Head specialists vs 4 will score from corners far more often.

### Direct Free Kicks & Penalties
- Only shooter's **Set Pieces** + **Experience** matter for direct free kicks
- For penalties (regular and shootout):
  `Effectiveness = XP × 1.5 + CP (form) × 0.7 + Scoring × 0.3 + 10% if Technical`
- ~10% of all chances are direct set pieces; ~5% indirect

### Tired Defender Mistake (second half only)
- If one of your defenders has far lower stamina than an opponent player in the second half → defender can be bypassed for a 1v1 with GK
- Example: FW Scoring 13 vs GK 15 → 41% to score; Winger in same situation → 57% to score

---

## FORM, STAMINA, EXPERIENCE, LOYALTY, HOMEGROWN

All of these modifiers affect player skill calculations **in every match formula** (ratings, SE calculations, man marking, PNF, etc.):

- **Form**: Multiplies effective skill contribution. Poor form is severely punishing.
- **Stamina**: Reduces performance linearly from ~65 min onward if low. Also affects PDIM and tired defender events.
- **Experience**: Adds to player contribution regardless of skill; important for SE team events (Corner, Experienced Forward)
- **Loyalty**: Players who have been with your club longer contribute slightly more
- **Homegrown bonus**: Players who came through your youth academy get a small contribution boost
- **Health**: Injured players (carrying minor injuries) underperform

---

## DISORGANISATION & NEGATIVE EXPERIENCE EVENTS

- **Disorganisation**: When triggered (e.g., from Support player failure, or pulling back from a lead), team ratings drop temporarily. The larger the drop level, the bigger the performance hit.
- **Negative Experience event**: Affects all ratings as if going into disorganisation. Depends on the experience levels of both teams — more experienced teams suffer less.

### Disorganisation level → team performance %

| Org Level | Performance |
|-----------|------------:|
| Solid | 95–98% |
| Passable | 89–94% |
| Inadequate | 83–88% |
| Weak | 76–82% |
| Poor | 66–75% |
| Wretched | ≤65% |

Disorganization can occur at **any minute** during the match (example: HT match 668299582 had a 13' break).

**Negative experience event captain weighting**: The captain's leadership × 3 and experience × 2 (vs ×1 for all other players). The default-chosen captain is not always optimal — using exact formula or the 3×LS, 2×XP rule of thumb usually gives better results.

Exact team-experience formula (HO):
```
Total Player XP = (sum of 11 players' XP + captain XP) / 12 × (1 − (7 − captain LS) / 20)
```

No negative experience message in League / Friendly matches — only Cup, ladder, tournament, play-off, and NT matches.

---

## MATCH DYNAMICS / PULLBACK (latest mechanics)

A team that gains a lead of two goals automatically starts to lose attacking momentum and focus more on defence. This effect scales with goal difference:

- **Each goal of lead beyond 2: −9% attack, +7.5% defence**
- Each goal pulled back: reverses one increment.
- Cap: lead difference of **8 goals**, after which ratings stop changing.

These are the latest official numbers from the manual (older Unwritten Manual versions cite −6.25% / +5%, which has been superseded; in turn replacing an even older −15% atk / +10% def).

**Disabled** during:
- "Match of the Season" (MOTS)
- National Cup final
- World Cup final
- Hattrick Masters final
- The last league round of the season

---

## HATSTATS
Hattrick's internal rating unit. Each sector rating (midfield, attack, defence per side) is expressed in "Hatstats" as a combined star-based value. Used in all chance and conversion formulas. Foxtrick displays Hatstats for your team and opponents in pre-match analysis.

---

*Sources: devblog.hattrick.org (HT-Tasos 2016/2017/2018/2020, HT-Jens), wiki.hattrick.org, official HT editorials, the Unwritten Manual #15 by LA-Alpa (Hattrick Global English forum thread 17665541, sections 13 "Set Pieces & Special Events" and 14 "Tactics"), Live data studies by nickarana (manager 884407) on chance distributions, conversion rates, and CA mechanics.*
