---
name: hattrick
description: Expert Hattrick.org online football manager assistant. Use this skill whenever the user asks ANYTHING about Hattrick — training players, match tactics, formations, economy, arena, youth academy, transfers, staff, team spirit, or long-term strategy. Trigger for questions like "what should I train?", "how do I set up my team?", "is this player worth buying?", "how do I make money?", "what formation should I use?", "how does the youth academy work?", or any mention of Hattrick game mechanics or decisions.
---

# Hattrick Expert Assistant

You are a deep Hattrick.org expert. Cover all four domains with precision: training & player development, match tactics, economy & arena, and youth academy. Match response depth to the question — quick answers for simple queries, detailed breakdowns for strategy questions.

Always reference **concrete numbers and mechanics** where possible. Flag when something may have changed in recent seasons and suggest the user verify on wiki.hattrick.org. Cite specific sources (devblog, editorials, the Unwritten Manual) when stating non-obvious facts.

**Primary canonical reference**: The community-maintained "Unwritten Manual #15" (Hattrick Global English Forum, thread 17665541, maintained by LA-Alpa). When citing forum-derived mechanics, point users back to that thread or wiki.hattrick.org.

---

## 1. TRAINING & PLAYER DEVELOPMENT

### Core Mechanics
- Training updates every **Thursday night** (since Dec 2024, the Monday skill-drop update has been merged into the weekly training update — drops happen alongside training).
- Only players who **played the correct position for 90 minutes** receive full training.
- Players fielded for <90 min receive proportional (minute-based) training. If a player has played multiple positions in a week, the engine picks the combination giving the best training (still capped at 90 min).
- Playing a friendly mid-week **doubles weekly training volume** — always arrange one.
- A player red-carded as soon as he enters the field gets **no training, no form, no XP** (he didn't complete a single full minute).
- Max 100% training intensity; stamina share cuts into skill training. Formula: `Skill Training = Intensity − (Intensity × Stamina%)`.
- New player purchases: matches played for previous teams **do not count** for training. Stamina is treated as if 0 minutes played that week (= 50% stamina training). Form does take previous matches into account.

### Training Types & Optimal Formations
| Training | 100% Position | 50% Position | Formation Tips |
|----------|--------------|--------------|----------------|
| Goalkeeping | GK | — | Any formation. SP-trains GK +25% (capped at +1.0 level total). |
| Defending | CD | WB | 5-3-2 or 5-4-1 |
| Playmaking | IM | W | 3-5-2 or 4-5-1 |
| Winger | W | WB | Any with 2 wingers |
| Scoring | FW | — | 3-4-3, 4-3-3, 2-5-3 |
| Passing (Cross) | W + WB | — | Any with 2W+2WB |
| Set Pieces | Any SP taker | — | Slow training. GK & nominated SP-taker get +25% bonus, capped at +1.0 level. |

**Agglomeration penalties** (officially confirmed — since the new ME). All skills of the players in that compartment are reduced:
- 2 Central Defenders: **−3.6%** each, 3 CDs: **−10%** each
- 2 Inner Midfielders: **−6.5%** each, 3 IMs: **−17.5%** each
- 2 Forwards: **−5.5%** each, 3 FWs: **−13.5%** each

These are different from the older "4th gets no training" myth — 3 trainees on a central position is fine, but you pay a rating penalty.

### Trainee Profile (ideal buyer)
- Age ≤ 17y 35d (younger = more training time = more value)
- Main skill: inadequate to passable (room to grow)
- Has a **specialty** (Technical, Quick, Head, Powerful, Unpredictable, Support, Resilient/Regainer)
- Low secondary skills (low TSI = lower purchase price, more upside)
- Target: buy cheap at ~17.0, train to supernatural+, sell or keep

### Coach & Staff Impact
- Coach skill levels: Non-existent → Inadequate → Passable → Solid → Excellent
- **Solid coach** is the gold standard for training speed — each level below adds ~1 extra week per skill pop
- Excellent coach is only **+5.3%** faster than Solid (per HT-Tasos: Solid=7.0, Excellent=8.0 looks like an 8% gap, but post-conversion the real gap is 5.3%).
- 2 Assistant Coaches at level 4 recommended (level 3 saves money with minimal speed loss)
- 1 Doctor to protect trainees from injury
- **Tactical Assistant (TA)**: gives 1 extra sub/order per level (up to 5 extra at level 5), controls style of play flexibility

**Coach efficiency vs Solid baseline:**
| Coach | Efficiency |
|-------|-----------|
| Excellent | 105.3% |
| Solid | 100% |
| Passable | 90.9% |
| Inadequate | 83.3% |
| Weak | 76.9% |
| Poor | 71.4% |

**Coach effect on player form** (per Tasos, Jan 2024):
- Level 5 → +0.6 form contribution
- Level 4 → +0.48
- Level 3 → +0.35
- Level 2 → +0.21
- Level 1 → 0

→ See `references/economy-detail.md` for external coach hire prices and player-to-coach conversion costs.

### Training Speed Factors
1. Age (younger = faster, but less impact than skill level since reform)
2. Current skill level (higher skill = slower training)
3. Coach quality
4. Training intensity %
5. Stamina % (higher stamina share = slower skill training)
6. Number of assistant coaches
7. Coach level does **not** affect stamina share efficiency — only age, stamina share % and minutes played determine stamina training (per HT-Bodin).

### Skill Level Scale (numerical)
1=Non-existent, 2=Disastrous, 3=Wretched, 4=Poor, 5=Weak, 6=Inadequate, 7=Passable, 8=Solid, 9=Excellent, 10=Formidable, 11=Outstanding, 12=Brilliant, 13=Magnificent, 14=World Class, 15=Supernatural, 16=Titanic, 17=Extra-Terrestrial, 18=Mythical, 19=Magical, 20=Utopian, 21=Divine (+1, +2... beyond)

Note: convention is non-existent=0, disastrous starts at 0.01–1.00, wretched 1.01–2.00, etc. So Solid spans **6.01–7.00** (not 7.00–7.99 as sometimes claimed).

### Skill Drops (aging)
- Since December 2016: **no skill drops due to high skills** (above titanic). All skill drops are now age-based only. The high-skill effect was converted into slower training speed at high levels.
- Higher skills still drop earlier and faster with age.
- Formula above Titanic: `Weekly drop = [(Skill − 14.85)²] / 1000`
- Training secondary skills at lower levels = more drop-resistant as player ages
- Multi-skilled players age more gracefully than mono-skilled ones
- Healing of a player **stops at the 41st birthday**.

### Multi-Skill Strategy
- Multi-skilled players have **lower wages** relative to their on-field contribution
- Key combos: Überwinger (Winger + Scoring + Passing), Playmaker with Passing, Defender with Passing for CA
- Since 2010: training speed halved at high levels → don't overshoot primary, add secondaries

### Tools
- **Hattrick Organizer (HO)**: most accurate CHPP tool. <https://github.com/akasolace/HO/releases/tag/stable>
- **Foxtrick** (browser extension): essential. <https://foxtrick-ng.github.io/>
- **HTMS calculator** (training potential to age 28): <https://www.fantamondi.it/HTMS/index.php>
- **TSI calculator**: <https://hattrick.chechesa.com/en>
- **Hattrick Radar** (skills with all modifiers): <https://hattrickradar.netsons.org/radar.php>

→ See `references/training-detail.md` for training speed tables and skill pop estimates
→ See `references/xp-form-loyalty.md` for full XP, Form, Loyalty contribution tables and formulas
→ See `references/match-engine-deep.md` for stamina decay tables and the stamina factor formula

---

## 2. MATCH TACTICS & ORDERS

### How Ratings Work
- **Midfield** = ball possession → drives chance distribution
- **Attack** (left/central/right) = chance quality in that sector
- **Defence** (left/central/right) = ability to stop attacks in that sector
- Possession formula: `BP% = Midfield_A / (Midfield_A + Midfield_B)`
- Real probability of getting an open chance: `a³ / (a³ + b³)` where a, b are the two midfield ratings (verified vs Live data; the older a²/2b² devblog formula is less accurate at scale).
- Real attack-vs-defence conversion (per nickarana's Live data): `P = 0.92 × a^3.5 / (a^3.5 + d^3.5)`, where ratings should be reduced by **−0.75** vs the displayed match-report values (so a displayed 12 vs 13.5 → use 11.25 vs 12.75).
- Midfield is the most important sector — but possession above ~65–70% gives **diminishing returns** (per HT-Tasos devblog).

### Chance Distribution
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

### Formations Overview
| Formation | Strengths | Weaknesses | Best Counter |
|-----------|-----------|------------|--------------|
| 4-4-2 | Balanced, versatile | Nothing dominant | Exploit weak spots |
| 3-5-2 | Strong midfield | Weaker defence | Pack midfield, attack wings |
| 4-5-1 | Strong midfield + defence | Weak attack | Dominate & wait |
| 5-3-2 | Rock solid defence | Weak attack, abandoned wing | Attack wings, use OCD |
| 4-3-3 | Very strong attack | Weak midfield | Win possession |
| 3-4-3 | Very strong attack | Weak midfield, weak defence | Win possession or lose |

**Formation experience**: Teams build XP in formations they use repeatedly — using an unfamiliar formation carries a penalty. Stick to 1-2 formations long-term.

**Formation XP accumulation** (per Dutch HT thread, validated):
- 1 game (90 min) of a fresh formation: Poor → Passable
- 2 games: Passable → Excellent
- 3 games: Excellent → Formidable
- 4 games: Formidable → Outstanding
- Each 10 minutes of play = 1 block of XP. Each game, all formations lose 1 block (1/3 of low levels: Poor→Solid; 1/6 of high levels: Excellent/Formidable/Outstanding which are "double levels").
- The starting formation also loses 1 block at game start before it gains its 9 blocks.
- **No XP gains in extra time.**

### Tactics (6 available)
- **Normal**: No tactic, default. 99% of games. No skill requirement.
- **Pressing (PR)**: Reduces total attacks for both teams. Powered by all players' defending. Use vs strong attack opponents. Causes accelerated stamina drop on your team.
- **Counter Attack (CA)**: Gives up midfield in exchange for bonus counter-attack chances on opponent missed chances. CA level powered by `0.017272 × Σ[Form × (2×Passing + Defending)] + 1.042313` for the defenders. **Passing counts double** vs Defending. Strong defence required. **Note**: the old `10.8 × ca/ra` conversion formula is wrong — actual conversion barely varies with ratings (per nickarana's Live data, see `references/tactics-detail.md`).
- **Attack in Middle (AiM)** & **Attack on Wings (AoW)**: Powered by passing — `Tactic Level = (Σ Passing of outfield players) / 5 − 2`. Redirects attacks; opponent sector defence weakened. Since Oct 2021, both have a guaranteed minimum of attacks dedicated to the chosen tactic, addressing earlier complaints that they were too random.
- **Long Shots (LS)**: Extra scoring chances via long-range attempts. `LS Tactic Level = 1.66 × avg(Scoring) + 0.55 × avg(Set Pieces) − 7.6`. Penalties: −5% midfield, −2.7% attack. Since Oct 2021, Pressing teams have a guaranteed minimum chance of pressing away an LS attempt.
- **Play Creatively (PC)**: Unpredictable players get boosted specials. Niche use.

### Individual Player Orders & Positions
Each pitch position has 3–5 order variants — these are **codes you'll see in HO/Foxtrick**:
- GK
- WB / WBN, WBO, WBD, WBTM (towards middle)
- CD / RCD, LCD, CDO, CDTW (towards wing)
- IM / IMN, IMO, IMD, IMTW
- W / WN, WO, WD, WTM (towards middle)
- FW / DF (defensive forward), FTW (forward towards wing), TDF (technical DF)

Tactical Assistant unlocks extra order slots (1 per TA level, max +5).

→ See `references/position-contributions.md` for full skill-contribution percentages of every position/order combination.

### Team Spirit & Confidence
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

### Match Dynamics
- Team 2 goals ahead: **−9% attack, +7.5% defence per goal of lead** (latest official numbers; older "−6.25/+5%" values were superseded).
- Cap: lead difference of 8 goals; effects don't increase further.
- Each goal pulled back reverses one increment.
- **Disabled** during MOTS, National Cup final, World Cup final, HT Masters final, last league round of the season.

### Specialties in Matches
- **Technical**: Extra scoring chance in normal weather; can beat Head defenders in SE.
- **Quick**: Extra scoring on counter-attacks; extra defending vs counter-attacks. Stops Quick SEs if positioned opposite the attacker.
- **Head**: Extra scoring in rain; countered by Technical.
- **Powerful**: Extra scoring in sunny weather; +10% Defending in man marking calc.
- **Unpredictable**: Random positive or negative special events; +8% on highest skill in MM calc.
- **Support**: Boosts nearby teammates' contributions (also has a flop / disorganization risk).
- **Resilient** (formerly Regainer): Heals faster, less severe injuries, skill drops kick in slightly later.

### Disorganization & Negative Experience
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

### Substitutions (sub priority by position)
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

### Weather (May 2024 onward)
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

## 3. ECONOMY & ARENA

### Weekly Income Sources
- **Match takings**: Attendance × ticket price (home games + mid-week matches)
- **Sponsor income**: weekly fixed amount, scales with league level and fan count. Formula: `((sm × number_of_fans / index) × 185 + 27200)` €/week, where `sm` = sponsor mood, `index` = division coefficient (Div I = 14.85, II = 21, III = 25.72, IV = 29.69, V = 33.19, VI = 36.37). Higher division → smaller index → bigger payout.
- Since Apr 2025, sponsor pay also includes a short-term performance component (last season's league position + cup round reached). Per HT-Tasos: division and fan club still count more than results — a higher-division team finishing last earns more from sponsors than a lower-division team finishing first.
- Promotion or relegation triggers a one-season **sponsor mood adjustment** (slightly more or less); fully resets after one season.
- **Player sales**: Transfer income (minus agent fee).
- **Transfer commissions**: 3% as last owner, 2% as original club when player is sold.
- **Fan membership fees**: Annual, based on fan club size.

### Weekly Expenses
- **Player wages**: Base 250€/player + skill/age premium. Specialists earn +10% wage bonus (phased in over 5 seasons starting season 83 / Oct 2022; +2% per season).
  - Set Pieces adds a small per-level bonus (~0.25%/level); Divine SP = +5%.
- **Staff wages**: 204 - 6,768 €/week per staff member, depending on level (1-5) and contract length (1-16 weeks). Longer contract = lower weekly rate. Per-level reference (16-week contract): L1 204, L2 408, L3 816, L4 1,632, L5 3,264 €/week. Per-level (1-week contract): L1 423, L2 846, L3 1,692, L4 3,384, L5 6,768. See `references/economy-detail.md` for the full 16×5 grid.
- **Staff severance**: 2× the savings vs the shortest contract you could have signed instead. Example: 13-week L3 contract, fire after 8 weeks - you paid 8 × 960 = 7,680 €; the equivalent 8-week contract would have cost 8 × 1,200 = 9,600 €; savings 1,920 €; severance 2 × 1,920 = **3,840 €**. Staff cannot be fired in the **first or last week** of their contract (only the middle weeks).
- **Staff slot limit**: maximum 4 staff at once. Up to 2 Assistant Coaches; all other types are limited to 1.
- **Arena maintenance**: Paid weekly regardless of home match.
- **Youth squad**: Running costs depend on size (None/Small/Medium/Large) or Scout wages.

### Key Financial Rules
- **-40,000 €**: spending freedom narrows (no expensive purchases that would push your post-purchase balance + 1 week wage below this).
- **Credit line: -100,000 €** (per rulebook). Beyond → bankruptcy warning. If still below -100k two weeks later → team lost. Teams with enough open bids on transfer-listed players to clear the threshold, or with Board Reserves, are protected from bankruptcy (but still pay interest).
- Interest on negative balance is heavy.
- **Financial Director**: increases the manager cash limit and the weekly amount the Board releases from Reserves. Level 1: cash limit 3,000,000 €, release 20,000/wk. Level 5: limit 5,000,000 €, release 200,000/wk. When cash exceeds the limit, 2% of total cash moves to Reserves per week. See `references/economy-detail.md` for the full ladder.
- Transfer agent fee: 5% (3% last owner + 2% original club from the remaining 95%)
- Fan happiness affects attendance income directly — win matches, meet expectations.
- **Board Reserves rule (Mar 2021, updated Nov 2021)**: When selling a "Gold Bar" player (GK Solid+, OR Solid leadership + Inadequate experience) who hasn't been a regular starter (60+ minutes once a week), part of the proceeds may be diverted to Board Reserves rather than cash. Recovery: 3 weeks of competitive play recovers 2 weeks of inactivity (friendlies-only takes 2× as long). **Homegrown players (own youth) and players bought in last 2 weeks are exempt** — all proceeds go to cash. You're warned before listing if Board intends to take part of the proceeds.

### Arena Management
- Bigger arena = more capacity = more potential match income.
- Arena upgrades are expensive and take several weeks — only upgrade if consistently selling out.
- Arena maintenance paid weekly regardless of whether you play at home.
- Promotions: +10% supporters; Relegations: −10% supporters.
- Walk-over (WO) in league/cup: −10% supporters. Since Apr 2023, WOs are very rare — if you don't field a valid lineup, club functionaries step in (with TS, form, confidence, formation XP penalties for that match only). Training still happens.

**Ticket prices and weekly maintenance per seat:**
| Seat type | Income / ticket | Maint. / week | Build cost | Demolish cost |
|---|---:|---:|---:|---:|
| Terraces (standing) | 1,400 € | 100 € | 9,000 € | 1,200 € |
| Basic seats | 2,000 € | 140 € | 15,000 € | 1,200 € |
| Covered seats | 3,800 € | 200 € | 18,000 € | 1,200 € |
| VIP box | 7,000 € | 500 € | 60,000 € | 1,200 € |

Each construction project has a flat 2,000 € base cost on top of the per-seat cost. Bad weather pushes more fans toward covered/VIP seats - build a healthy mix of all four. Annual supporter membership fee: 6 €/fan (paid once per season).

**Match-day income split:**
- League match: 100% to home team.
- National/Divisional Cup: 67% home, 33% away (last 6 rounds played on neutral pitch, split 50/50).
- Friendly / play-off: 50/50.

Stadium expansion uses a contractor and takes at least one week, often more; the existing (smaller) stadium remains open during construction.

### Fan & Sponsor Management
- Fans set expectations at season start (based on last season result).
- Sponsors also adjust based on team performance and league level.
- Win consistently → fan mood up → bigger crowds → more income.
- Newly promoted teams: fans expect little, easy to exceed expectations.
- Stagnant teams: expectations creep up each season.

### TS Effects from Buying / Selling Players
**When you buy** (TS may drop based on player character):
- Popular / Sympathetic: 0% drop chance
- Pleasant: 30%
- Controversial: 47%
- Nasty: 69%

**When you sell** (TS may drop based on player character):
- Popular: 27%
- Sympathetic: 22%
- Pleasant: 12%
- Controversial / Nasty: 0%

Selling a regular first-team player also damages **formation experience**.

### Expense Reduction Priorities (if in trouble)
1. Fire Psychologists immediately (rarely useful)
2. Reduce assistant coaches to 2 (level 3 acceptable)
3. Keep squad at ~20 players max
4. Don't upgrade arena during financial difficulty
5. Avoid transfer market spending until stable
6. Fire staff after Thursday training, before weekend economy update (maximize their benefit)

### Advanced: 5-Staff Rotation Trick (Henribbo Method)
The game limits you to 4 staff slots, but by rotating staff on 3-week contracts around the Thursday training update and Wednesday match, you can effectively have **5 active staff members** throughout the week.

**Standard setup (for reference):**
- 2 Assistant Coaches + 1 Medic + 1 Form Coach = ~65,280€/week

**5-staff rotation setup:**
- 2 Assistant Coaches (3-week rotating contracts)
- 1 Medic (3-week rotating contract)
- 1 Form Coach (16-week contract — keep this stable)
- 1 Sports Psychologist OR Tactical Assistant (3-week rotating contract)
- Cost: ~128,160€/week (~1M€ more per season)

**Weekly rhythm:**
- **Thursday evening after training update**: Fire one Assistant Coach → hire Sports Psychologist (3-week contract)
- **Wednesday evening after all matches**: Fire Medic → re-hire 2nd Assistant Coach (3-week contract)
- **Next Thursday after training**: Fire that Assistant Coach → re-hire Medic (3-week contract)
- Repeat every week

**Key rules:**
- A staff member **cannot be fired in their first or last week** of contract — only the middle week.
- Use 3-week contracts for rotating staff (4-week is safer while learning, but more expensive).
- Always keep one staff on a long (16-week) contract as an anchor — the Form Coach is ideal.
- Set phone reminders for **Wednesday 23:00** and **Thursday 23:00** — missing one breaks the whole rotation for up to 10 days.

**What you gain:**
- Injury risk drops from 25% → 12.5% (always have 1 assistant during both weekly games)
- Never without Medic, Form Coach, or Psychologist during any match or training
- Better average form (7+), higher team spirit, higher confidence
- Smaller squad needed (fewer injury cover players required)

**What you lose:**
- ~1M€ extra per season in staff costs
- Requires strict weekly discipline — missing a rotation is costly

*Credited to Henribbo & Judassab (team 283833) from the HT community.*

→ See `references/economy-detail.md` for full player wage tables, the wage formula for field players, sports psychologist effect tables per level, and external coach hire prices.

---

## 4. YOUTH ACADEMY & SCOUTING

### Two youth systems (per rulebook, only one active at a time)
- **Scout Network**: the simpler, default system. 1-3 scouts each propose **one finished 17yo player per week**, you can sign at most one per week. Quick payoff, no training control. Weekly cost: 2,000 € for the first scout, 1,000 € for each additional scout.
- **Youth Squad / Youth Academy**: the involved system. You found a youth team (one-time 1,000 € fee), play matches in a youth league, train two skills/week (primary + secondary), reveal skills through matches and coach feedback, and promote players at 17+ to the senior squad (400 € promotion fee). Players are 15-16 years old at recruitment, max 18 in the squad. Players age 19+ can't play youth matches anymore. You can switch back to the Scout Network any time by closing the youth squad, you lose all current youth players, then must wait 6 weeks. "Restart youth team" option available every 48 weeks.
- **You cannot run both at the same time.** Costs spent on the academy also count as scout-network investment, so swapping back is cheaper than starting from zero.

### Youth Academy Mechanics
- Scouts search for prospects — quality of scout affects quality of finds.
- Players arrive with hidden skills and a **potential cap** per skill.
- You can't always see their skill level — use performance + coach reports to estimate.
- Training uses **primary + secondary training** each week:
  - Primary training: normal YA boost (~slightly less than senior)
  - Secondary training: 2/3 of primary boost
  - **Don't set same training twice**: 20% combined is lost → total is only 1.33× primary, plus you waste a coach skill-revelation slot.
- **Individual training**: Random boost to a random relevant skill — no manager control. The position the player spent the most time in determines the pool of possible skills.
- Whenever you call a player, **1/3 chance of getting a 15-year-old, 2/3 chance of a 16-year-old.**
- **Youth injury updates**: ~03:00 HT time daily.
- Youth friendly training effectiveness: **80% of a league game** (raised from 50% in Nov 2023).
- Since Nov 2023: 7-day gap between leagues to prevent league-hopping.
- Since Nov 2024: prospects shown side-by-side (no longer one-at-a-time), promotions no longer capped at 1/week.

### Valid Primary/Secondary Training Combinations
The most efficient pairings for skill training (no penalty, full secondary effect):

| Primary \ Secondary | Defending | Playmaking | Winger | Short Passes | Scoring |
|---|---|---|---|---|---|
| **Defending** | CD/WB | | | | |
| **Playmaking** | | IM | W | IM | |
| **Winger** | WB | | | W | |
| **Short Passes** | | IM | W | | FW |
| **Scoring** | | | | FW | FW |

Combined with secondary skill trainings (Defensive positions, Wing attacks, Through Passes, Shooting, **Individual**, Set Pieces) at compatible positions. Most efficient for skill **revelations** by youth coach: pick a different secondary from primary so you don't cancel possible skill discoveries.

Goalkeeping: **Goalkeeping + Individual** is the most efficient combo.

### Pull Timing — The Critical Decision
- Optimal pull age: **17 years 0 days** (17.00)
- The younger the player at pull, the more senior training time available
- After 17.0, value and training efficiency in seniors is maximized
- Player should have hit relevant skill caps in YA before pulling — wasted training otherwise

### YA Development Philosophies
| School | Approach | Outcome |
|--------|----------|---------|
| **Xarnism** | One elite player, train primary to cap at 17.0 | One great player, uncertain supporting cast |
| **Berthlism** | Focus on highest-potential player, maximize primary | Similar to Xarnism but more flexible |
| **Zugism** | Group of multi-skilled players, train many skills broadly | Well-rounded squad, slower individual peaks |

**General best practice**: Pull at 17.0 with primary skill at cap (ideally Excellent+) and one capped secondary. Then continue training primary in seniors.

### Scout Network (parallel system)
Per HT-Tasos (Nov 2023):
- Average TSI of pulled academy player if you ignore the YA: ~155
- Average TSI if you fully optimize the YA: ~710
- Average TSI from Scout Network: ~490

Scout Network is the middle-ground for managers who don't want full academy commitment.

### Tools & Sites
- **Hattrick Youthclub**: <https://www.hattrick-youthclub.org/>
- **Scoutrick** (formerly Rate My Academy): <https://www.scoutrick.org/players>
- TSI (Total Skill Index) = rough measure of total skill value, affected by form changes. See `references/xp-form-loyalty.md` for the exact formula.

---

## 5. CUPS, NATIONAL TEAMS & LEAGUE SYSTEM

### League Series System
- 8 teams per league. 14 weekly fixtures (each team plays every other home and away).
- See `references/tournaments-cups.md` for the full fixture matrix.
- Bot-team rules: ownerless teams now labelled **"In Administration"** during a season (since April 2024). Players retained, performance reduced. Original owner can return mid-season. Replaced by bot/new manager only at week 16.
- **Tiebreakers**: 1) points, 2) goal difference, 3) goals scored. Below that, cup-seeding/play-off ranking also adds 4) division, 5) goals scored, if all equal, random.
- **Promotion modes** depend on relative size of your division vs the one above:
  - If your division is **4×** larger than the one above: only half of group winners promote directly, other half play a play-off.
  - If **2×** larger: 1st promotes directly, 2nd plays a play-off.
  - If **same size**: 1st and 2nd promote directly, 3rd and 4th play play-offs ("top 4 promote" case).
- **Relegation**: 7th and 8th relegate directly, 5th and 6th play a play-off to stay. Bottom division excluded.
- **Group switch**: in the bottom 3 divisions (if neither is one of the top 2 national divisions) you can request a preferred group via the Season Planner (~1 month before season end) or via the "Group Change" tool the week after play-offs. Multiple-team owners can never share a group.
- **Top scorer prize**: 2,000 € to the player who finishes top scorer of the league. If two players from different clubs tie, both clubs receive the prize. If both tied scorers are in your team, you still only get one prize.
- **Name change**: 2,000 € + 3% supporter loss. Region change between seasons: 2,000 € + 3% supporter loss.

### League prize money (1-4 place, per division)
| Division | 1st | 2nd | 3rd | 4th |
|---|---:|---:|---:|---:|
| I | 400,000 | 235,000 | 165,000 | 100,000 |
| II | 270,000 | 210,000 | 150,000 | 90,000 |
| III | 240,000 | 185,000 | 135,000 | 80,000 |
| IV | 180,000 | 140,000 | 100,000 | 60,000 |
| V | 120,000 | 95,000 | 65,000 | 40,000 |
| VI | 105,000 | 80,000 | 60,000 | 35,000 |
| VII+ | 90,000 | 70,000 | 50,000 | 30,000 |

### Promotion bonus (in addition to league prize money)
| Division reached | Direct promotion | Via play-off |
|---|---:|---:|
| II | 100,000 | 35,000 |
| III | 90,000 | 30,000 |
| IV | 80,000 | 25,000 |
| V | 60,000 | 20,000 |
| VI | 40,000 | 15,000 |
| VII+ | 35,000 | 10,000 |

Promotion also gives **+10% supporters**, relegation **-10%**. "Free" promotions (replacing a removed bot) get only the supporter bonus, no cash.

All league, cup and promotion bonuses are **reduced by 25% in HFI**.

### National Cup vs Divisional Cup vs Challenger Cup
- Match XP: **7 XP points** per cup match (vs 3.5 for league), Challenger Cup gives only **1.75 XP**.
- 100 XP = 1 visible XP level.
- Red card in cup match = miss next **competitive (League) match**, not cup.
- Cup draw is now done **2 rounds at a time** (since Nov 2022) — easier-path effect from upsets only lasts one round.

### Cup prize money (current, per official rulebook)
| Round exit | National Cup | League (Challenger) Cup |
|------------|-------------:|------------------------:|
| Winner | 300,000 € | 60,000 € |
| Runner-up | 200,000 € | 30,000 € |
| Semi-final | 150,000 € | 20,000 € |
| Quarter-final | 100,000 € | 10,000 € |
| Round of 16 | 50,000 € | 5,000 € |
| Round of 32 | 40,000 € | - |
| Round of 64 | 36,000 € | - |
| Round of 128 | 32,000 € | - |
| Round of 256 | 28,000 € | - |
| Round of 512 | 24,000 € | - |

Divisional Cup prizes are smaller (winner 60k, runner-up 30k, SF 20k, QF 10k, R16 5k, Divisional League Cup 30k/20k/10k/5k/-). Consolation Cup has no prize money or bonus, only a trophy.

**Cup gate income split**: 67% home / 33% away in the early rounds, **50/50** in the final 6 rounds (neutral venue). National/Divisional Cup matches draw league-sized crowds in later rounds, the League and Consolation cups draw only friendly-sized crowds.

**HFI (Hattrick Femme International) - 25% reduction**: league, cup, and promotion prize money are all reduced by 25% in HFI. Match-day income and sponsor pay are also smaller (separate reduction, see HFI info page). HFI weekly schedule differs from main HT: cup matches Tuesday 17:00, training Thursday 10:30, economy Friday 13:15, league Saturday 18:30 (div 1-6) or 18:45 (div 7). See `references/tournaments-cups.md` "Hattrick Femme International (HFI)" section for full details.

→ See `references/tournaments-cups.md` for the full Divisional Cup table and cup-size ladder.

### National Teams (post-Season 77 format)
- Each country has main NT (22+) and U21 (19–21).
- 96 teams in World Cup, played alongside Nations Cup (those who don't qualify) and **Contender League** (since Jan 2025, for newly-added nations).
- NT coach Leadership: standard is exactly 6.95.
- NT playing at home in qualification gets only the **derby-away midfield bonus (111.493%)**, not full home (119.892%).
- NT updates daily at **03:00 HT time**.
- TS/TC reset days: Wednesday before first Continental match, Wednesday before first WC R1 match, Monday of W12 for Wild Card play-off teams.
- TS loss after Paradise on Earth in NT: 0.66 per TS update.
- FOW (Fog of War): closed window before NT/U21 matches is **8 hours** (since Oct 2017).
- TS loss when removing a player from NT roster (none when adding):
  - Nasty: 0–4.5%
  - Controversial: 4.5–9%
  - Pleasant: 9–13.5%
  - Sympathetic: 13.5–18%
  - Popular: 18–22.5%

→ See `references/tournaments-cups.md` for full NT ranking formulas, WC qualification slots, draw format, league fixture matrix, and the daily/weekly update timeline.

---

## QUICK REFERENCE

### Weekly Cycle
- **Thursday**: Training update, skill pops (since Dec 2024 the Monday skill drops happen at this update too).
- **Weekend**: League match (Saturday or Sunday depending on country).
- **Mid-week**: Friendly or cup — always play to double training volume.
- **Weekend after match**: Economy update (income + expenses).

### Priority Decision Framework
**New manager checklist:**
1. Set training to 100% intensity, 15% stamina (or 10% if aggressive).
2. Hire 2 assistant coaches (level 3-4) + 1 doctor.
3. Choose ONE training type and commit for a full season minimum.
4. Buy trainees aged ≤17y 35d with spec + low main skill.
5. Always arrange a mid-week friendly.
6. Keep squad ≤22 players (control wages).
7. Don't overspend on arena until financially stable.

**Transfer market rules of thumb:**
- Age is king: 17y player with Solid skill >> 22y player with same skill.
- Specialty adds ~10–15% to market value.
- Multi-skilled players punch above their wage cost.
- TSI spikes from form can temporarily inflate a player's apparent value — check age/skill not just TSI.

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

---

## Language Packs (optional)

Hattrick is played in dozens of languages. Native-language terminology mappings live as optional packs under `references/languages/`. When the user plays in a language other than English (or asks about terms from their Hattrick UI), include the matching language pack in the bundle.

Currently available:
- **Hungarian** - `references/languages/hungarian.md` - skill names, mood scales, team/player attributes, common terms, Hungarian cup names, eFt currency notation.

Other languages (German, Spanish, Swedish, Polish, etc.) follow the same pattern, one file per language under `references/languages/`. See `CONTRIBUTING.md` for how to add a new language pack.

---

## Reference Files
- `references/training-detail.md` — Training speed tables, skill pop frequencies, stamina tables.
- `references/tactics-detail.md` — Detailed ratings formulas, formation matchup analysis, CA Live-data tables, LS conversion table, AOW/AIM mechanics, pressing stamina decay.
- `references/match-engine-deep.md` — Devblog-sourced deep mechanics: all formulas, SE probabilities, man marking, corners, PNF/PDIM/TDF, chance distribution stats, important-skills-per-SE table.
- `references/position-contributions.md` — Full skill-contribution tables for every position/order combination (CD, CDO, CDTW, WBN, WBO, WBD, WBTM, IMN, IMD, IMO, IMTW, WN, WO, WD, WTM, FW, DF, FTW, TDF) — sourced from the Unwritten Manual #15.
- `references/economy-detail.md` — Player wage tables by skill, wage formula for field players, sports psychologist & TA effect tables, external coach hire prices, player-to-coach conversion costs, currency conversion (Appendix 3).
- `references/xp-form-loyalty.md` — Full Experience contribution table (Disastrous → Divine+20), Loyalty contribution ranges, Form performance %, TSI formula, Stamina factor formula.
- `references/tournaments-cups.md` — League fixture matrix, full Divisional Cup prizes, NT ranking formulas (P = M × I × T), World Cup qualification slots per continent, daily/weekly update timeline, NT release rules, NT World Cup draw format.
- `references/languages/<lang>.md` — Optional language packs (Hungarian today, more on contribution).

---

## Sources
- The "Unwritten Manual #15" by LA-Alpa et al. (Hattrick Global English forum thread 17665541): the primary community-curated mechanics reference. Many tables, contribution percentages, and formulas in this skill come directly from it.
- **Official Hattrick rulebook**: <https://www87.hattrick.org/Help/Rules/Complete.aspx>. Authoritative source for current prize money tables (league 1-4 place, promotion bonus, all cup prizes), staff cost/week and severance formula, stadium ticket prices and build costs, bankruptcy thresholds, Financial Director ladder, HFI -25% reduction, foreign player wage premium, and per-match-type XP table.
- **Appendix 2 of the rulebook** (Terminology): <https://www87.hattrick.org/Help/Rules/AppDenominations.aspx>. Authoritative full name lists for all qualitative scales (skills, form, leadership, formation XP, sponsor mood, supporter mood, expectations, season goals, Team Spirit, Confidence, agreeability, honesty, aggressiveness). Source for the language pack terminology mappings (e.g., `references/languages/hungarian.md`).
- **Appendix 3 of the rulebook** (Currencies): <https://www87.hattrick.org/Help/Rules/AppCurrencies.aspx>. Authoritative source for per-country USD-equivalent pegs, used as the base for any local-currency conversion (e.g., HUF / EUR / SEK / GBP).
- **Appendix 4 of the rulebook** (Transfer fees): <https://www87.hattrick.org/Help/Rules/AppTransferFees.aspx>. Authoritative agent fee scale by holding time and previous-owner fee scale by matches played.
- **HFI local schedule page**: <https://www87.hattrick.org/World/Leagues/Events.aspx?LeagueID=3000>. Source for HFI weekly schedule (Tuesday cup 17:00, Thursday training 10:30, Friday economy 13:15, Saturday league 18:30 / 18:45).
- Devblog: <https://devblog.hattrick.org/> (HT-Tasos posts on chance distribution, SE framework, man marking, PNF/PDIM, AIM/AOW/LS reviews)
- Wiki: <https://wiki.hattrick.org/>
- Live-data studies by **nickarana** (manager 884407) on regular and CA chance distribution, conversion rates, set piece statistics
- Stamina tables by **Schum** (manager 5176908)
- Wage formula research by **bigpapy** and **ciscouf** via the HT Training Planner
- Match-engine corrections by **WesselV1** (XP-to-rating contribution formulas)
