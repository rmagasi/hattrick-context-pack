# XP, Form, Loyalty, TSI & Stamina Reference

Player attribute formulas and contribution tables sourced from the Unwritten Manual #15.

---

## TSI (Total Skill Index)

TSI is a measure of total skill output. It increases with training and varies with form.

**TSI for outfield players:**
```
TSI = ( 1.03 × Def³ + 1.03 × PM³ + 1.03 × Sc³ + 1.0 × Ps³ + 0.84 × Wg³ )² × St^0.5 × Fm^0.5 / 1000
```

**TSI for goalkeepers:**
```
TSI_gk = 3 × Gk^3.359 × Fm^0.5
```

Skill values use the convention where Solid = 6.01–7.00 (so "Solid" = 6.0+ in the formula).

**TSI calculator**: <https://hattrick.chechesa.com/en>

---

## Stamina Factor

```
Stamina factor = ((Stamina + 6.5) / 14)^0.6
```

(From HO. Used to apply stamina to skill ratings.)

### Stamina decay during a match — Normal play (no Pressing)

| Stamina | Avg over 90' | At 45' | At 90' | At 120' |
|--------:|-------------:|-------:|-------:|--------:|
| 1.7 (min) | 65.2% | 58.9% | 26.5% | 10% |
| 2.0 | 67.1% | 60.8% | 29.4% | 10% |
| 2.5 | 70.2% | 64.0% | 34.4% | 10% |
| 3.0 | 73.3% | 67.1% | 39.3% | 10% |
| 3.5 | 76.3% | 70.3% | 44.2% | 15.6% |
| 4.0 | 79.3% | 73.5% | 49.1% | 21.8% |
| 4.5 | 82.3% | 76.7% | 54.1% | 28.1% |
| 5.0 | 85.2% | 79.9% | 59.0% | 34.4% |
| 5.5 | 88.0% | 83.1% | 63.9% | 40.6% |
| 6.0 | 90.7% | 86.3% | 68.8% | 46.9% |
| 6.5 | 93.1% | 89.4% | 73.7% | 53.2% |
| 7.0 | 95.3% | 92.6% | 78.7% | 59.5% |
| 7.5 | 97.1% | 95.8% | 83.6% | 65.7% |
| 8.0 | 98.5% | 99.0% | 88.5% | 72.0% |
| 8.5 | 99.7% | 100% | 95.6% | 79.1% |
| 9.0 | 100% | 100% | 100% | 86.3% |
| 9.4 (max) | 100% | 100% | 100% | 92.0% |

### Stamina decay during a match — Pressing

| Stamina | At 45' | At 90' | At 120' |
|--------:|-------:|-------:|--------:|
| 1.7 | 54.3% | 16.8% | 10.0% |
| 2.0 | 56.3% | 20.0% | 10.0% |
| 2.5 | 59.7% | 25.2% | 10.0% |
| 3.0 | 63.0% | 30.5% | 10.0% |
| 3.5 | 66.3% | 35.7% | 10.0% |
| 4.0 | 69.7% | 41.0% | 10.3% |
| 4.5 | 73.0% | 46.2% | 17.1% |
| 5.0 | 76.4% | 51.5% | 23.8% |
| 5.5 | 79.7% | 56.7% | 30.5% |
| 6.0 | 83.0% | 62.0% | 37.3% |
| 6.5 | 86.4% | 67.2% | 44.0% |
| 7.0 | 89.7% | 72.5% | 50.7% |
| 7.5 | 93.1% | 77.7% | 57.5% |
| 8.0 | 96.4% | 83.0% | 64.2% |
| 8.5 | 100% | 90.1% | 71.3% |
| 9.0 | 100% | 97.3% | 78.5% |
| 9.4 | 100% | 100% | 84.2% |

(Tables by Schum, manager 5176908.)

**Stamina tools:**
- <https://lizardopoli.altervista.org/staminia/>
- <https://hattrickportal.online/Utils/PlayerTraining.aspx>

---

## Experience (XP)

XP is not applied directly to skills, but to **ratings**. Approximate rating contributions from XP (per WesselV1 study):
- Side defence + midfield: `0.36 × (1 − 0.85^XP_level)`
- Central defence + side attack: `0.36 × (7/8) × (1 − 0.85^XP_level)`
- Central attack: `0.36 × (4/5) × (1 − 0.85^XP_level)`

XP affects each skill's contribution as a chain — anything depending on the skill (tactic level, SE probability) is affected.

### Older per-skill XP contribution table (Unwritten Manual)

```
XP influence = log(experience) × 4/3
```

| XP Level | Contribution |
|---|---|
| Disastrous | +0.00 |
| Wretched | +0.40 |
| Poor | +0.64 |
| Weak | +0.80 |
| Inadequate | +0.93 |
| Passable | +1.04 |
| Solid | +1.13 |
| Excellent | +1.20 |
| Formidable | +1.27 |
| Outstanding | +1.33 |
| Brilliant | +1.39 |
| Magnificent | +1.44 |
| World Class | +1.49 |
| Supernatural | +1.53 |
| Titanic | +1.57 |
| Extra-Terrestrial | +1.61 |
| Mythical | +1.64 |
| Magical | +1.67 |
| Utopian | +1.71 |
| Divine | +1.73 |
| Divine +1 | +1.7629 |
| Divine +2 | +1.7898 |
| Divine +3 | +1.8156 |
| Divine +4 | +1.8402 |
| Divine +5 | +1.8639 |
| Divine +10 | +1.9694 |
| Divine +15 | +2.0587 |
| Divine +20 | +2.1360 |

### XP Mechanics

- **1 XP level = 100 XP points**
- A player can not gain more than **90 minutes of experience** per match.
- A player who plays <1 full minute (e.g. red-carded immediately on entry) gets **no training, form, or XP**.
- XP has a bigger impact on **penalty shootouts** than on regular penalty kicks or set pieces during play.

### XP points per match type (per rulebook, current)
| Match type | XP points |
|---|---:|
| League | 3.5 |
| Play-off | 7 |
| National / Divisional Cup | 7 |
| Secondary (League/Consolation) Cup | 1.75 |
| Friendly | 0.35 |
| International friendly | 0.7 |
| Hattrick Masters | 17.5 |
| Youth league | 3.5 |
| Youth friendly | 0.35 |
| World Cup group/round | 28 |
| World Cup semi/final | 56 |
| World Cup wildcard play-off | 14 |
| Continental Cup group | 14 |
| Continental Cup QF/SF/Final | 21 |
| Nations Cup group | 7 |
| Nations Cup knockout | 14 |
| NT friendly | 3.5 |
| Qualification Cup | 7 |
| (Legacy) Old WC match | 35 |
| (Legacy) Old WC final | 70 |
| (Legacy) Old NT friendly | 7 |

---

## Form

Form acts as a multiplier on a player's effective skills.

### Form → Performance % (effective skill output)

| Form | Performance |
|------|------------:|
| Excellent | 100% |
| Solid | 96.7% |
| Passable | 89.7% |
| Inadequate | 82% |
| Weak | 73.2% |
| Poor | 62.9% |
| Wretched | 50% |
| Disastrous | 30.5% |

**Form factor** (from HO):
```
Form factor = ((Form − 0.5) / 7)^0.45
```

### Improving Form (background form drives the visible value)

- Make every player play once per week (friendlies count).
- Run high training intensity.
- Hire a Form Coach.
- Have a Coach + Assistant Coaches with high Leadership.

### Form Coach effect on player form

| Coach Level | Form contribution |
|---|---|
| Level 5 | +0.6 |
| Level 4 | +0.48 |
| Level 3 | +0.35 |
| Level 2 | +0.21 |
| Level 1 | 0 |

(From HT-Tasos, Jan 2024 update — these are now visible in-game on the Staff page.)

---

## Loyalty

Years with the club add a flat skill-rating bonus per skill, scaled to a 0–1 contribution range.

| Loyalty Level | Min Contrib | Max Contrib |
|---|---:|---:|
| Disastrous | +0 | +0.0525 |
| Wretched | +0.0526 | +0.1052 |
| Poor | +0.1053 | +0.1578 |
| Weak | +0.1579 | +0.2104 |
| Inadequate | +0.2105 | +0.2631 |
| Passable | +0.2632 | +0.3157 |
| Solid | +0.3158 | +0.3683 |
| Excellent | +0.3684 | +0.4210 |
| Formidable | +0.4211 | +0.4736 |
| Outstanding | +0.4737 | +0.5262 |
| Brilliant | +0.5263 | +0.5788 |
| Magnificent | +0.5789 | +0.6315 |
| World Class | +0.6316 | +0.6841 |
| Supernatural | +0.6842 | +0.7367 |
| Titanic | +0.7368 | +0.7894 |
| Extra-Terrestrial | +0.7895 | +0.8420 |
| Mythical | +0.8421 | +0.8946 |
| Magical | +0.8947 | +0.9473 |
| Utopian | +0.9474 | +0.9999 |
| Divine | +1 | +1 |

### Loyalty rules
- If you transfer-list a player by mistake and buy him back within 3 days, he keeps loyalty — he didn't actually leave.
- If you re-buy a former YA player, you do **not** get the motherclub loyalty bonus back.

### Per-rulebook bonus values (current)
- **Loyalty bonus at Divine**: **+1 skill level** on every skill except Stamina.
- **Motherclub (nevelőegyesület) bonus**: **+0.5 levels** on every skill except Stamina, for players who have spent their whole career at the club (own youth pulls). Shown by a heart icon on the player card.
- Both bonuses stack - own youth pulls who reach Divine loyalty get **+1.5 levels** across the board.
- Loyalty grows fast at first and slows over time: half of max in ~12 weeks, full max in **3 seasons**.
- Selling a player wipes his loyalty; re-buying him later resets it to 0.

(Detailed loyalty-vs-days table from Danfisico (manager 3232936): HT thread 15305653.2.)

---

## Injuries

### Bruised player average performance

A bruised player performs at ~95% of normal stars (data from 7,155 cases):

| Stars (normal) | Bruised performance |
|---:|---:|
| 0.5 | 97.17% |
| 1 | 95.77% |
| 1.5 | 94.41% |
| 2 | 92.60% |
| 2.5 | 91.85% |
| 3 | 93.92% |
| 3.5–4.5 | 94.75% |
| **Total** | **95.00%** |

Performance ≈ % of health. Bruised health = [0.9, 1.0). Average ≈ 0.95.

### Injury rules (post Sept 2024 update)
- Injuries are localized to body parts. Re-fielding a bruised player risks aggravating that exact spot — the new injury is more likely to be in the same place and slightly more serious.
- **No difference in injury length** based on type of injury (card vs random) — confirmed by HT-Tasos.
- Healing **stops at the 41st birthday**.
- Sept 2024 update: shifted distribution from long-term to short-term injuries; reduced risk of multi-injury matches; **minor risk of training injury** (max bruise) introduced for healthy players who participated in matches.

### Fouls and cards
- Aggressiveness × Honesty governs foul/cheat/card probabilities.
- 25% injury rate on yellow card that resulted from a foul.
- Cards in cup match → miss next league match (and other competitive cards apply per cup type).

---

## Sources
- LA-Alpa, "[HT] The Unwritten manual #15", Hattrick Global English Forum thread 17665541 (sections 2 "Skills" and 3 "Other Attributes")
- **Official Hattrick rulebook**, <https://www.hattrick.org/Help/Rules/Complete.aspx> - authoritative XP table per match type, current loyalty bonus values (+1 at Divine, +0.5 motherclub).
- Schum (manager 5176908) — stamina decay tables
- WesselV1 (manager 11234483) — XP-to-rating contribution formulas (HT thread 17371940.86)
- HT-Tasos editorials (Jan 2024 update on coach form contribution; Sept 2024 update on injury system)
- Murzim (manager 8649722) — XP × skill calculator: <http://www.evdaimon.com/hattrick/xp_skill2.php>
