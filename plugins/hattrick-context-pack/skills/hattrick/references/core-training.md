# Training and player development

Core section of the hattrick skill, loaded on demand. Deeper tables live in the other `references/` files it points to.

## Core Mechanics
- Training updates every **Thursday night** (since Dec 2024, the Monday skill-drop update has been merged into the weekly training update — drops happen alongside training).
- Only players who **played the correct position for 90 minutes** receive full training.
- Players fielded for <90 min receive proportional (minute-based) training. If a player has played multiple positions in a week, the engine picks the combination giving the best training (still capped at 90 min).
- Playing a friendly mid-week **doubles weekly training volume** — always arrange one.
- A player red-carded as soon as he enters the field gets **no training, no form, no XP** (he didn't complete a single full minute).
- Max 100% training intensity; stamina share cuts into skill training. Formula: `Skill Training = Intensity − (Intensity × Stamina%)`.
- New player purchases: matches played for previous teams **do not count** for training. Stamina is treated as if 0 minutes played that week (= 50% stamina training). Form does take previous matches into account.

## Training Types

Bracket convention from the official Hattrick rulebook: no brackets = full training effect, (single brackets) = small effect, ((double brackets)) = very small "osmosis" effect. The rulebook only gives one explicit 50% rate, **wingers receive half training in Playmaking, and wing backs receive half training in Crossing**. All other positions follow the bracket scale above.

| Training | Skill developed | Who gets it | Match formation tips |
|----------|-----------------|-------------|----------------------|
| Goalkeeping | Goalkeeping | Goalkeepers | Any |
| Defending | Defending | Defenders, ((all on field)) | 5-3-2, 5-4-1, 5-5-0 |
| Defensive positions | Defending | (GK, defenders, IMs, wingers), ((all on field)) | Any |
| Playmaking | Playmaking | IMs, wingers at 50%, ((all on field)) | 3-5-2, 4-5-1 |
| Crossing (Winger) | Winger | Wingers, wing backs at 50%, ((all on field)) | Any with 2 wingers |
| Wing attacks | Winger | Forwards and wingers, ((all on field)) | Any with 2 wingers |
| Scoring | Scoring | Forwards, ((all on field)) | 3-4-3, 4-3-3, 2-5-3 |
| Shooting | (Scoring) + ((Set pieces)) | (All on field) | Any |
| Short passes | Passing | IMs, wingers, forwards, ((all on field)) | Any |
| Through passes | Passing | Defenders, IMs, wingers, ((all on field)) | Any |
| Set Pieces | Set Pieces | All on field, +25% to nominated SP-taker and GK | Any (slow training) |
| Individual (youth only) | Position-relevant skill | (All on field) | Youth only |

A player gets full training only with 90 minutes played in a relevant position across the week (league + friendly combined). Less than 90 minutes = proportional training. Source: official Hattrick Rulebook, section 5 Training.

**Agglomeration penalties** (officially confirmed — since the new ME). All skills of the players in that compartment are reduced:
- 2 Central Defenders: **−3.6%** each, 3 CDs: **−10%** each
- 2 Inner Midfielders: **−6.5%** each, 3 IMs: **−17.5%** each
- 2 Forwards: **−5.5%** each, 3 FWs: **−13.5%** each

These are different from the older "4th gets no training" myth — 3 trainees on a central position is fine, but you pay a rating penalty.

## Trainee Profile (ideal buyer)
- Age ≤ 17y 35d (younger = more training time = more value)
- Main skill: inadequate to passable (room to grow)
- Has a **specialty** (Technical, Quick, Head, Powerful, Unpredictable, Support, Resilient/Regainer)
- Low secondary skills (low TSI = lower purchase price, more upside)
- Target: buy cheap at ~17.0, train to supernatural+, sell or keep

## Coach & Staff Impact
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

## Training Speed Factors
1. Age (younger = faster, but less impact than skill level since reform)
2. Current skill level (higher skill = slower training)
3. Coach quality
4. Training intensity %
5. Stamina % (higher stamina share = slower skill training)
6. Number of assistant coaches
7. Coach level does **not** affect stamina share efficiency — only age, stamina share % and minutes played determine stamina training (per HT-Bodin).

## Skill Level Scale (numerical)
1=Non-existent, 2=Disastrous, 3=Wretched, 4=Poor, 5=Weak, 6=Inadequate, 7=Passable, 8=Solid, 9=Excellent, 10=Formidable, 11=Outstanding, 12=Brilliant, 13=Magnificent, 14=World Class, 15=Supernatural, 16=Titanic, 17=Extra-Terrestrial, 18=Mythical, 19=Magical, 20=Utopian, 21=Divine (+1, +2... beyond)

Note: convention is non-existent=0, disastrous starts at 0.01–1.00, wretched 1.01–2.00, etc. So Solid spans **6.01–7.00** (not 7.00–7.99 as sometimes claimed).

## Skill Drops (aging)
- Since December 2016: **no skill drops due to high skills** (above titanic). All skill drops are now age-based only. The high-skill effect was converted into slower training speed at high levels.
- Higher skills still drop earlier and faster with age.
- Formula above Titanic: `Weekly drop = [(Skill − 14.85)²] / 1000`
- Training secondary skills at lower levels = more drop-resistant as player ages
- Multi-skilled players age more gracefully than mono-skilled ones
- Healing of a player **stops at the 41st birthday**.

## Multi-Skill Strategy
- Multi-skilled players have **lower wages** relative to their on-field contribution
- Key combos: Überwinger (Winger + Scoring + Passing), Playmaker with Passing, Defender with Passing for CA
- Since 2010: training speed halved at high levels → don't overshoot primary, add secondaries

## Tools
- **Hattrick Organizer (HO)**: most accurate CHPP tool. <https://github.com/akasolace/HO/releases/tag/stable>
- **Foxtrick** (browser extension): essential. <https://foxtrick-ng.github.io/>
- **HTMS calculator** (training potential to age 28): <https://www.fantamondi.it/HTMS/index.php>
- **TSI calculator**: <https://hattrick.chechesa.com/en>
- **Hattrick Radar** (skills with all modifiers): <https://hattrickradar.netsons.org/radar.php>

→ See `references/training-detail.md` for training speed tables and skill pop estimates
→ See `references/xp-form-loyalty.md` for full XP, Form, Loyalty contribution tables and formulas
→ See `references/match-engine-deep.md` for stamina decay tables and the stamina factor formula
