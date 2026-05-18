# Tactics & Match Engine Detail Reference

Updated with formulas and Live-data tables from the Unwritten Manual #15.

---

## Match Ratings Structure
Every match produces ratings in 7 sectors:
- **Midfield**: Drives possession and chance distribution for the entire match
- **Right Attack / Central Attack / Left Attack**: Chance quality when attacking in each zone
- **Right Defence / Central Defence / Left Defence**: Ability to stop attacks in each zone

Midfield rating is the single most impactful number — it determines what % of chances are created for each side.

### Real-data formulas
- Possession: `BP% = Midfield_A / (Midfield_A + Midfield_B)`
- Probability of getting an open chance: `a³ / (a³ + b³)` (the older Tasos-devblog `a²/2b²` is less accurate at scale; verified from Live data by nickarana, thread 17572304.373).
- Real attack-vs-defence chance conversion: `0.92 × a^3.5 / (a^3.5 + d^3.5)`. Use ratings reduced by **−0.75 vs the displayed match-report values** (so a displayed 12 vs 13.5 → use 11.25 vs 12.75).

---

## Skill Contributions by Position

For full position/order contribution percentages, see `references/position-contributions.md`.

Quick mental model:
- **Midfield (Playmaking)**: IM is primary; Wingers contribute heavily; FWs and CDs add small amounts.
- **Wing Attack**: Wingers (Winger skill) primary; FWs (Scoring secondary, Winger secondary); WBs offensive contribute.
- **Central Attack**: FWs primary (Scoring); IMs (Scoring + Passing) significant.
- **Central Defence**: CDs primary; IMs (Defending) and GK (Goalkeeping) secondary.
- **Side Defence**: WBs primary; CDs (especially RCD/LCD/CDTW) and Wingers (defensive order) contribute.

---

## Tactic Mechanics Detail

### Counter Attack (CA)

**CA Tactic Level formula** (per Unwritten Manual):
```
CA Level = 0.017272 × Σ[Form × (2×Passing + Defending)] + 1.042313
```

Sum is across your defenders. **Passing counts double Defending** for CA level — defenders with Passing skill make CA strong.

**Old conversion formula** (now disputed): `Conversion = 10.8 × ca / ra`, where `ra` = sum of both teams' ratings without ×3 midfield. This is in the Unwritten Manual but has been shown to be **wrong** by nickarana's Live data analysis (thread 17493341.115):

> The conv% hardly varies based on the average rating in the match. The CA Formula assumes too much power for the "ra" factor. It's fairly close at lower ra levels but progressively wrong as ra goes up.

| CA Tactic Level | Match Avg Rating 10 | 11 | 12 | 13 | 14 |
|---:|---:|---:|---:|---:|---:|
| 16 | 33% | 33% | 32% | 31% | 30% |
| 17 | 34% | 35% | 34% | 33% | 32% |
| 18 | 36% | 36% | 35% | 35% | 34% |
| 19 | 35% | 37% | 37% | 36% | 36% |
| 20 | 39% | 39% | 38% | 37% | 36% |

(Live data; conv% varies far less with `ra` than the formula predicts.)

**CA Trigger Rate** (probability of converting an opponent's missed normal chance into a CA chance, by tactic level):

| Tactic Level | CA Trigger % |
|---:|---:|
| 6 | 3% |
| 8 | 7% |
| 10 | 13% |
| 12 | 19% |
| 14 | 25% |
| 16 | 32% |
| 18 | 35% |
| 20 | 38% |
| 22 | 41% |
| 24 | 43% |
| 26 | 43% |
| 28 | 43% |
| 30 | 47% |

Plateaus around 43–45% at high tactic levels (data from matches with both teams 400+ Hatstats).

**Probability of getting X CAs given Y normal missed chances by opponent** (CA tactic 17–18):

| Opponent missed chances | 0 CA | 1 CA | 2 CA | 3 CA |
|---:|---:|---:|---:|---:|
| 1 | 66% | 34% | — | — |
| 2 | 37% | 55% | 8% | — |
| 3 | 19% | 56% | 23% | 1.5% |
| 4 | 9% | 47% | 38% | 6% |
| 5 | 5% | 35% | 44% | 16% |
| 6 | 2% | 24% | 43% | 27% |

**CA conversion evolution within a match**: After a successful CA, the next CA's success rate drops; after a failed CA, the next CA's rate rises. The system "returns to the mean" — overall conversion stays stable around the target rate (~34% for ratings 15–20). See thread 17493341.75 for full table.

**Strategic notes**:
- Midfield penalty: ~7% for choosing CA (effective coefficient 93%).
- Best used: opponent has stronger midfield + you have strong defence + Passing on defenders.
- CA chances trigger on opponent's *missed normal* chances, so a strong defence that forces missed chances is fundamentally synergistic.
- Defensive order on defenders increases CA defence contribution.

### Pressing (PR)
- Powered by: Sum of all players' Defending skills.
- Effect: Reduces total attacks for both teams proportionally to tactic level.
- Best used: You have a goal lead and want to protect it; opponent has weak defenders.
- **Stamina cost**: severe — your team's effective ratings drop sharply over the match.

**PR rating decay during match** (vs starting rating):

| Minutes | %PR-rating |
|---|---|
| 0–5 | ~100% |
| 25 | ~99% |
| 35 | ~96% |
| 45 (HT) | ~92% |
| 60 | ~95% (recovers a bit) |
| 75 | ~87% |
| 90 | ~77% |
| Overtime avg | ~70% |

(From Live data; ~9k matches first half, 8k second.)

Pressing only makes sense if your defending skills are sufficient to power a useful tactic level *and* you can sustain stamina-costly play.

### Long Shots (LS)

**LS Tactic Level formula:**
```
LS Tactic Level = 1.66 × avg(Scoring of outfield players) + 0.55 × avg(SP of outfield players) − 7.6
```

(Equivalent calculator: <https://ht.alergromania.ro/tools/tactic-long-shots/>.)

Penalty for choosing LS: −5% Midfield, −2.7% Attack.

**LS Tactic Level → conversion probability** (per chance redirected to a long shot):

| LS Level | Conversion |
|---:|---:|
| 1 | 3.48% |
| 2 | 6.70% |
| 3 | 9.69% |
| 5 | 15.02% |
| 7 | 19.59% |
| 10 | 25.28% |
| 12 | 28.40% |
| 15 | 32.29% |
| 17 | 34.42% |
| 20 | 37.07% |

Conversion formula: `0.474 × (1 − exp(−0.0762 × tactic_level))`.

**Goal probability formula** (LS goal probability vs opponent's defence):
```
Attack  = 0.0643 × Scoring^2.3808 × SP^2.7720
Defense = 1977.4524 × GK^0.9 + 31.4827 × SP^2.3262
LS Goal Probability = Attack / (Attack + Defense)
```

GK and Scoring are modified by all the usual modifiers (form, stamina, XP, loyalty, weather). **SP does not use form or stamina** in this calculation.

**LS Tactic Level → "Total" Scoring+SP shorthand:**

| LS Level | TOTAL = 3×avg(SC) + avg(SP) |
|---:|---:|
| 4 (weak) | 20.4–23.0 |
| 6 (passable) | 24.7–25.9 |
| 8 (excellent) | 27.9–29.4 |
| 10 (outstanding) | 31.2–33.1 |
| 12 (magnificent) | 34.3–36.2 |
| 14 (supernatural) | 37.9–40.0 |
| 16 (extraterrestrial) | 42.2–43.9 |
| 18 (magical) | 45.6–? |

**Pressing vs Long Shots (Oct 2021 review)**: Pressing teams now have a guaranteed minimum chance to press away an LS attempt. The LS team retains an overall advantage but the floor is no longer 0%.

### Attack on Wings / Attack in the Middle (AoW / AIM)

**AOW/AIM Tactic Level formula**:
```
Tactic Level = (Σ Passing of outfield players) / 5 − 2
```

**Sum of Passing → Tactic Level:**

| Σ Passing | Tactic Level |
|---:|---|
| 30 | Weak |
| 35 | Inadequate |
| 40 | Passable |
| 45 | Solid |
| 50 | Excellent |
| 55 | Formidable |
| 60 | Outstanding |
| 65 | Brilliant |
| 70 | Magnificent |
| 75 | World Class |
| 80 | Supernatural |
| 85 | Titanic |
| 90 | Extra-Terrestrial |
| 95 | Mythical |
| 100 | Magical |
| 105 | Utopian |
| 110 | Divine |

**Effect:**
- AiM redirects up to 40% of attacks centrally; weakens side defences.
- AoW redirects attacks to wings; weakens central defence.

**Oct 2021 review**: Both tactics now generate guaranteed attacks dedicated to the chosen tactic, addressing the previous complaint that attacks could randomly fall outside the redirected sector.

### Play Creatively (PC)
- Only Unpredictable players benefit.
- Creates bonus special events for those players.
- Niche — only useful with multiple Unpredictable specialists in central/attacking positions.

---

## Specialty Events Table (high-level)

| Specialty | Positive Event | Negative Event |
|-----------|---------------|----------------|
| Technical | Extra scoring chance (normal weather); can beat Head defender | Gets pushed off ball by Powerful |
| Quick | Extra chance on counter; stops counter | Can be caught by another Quick |
| Head | Extra scoring in rain; corner header advantage | Loses ball to Technical |
| Powerful | Extra scoring in sunny weather; +10% MM defending | None significant |
| Unpredictable | Surprise positive event | Surprise negative event (own goal, mistake) |
| Support | Boosts adjacent teammates | Disorganization risk |
| Resilient (ex-Regainer) | Heals faster, less severe injuries | None |

**Weather interactions:**
- Sunny: Powerful +5% all skills; Technical −5%; Quick −5%
- Rainy: Head specialty favoured (header events); Technical −5% all skills; Quick −5% all skills
- Normal weather: Technical favoured for SE
- Quick players don't suffer weather penalty in the **first half** in sunny conditions.

---

## Team Spirit & Confidence Mechanics

### TS × Attitude × Midfield Multiplier

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

(After season-start TS reset, all teams sit at "composed medium" = 4.50.)

### TS Trick (lowering training intensity)
- Lowering training intensity raises TS that week.
- Must lower **before the last update preceding the training update** (e.g. before Thursday morning if training updates Friday morning).
- Side effects: form drops on subsequent weeks, big TS hit when you return to 100%.
- Calculator: <https://ht.8ic.ro/trainingintensity>.

### Confidence (post-May 2024 system)
- Effects are slower and depend on more factors.
- Goals matter, but fan expectations, coach Leadership, and staff Sports Psychologist all play in.
- Confidence updates **daily during the daily update**, with the visible value drifting toward a hidden background confidence.
- (Pre-May 2024: confidence updated only after match, based purely on home/away goals. 1-0 was 4.5% better than 2-1; 2-1 was 1.8% better than 3-2.)

### Sept 2024 Confidence tweaks
- Starting TC at season start: raised from 4.5 to **5.0**.
- Cannot lose TC after a win (even if opponent scored several goals).

---

## Match Dynamics (Pullback)

- **Automatic pullback (when winning)**:
  - Per goal of lead beyond 2: **−9% attack, +7.5% defence**.
  - Stops scaling at 8-goal lead difference.
  - Effects reverse one increment per goal pulled back.
  - **Disabled** during MOTS, National Cup final, World Cup final, HT Masters final, last league round.

(Older devblog values like −6.25% / +5% per goal are obsolete — these are the latest.)

---

## Disorganization & Performance

When a disorganization message appears, the team performs at the following multiplier of full ratings:

| Disorganization Level | Performance |
|-----------------------|------------:|
| Solid | 95–98% |
| Passable | 89–94% |
| Inadequate | 83–88% |
| Weak | 76–82% |
| Poor | 66–75% |
| Wretched | ≤65% |

Disorganization can occur **at any minute** during the match. Negative experience events also trigger disorganization-like performance loss.

**Captain experience formula:**
```
Total Player Experience = (Σ player_xp_11 + captain_xp) / 12 × (1 − (7 − captain_LS) / 20)
```

The default-chosen captain (the auto-pick) is not always the optimal one. Tools to find the best captain:
- <https://ht.alergromania.ro/tools/find-best-captain/>
- <https://teamxpcalculator.vercel.app/>

---

## Formation Experience Detail

- 1 game (90 min) of a fresh formation: Poor → Passable
- 2 games: → Excellent
- 3 games: → Formidable
- 4 games: → Outstanding

Each 10 minutes of play in a formation = 1 block of XP gained. Each game, **all formations lose 1 block** (1/3 of low levels Poor through Solid; 1/6 of Excellent/Formidable/Outstanding which are "double levels").

The starting formation also loses 1 block at game start before adding the gains. So a fresh game of Excellent-low formation that's never been played → end at Solid mid → not Excellent high.

**No XP is gained in extra time** (verified by Tasos).

---

## Individual Player Orders

Available orders per player:
- **Normal** (default)
- **Offensive / Defensive** (shifts contribution balance)
- **Towards Middle / Towards Wing** (redirects attack/defence sector)
- **Extra Defensive** (very strong defensive contribution, minimal attack)
- **Extra Forward** (very strong attack contribution, minimal defence)

**Tactical Assistant (TA) unlocks additional order slots**:
- No TA: 5 custom orders per match (subs + position changes)
- TA Level 1: 6 orders
- TA Level 2: 7 orders
- TA Level 5: 10 orders

Max 3 substitutions regardless of TA level. TA also expands the available range between offensive/defensive style of play (see `references/economy-detail.md`).

---

## Penalty Shootout

Only **goalkeeper skill** matters for the GK in shootouts (no form, stamina, etc.). Confirmed by HT-Tasos.

For the taker, Form, Stamina, XP, Specialty all factor in.

**Original Unwritten Manual taker formula** (now disputed):
```
Taker effectiveness = XP × 1.5 + SP × 0.7 + SCO × 0.3
                    +10% if Technical specialty
```

**Alternative formula** (IanMajor, justification in thread 17629498.732):
```
0.92 × ((((XP^4 / (XP^4 + 5^4)) × (SC^0.72 × (SP × (1 + 0.18×TECH))^0.28))^3.5)
       /
       (((XP^4 / (XP^4 + 5^4)) × (SC^0.72 × (SP × (1 + 0.18×TECH))^0.28))^3.5 + ((GK^0.68) / 0.90)^3.5))
```
(TECH = 1 if Technical, else 0.)

**Set-up rules:**
- Set order in advance via Penalty Takers form.
- If your SP taker is substituted, the **second player** in the Penalty Takers tab takes set pieces (not the substitute who came in).
- Worst penalty taker should be listed last (shootouts rarely exceed 10 kicks).

### Indirect Free Kick (IFK)
```
off IFK = 0.5 × m_Att + 0.3 × m_SP + 0.09 × SP_shooter
def IFK = 0.4 × m_Def + 0.3 × m_SP + 0.1 × SP_gk + 0.08 × GK_gk
```
Where `m_Att` / `m_Def` are outfield-player average attack/defence skills.

### Direct Free Kick (DFK)
- Only the **SP taker's SP and XP** are taken into account (no form/stamina).

---

## Sources
- LA-Alpa, "[HT] The Unwritten manual #15", thread 17665541 (sections 14 "Match: Tactics" and 15 "Substitutions" and 13 "Set Pieces and Special Events")
- nickarana (manager 884407) — Live data analysis on chance distribution, CA conversion, free kicks: HT thread 17493341
- HT-Tasos forum posts on tactic mechanics (CA, AIM/AOW, LS reviews)
- HO source for stamina/form factor formulas
