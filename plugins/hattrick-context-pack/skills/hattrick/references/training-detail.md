# Training Detail Reference

## Training Speed by Type (approximate, 17y, Solid→Excellent, 100% intensity, 15% stamina, Solid coach)

| Training Type | Weeks for 1 pop (approx) | Speed Category |
|--------------|--------------------------|----------------|
| Goalkeeping | 4–6 weeks | Medium |
| Defending | 4–6 weeks | Medium |
| Playmaking | 5–7 weeks | Medium |
| Winger | 5–7 weeks | Medium |
| Scoring | 5–8 weeks | Medium-Slow |
| Passing (Cross) | 3–5 weeks | Fast |
| Set Pieces | 8–14 weeks | Slow |

*These are rough ranges — actual speed depends on current skill level, age, sub-skills (hidden), coach level, and stamina %.*

## Training Update Timeline

- **Training update**: weekly, occurs at the **2nd daily update after the Cup/Friendly match**.
- Since **December 2024**, the Monday "skill drop" update has been **merged into the same weekly training update**: drops happen at the same moment as training pops. This means a player's net visible change post-training reflects both training gains and any age-based drops.
- **Bruises can occur during training** since the September 2024 update — only for healthy players who participated in matches that week, and never more serious than a bruise. Maximum 1 player can be injured during training per cycle.
- **Set Pieces training**: GK and the nominated SP-taker get a **+25%** bonus on training, but the bonus has a **hard cap of +1.0 level total** (per HT-Tasos).

## Age & Skill Level Effect
- Low skills (Weak–Passable): Train MUCH faster regardless of age
- High skills (Brilliant+): Train slower even at young age
- 17y vs 24y at same skill level: 17y is faster, but the gap is smaller than pre-reform
- A 24y Formidable player trains their secondary skills faster than a 17y player with the same secondary skill (because the secondary is still low)

## Coach Quality Impact (approximate)
- Excellent coach: Baseline (fastest)
- Solid coach: ~+0 weeks (effectively same as Excellent for most purposes)
- Passable coach: ~+1 week per pop
- Inadequate coach: ~+2 weeks per pop
- Non-existent coach: ~+3+ weeks per pop

**Rule of thumb**: One extra week per level below Solid (approximate, less accurate for fast training types).

## Assistant Coach Impact
- Each assistant coach improves training speed and player form
- Level 4 vs Level 3: Marginal difference in speed, large difference in cost
- New managers: 2x Level 3 assistants is cost-effective
- Experienced managers: 2x Level 4 for maximum speed

## Stamina Share vs Training Speed
The stamina % directly reduces effective training intensity:
- 10% stamina → 90% of intensity goes to skill training
- 15% stamina → 85% of intensity goes to skill training
- 20% stamina → 80% of intensity goes to skill training

Lower leagues can often get away with 10%, higher leagues need 15–20% for match stamina.

## Training Slots per Position
| Position | Primary (100%) | Secondary (50%) |
|----------|---------------|-----------------|
| GK | Goalkeeping | — |
| CD | Defending | — |
| WB | — | Defending or Winger (depending on training type) |
| IM | Playmaking | — |
| W | Winger or Cross Passing | — |
| FW | Scoring | — |

### Maximum trainees per training type
- **Goalkeeping**: 1 (only 1 GK position)
- **Defending**: 3 CDs (100%) + 2 WBs (50%) = up to 5 trainees
- **Playmaking**: 3 IMs (100%) + 2 Ws (50%) = up to 5 trainees
- **Winger**: 2 Ws (100%) + 2 WBs (50%) = up to 4 trainees
- **Scoring**: 3 FWs (100%) = up to 3 trainees
- **Cross Passing**: 2 Ws + 2 WBs (all ~100%) = up to 4 trainees

With a mid-week friendly, you can double these numbers by fielding different trainees.

## Stamina Reference
- Stamina affects all players mid-match (since match engine reform)
- Tired players lose performance linearly from ~65 minutes onward
- Higher stamina = maintain full performance longer
- Stamina trains passively based on stamina % setting
- Recommend at least 15% for competitive play; lower leagues can do 10%

## Sub-Skills (Hidden)
- Each visible skill level contains hidden sub-levels (often referred to as 0–99 or 0.0–0.99)
- Tools like Foxtrick can approximate sub-skill levels based on TSI and training history
- A player at "high Solid" is much closer to popping to Excellent than one at "low Solid"
- Low sub-skills when purchasing = more upside (and typically lower purchase price)

## Skill Drop Formula (above Titanic = level 16)
`Weekly drop = [(Skill - 14.85)²] / 1000`

Examples:
- Level 17 (ET): [(17-14.85)²]/1000 = [2.15²]/1000 = 4.62/1000 ≈ 0.0046/week
- Level 20 (Utopian): [(20-14.85)²]/1000 = [5.15²]/1000 = 26.5/1000 ≈ 0.027/week
- Divine (21): [(21-14.85)²]/1000 = [6.15²]/1000 = 37.8/1000 ≈ 0.038/week

*These are sub-skill drops per week. With sub-skills 0–1, a player at Divine could see a skill drop within ~26 weeks even with continued training if training doesn't keep pace.*

## Training Intensity Formula

```
ST = TI − (TI × SS%)
```

Where:
- `ST` = specific (skill) training received
- `TI` = training intensity (0–100%)
- `SS%` = stamina share (0–100%)

So at TI = 100%, SS = 15% → effective skill training = 85% of intensity. Stamina training happens at TI × SS = 15% of full effort.

### Training Intensity Trick (TS-boost)

If you reduce training intensity, your **Team Spirit will jump up** at the next update — useful before a critical match.

Mechanics:
- Lower TI **before the daily update that precedes the training update** (e.g. if training update is Friday morning, drop TI before Thursday morning).
- Restoring TI to 100% afterwards causes a **negative form effect** on the squad in the following weeks and a sharp TS drop.
- Today this management is also visible directly on the new training page.

**Calculator**: <https://ht.8ic.ro/trainingintensity>

## Weather (May 2024 onward — deterministic)

The forecast for tomorrow is **deterministic**: what's shown is what you get. Set lineup confidently the day before.

| Weather | Frequency |
|---------|----------:|
| Rain | 15.92% |
| Overcast | 34.44% |
| Partially cloudy | 34.30% |
| Sunny | 15.35% |

This affects specialty bonuses (Head in Rain, Powerful in Sunny, Technical in normal weather) and crowd attendance.

## Training & New Players

When you buy a player from another team:
- Matches he played for the previous team **do not count** for training.
- Stamina is calculated as if he had **0 minutes played** that week (= 50% stamina training automatically).
- **Form** does take previous matches into account.

## Youth Academy — Training Mechanics

**Primary + Secondary** trainings each week:
- Primary training: ~slightly less than senior training boost.
- Secondary training: 2/3 of primary boost.
- **Don't pick the same training twice**: 20% of combined effect is lost → total is only 1.33× primary, plus you waste a coach skill-revelation slot for that player.

**Individual training** (random boost to a random skill of the player):
- The **position the player spent the most time in during the match** determines the pool of possible skills picked.
- For each position, fixed probabilities determine which skill gets the random Individual boost — these probabilities are not affected by other parameters.
- Goalkeeping example: a player who played GK has fixed probabilities to receive Goalkeeping, Defending, or Set Pieces as Individual training.

**Optimal primary/secondary combinations**:
- **Goalkeeping + Individual** is the most efficient combo for GKs.
- For all other skills, see the table in `SKILL.md` § 4 "Valid Primary/Secondary Training Combinations".

**Youth pull rules**:
- 1/3 chance of getting a 15-year-old, 2/3 chance of a 16-year-old when calling new players.
- Youth injury updates: ~03:00 HT time daily.
- Youth friendly training effectiveness: **80% of a league game** (raised from 50% in November 2023).

**Promotion to senior squad (Rules 13)**:
- Player must be **17+ years old** AND have been in your youth team for **at least 1 season = 112 days**. A 17-year-old you just pulled cannot be promoted, you must hold him for 16 weeks first.
- Cannot promote if it leaves the youth squad with **fewer than 11 match-eligible players** (under-19s).
- Cannot promote if the senior squad already has **50 players**.
- Once a player turns **19**, he stops playing youth matches but stays in the squad as "ready to promote", he disappears from the field until you move him to the senior side.
- **Promotion cost**: €2 000 (400 eFt).

**Skill reveals from matches (Rules 13)**:
- The "44-minute reveal threshold" is the rulebook minimum, a youth player must have played **at least 44 minutes in a trainable position** during the match to be eligible for a primary-skill current-level reveal.
- A player below the 44-min threshold gets only the "very small effect" training and **no reveal**.
- **Primary training** reveals current level of one eligible player per match in the trained skill.
- **Secondary training** reveals maximum potential of one eligible player per match in the secondary-trained skill (if primary and secondary differ, otherwise no secondary reveal).
- If a revealed player already hit his cap in that skill this week, the coach reports "cannot continue training" instead of a numeric reveal.
- If fewer than 8 players finished the match on the pitch, **no reveals happen at all**.
- The coach additionally reports one of the **top-3 highest-potential players in a non-trained skill** each week (a separate, free reveal slot).

**Costs (Rules 13)**:
- One-time **registration fee**: €5 000 (1 000 eFt) when opening a youth team.
- Weekly base: €10 000 (2 000 eFt) for 1 scout.
- Each additional scout: **€5 000 (1 000 eFt) per week** plus a **€5 000 (1 000 eFt) signing bonus** in the hire week. Max 3 scouts, never fewer than 1.

**Closing the youth team (Rules 13)**:
- Allowed only between youth seasons OR if the youth team is not in any youth league.
- Minimum operating period: **6 weeks**.
- "Restart youth team" (full wipe of squad + scouts, keeps league slot) is irreversible and limited to **once per 3 seasons (48 weeks)**.
- Restart button only appears if the team has been inactive ≥3 weeks with no scout calls, OR no scouts called this week AND fewer than 9 eligible (under-19) players in the squad.

## Sources
- LA-Alpa, "[HT] The Unwritten manual #15", Hattrick Global English Forum thread 17665541 (sections 6 "Training" and 18 "Youth players")
- HT-Tasos editorials (Dec 2024 training update consolidation; Sept 2024 injury system; Nov 2023 youth update)
