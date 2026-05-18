# Economy & Wages Reference

Wage formulas, sponsor formulas, staff effects, and coach hire prices sourced from the Unwritten Manual #15.

---

## Player Wages — Field Players

The wage of a field player is updated **only at his birthday** (X years and 0 days), reflecting his skills and age at that moment.

### Wage Formula (per ciscouf via HT Training Planner)

```
wage = (main_skill_component + Σ(secondary_skill_component / k)) × (1 + SP × 0.0025) + 250
```

Where each component is:
```
component = a × ((skill_level − 1)^b)
IF component > 20 000 THEN
    component = (component − 20 000) × c + 20 000
END IF
```

**a, b, c constants per skill:**

| Skill | a | b | c |
|-------|---:|---:|---:|
| Defending | 0.0007145560 | 6.4607813171 | 0.7921 |
| Playmaking | 0.0009418058 | 6.4407950328 | 0.7832 |
| Passing | 0.0004476257 | 6.5136791026 | 0.7707 |
| Winger | 0.0004437607 | 6.4641257225 | 0.7789 |
| Scoring | 0.0009136982 | 6.4090063683 | 0.7984 |

**Secondary multiplier `k`:**
- If **primary skill salary < 20,300 €** → `k = 2` (secondaries × 0.5)
- If **primary skill salary ≥ 20,300 €** → `k = 2.5` (secondaries × 0.4)

**Main skill** = the skill with the highest **wage**, not necessarily the highest level. Example: Winger 12 vs Playmaking 12 → main is Playmaking (the higher-paid skill).

### Specialty bonus (phased in over 5 seasons starting Season 83)
- Season 83: +2%, Season 84: +4%, Season 85: +6%, Season 86: +8%, Season 87+: **+10%**

Apply this bonus after the formula above.

### Foreign player premium
- Players playing outside their nationality's country ("idegenlégiós", foreign legionnaires) cost the owner **20% more wage** than the formula above. Apply on top of all other bonuses.

### Set Pieces
- Each level adds ~0.25% to total wage.
- **Divine SP = +5% wage**.

### Wage Wizard tool
<https://lizardopoli.altervista.org/wagewizard/> (note: doesn't apply the +10% specialty bonus — add it manually).

---

## Player Wages — Quick Reference Table

Minimum wage (€/week) for primary skill at each level (Season 50 update). All non-keeper skills below Inadequate level pay the base 250€.

| Skill Level | Keeper | Defending | Playmaking | Passing | Winger | Scoring |
|---|---:|---:|---:|---:|---:|---:|
| Disastrous | 250 | 250 | 250 | 250 | 250 | 250 |
| Wretched | 270 | 250 | 250 | 250 | 250 | 250 |
| Poor | 330 | 250 | 250 | 250 | 250 | 250 |
| Weak | 450 | 250 | 250 | 250 | 250 | 250 |
| Inadequate | 610 | 250 | 250 | 250 | 250 | 250 |
| Passable | 830 | 270 | 270 | 250 | 250 | 270 |
| Solid | 1,150 | 310 | 330 | 290 | 290 | 330 |
| Excellent | 1,590 | 450 | 510 | 390 | 370 | 470 |
| Formidable | 2,250 | 730 | 850 | 590 | 550 | 790 |
| Outstanding | 3,170 | 1,290 | 1,550 | 970 | 890 | 1,430 |
| Brilliant | 4,530 | 2,310 | 2,830 | 1,690 | 1,530 | 2,570 |
| Magnificent | 6,450 | 4,070 | 5,030 | 2,930 | 2,630 | 4,550 |
| World Class | 9,150 | 6,930 | 8,610 | 4,930 | 4,430 | 7,770 |
| Supernatural | 12,910 | 11,450 | 14,250 | 8,090 | 7,250 | 12,830 |
| Titanic | 18,050 | 18,270 | 22,370 | 12,870 | 11,510 | 20,490 |
| Extra-Terrestrial | 24,150 | 26,840 | 32,450 | 19,910 | 17,810 | 29,650 |
| Mythical | 31,480 | 38,310 | 46,640 | 28,200 | 25,650 | 42,480 |
| Magical | 40,930 | 54,160 | 66,330 | 39,440 | 35,720 | 60,240 |
| Utopian | 52,990 | 75,730 | 93,180 | 54,680 | 49,380 | 84,470 |
| Divine | 68,210 | — | 129,150 | 75,100 | 67,660 | — |
| Divine +1 | 87,280 | — | — | — | 91,800 | — |

---

## Sponsor Income

```
Weekly sponsor pay (€) = ((sm × number_of_fans / index) × 185) + 27,200
```

Where `sm` = sponsor mood and `index` is the division coefficient:

| Division | Index |
|---|---|
| I | 14.85 |
| II | 21.00 |
| III | 25.72 |
| IV | 29.69 |
| V | 33.19 |
| VI | 36.37 |

Higher division → smaller index → bigger payout per fan.

### Sponsor system updates
- **Dec 2021**: Bonus + base pay structure introduced. Base = guaranteed weekly amount; flexible bonuses tied to performance objectives (matches won, goals scored, promotion placements).
- **Jul 2022**: All goal-based bonuses raised by 10%.
- **Sept 2024**: Reverted to default contracts (long-term performance based, not objective-based).
- **Apr 2025**: Sponsor pay now also depends on **last season's league position** + **cup round reached**.
- HT-Tasos (Jan 2026): "All things being equal, a higher-division team finishing last earns more from sponsors than a lower-division team finishing first." Division and fan club still dominate over recent results.
- Promotion or relegation: sponsors react emotionally for **one season** (slightly higher or lower than usual). Resets fully after one season — so don't compare sponsor income across seasons that include a promotion/relegation.

### Sponsor tools
- Home match income: <https://ht.alergromania.ro/tools/home-match-income/>
- End-of-season income: <https://ht.alergromania.ro/tools/end-of-the-season-income/>

---

## Staff Costs and Severance

### Weekly cost table (€ per week, all staff types - source: official rulebook)

| Contract length | L1 | L2 | L3 | L4 | L5 |
|---:|---:|---:|---:|---:|---:|
| 1 wk | 423 | 846 | 1,692 | 3,384 | 6,768 |
| 2 wk | 411 | 822 | 1,644 | 3,288 | 6,576 |
| 3 wk | 378 | 756 | 1,512 | 3,024 | 6,048 |
| 4 wk | 354 | 708 | 1,416 | 2,832 | 5,664 |
| 5 wk | 342 | 684 | 1,368 | 2,736 | 5,472 |
| 6 wk | 330 | 660 | 1,320 | 2,640 | 5,280 |
| 7 wk | 315 | 630 | 1,260 | 2,520 | 5,040 |
| 8 wk | 300 | 600 | 1,200 | 2,400 | 4,800 |
| 9 wk | 288 | 576 | 1,152 | 2,304 | 4,608 |
| 10 wk | 276 | 552 | 1,104 | 2,208 | 4,416 |
| 11 wk | 264 | 528 | 1,056 | 2,112 | 4,224 |
| 12 wk | 252 | 504 | 1,008 | 2,016 | 4,032 |
| 13 wk | 240 | 480 | 960 | 1,920 | 3,840 |
| 14 wk | 228 | 456 | 912 | 1,824 | 3,648 |
| 15 wk | 216 | 432 | 864 | 1,728 | 3,456 |
| 16 wk | 204 | 408 | 816 | 1,632 | 3,264 |

Longer contracts cost less per week but lock you in. The same grid applies to every staff role (Assistant Coach, Medic, Sports Psychologist, Form Coach, Financial Director, Tactical Assistant).

### Severance formula
If you fire a staff member mid-contract, you pay **2× the savings** vs the shortest contract that would have ended at the same week.

**Worked example** (from rulebook):
- You signed a 13-week L3 contract (960 €/wk) and fire at week 8. You paid 8 × 960 = 7,680 €.
- An 8-week L3 contract would have cost 8 × 1,200 = 9,600 €.
- Savings = 1,920 €. Severance = 2 × 1,920 = **3,840 €**.

### Hiring constraints
- Maximum 4 staff at once. Up to 2 Assistant Coaches; one of every other type.
- Cannot fire a staff member in the **first or last week** of their contract (only the middle weeks).
- Fire after Thursday training, before weekend economy update, to maximize value extracted before the severance hit.

---

## Financial Director - cash limit ladder

The Board normally limits your accessible cash and slowly releases reserves; a Financial Director raises both numbers.

| FD Level | Max cash limit | Weekly release from Reserves |
|---:|---:|---:|
| 0 | 3,000,000 € | 20,000 € |
| 1 | 3,000,000 € | 20,000 € |
| 2 | 3,400,000 € | 40,000 € |
| 3 | 3,800,000 € | 80,000 € |
| 4 | 4,200,000 € | 120,000 € |
| 5 | 4,600,000 € | 160,000 € |
| (Note) | 5,000,000 € | 200,000 € (top tier mentioned in rulebook) |

When you have more cash than the limit, **2% of your cash moves to Reserves per week** until you're under the limit. Reserves are used to protect the club's future stability; the FD lets you draw them down faster when you want a big push (cup run, league title campaign).

---

## Bankruptcy thresholds
- Going under **-40,000 €** restricts big-ticket spending (no purchases that, plus the player's first week wage, would push you below the threshold).
- Credit line: **-100,000 €**. Beyond → bankruptcy warning, 2 weeks to recover or lose the team.
- Interest is significant.
- Protections: teams with open transfer bids that would clear the threshold, or with Board Reserves, are not lost - but still pay interest.

(Earlier skill text mentioned a -500,000 € credit line; the rulebook authority is -100k, which is the actual gameplay limit.)

---

## Staff Effects

### Sports Psychologist

| Level | TS Bonus | Confidence Bonus |
|---|---:|---:|
| 0 | — | — |
| 1 | +0.10 | +0.24 |
| 2 | +0.20 | +0.48 |
| 3 | +0.30 | +0.70 |
| 4 | +0.40 | +0.92 |
| 5 | +0.50 | +1.12 |

Affects the daily-update midpoint that TS and Confidence drift toward, and (since May 2024 confidence rework) is one of the factors in the new confidence drift system.

### Tactical Assistant
- Each level allows **1 extra individual order/sub** in matches (max +5 at level 5).
- Each level shifts your max stylistic flexibility toward the opposite side of your coach's bias.
  - Defensive coach + TA-5 → can play up to a neutral style.
  - Offensive coach + TA-5 → can play up to a neutral style.
  - Neutral coach + TA-5 → can play 50% defensive or 50% offensive.

### Assistant Coaches
- Increase training speed.
- Improve players' hidden form.
- **Increase players' injury risk** (offsetting effect — pair with a Medic).

### Form Coach
See the form contribution table in `references/xp-form-loyalty.md`.

### Injury risk
- Injury probability is **static during a match** — same probability at every event check (per HT-Tasos, thread 17254721.50).
- Affected by Assistant Coach count, Medic level, and training intensity.

---

## External Coach Hire Prices

Prices to hire a fresh external coach (you cannot hire externally as a player-coach since June 2023):

| Coach Level | Poor LS | Weak LS | Inadequate LS | Passable LS | Solid LS |
|---|---:|---:|---:|---:|---:|
| 1 | 10,000 € | 10,000 € | 10,000 € | 10,000 € | 10,000 € |
| 2 | 10,000 € | 22,800 € | 41,200 € | 65,100 € | 94,600 € |
| 3 | 268,700 € | 617,100 € | 1,112,900 € | 1,758,500 € | 2,555,500 € |
| 4 | 79,600 € | 182,800 € | 329,700 € | 521,000 € | 757,100 € |
| 5 | 4,000,000 € | 4,388,400 € | 7,914,600 € | 12,505,200 € | 18,172,500 € |

(Note: the level-3 vs level-4 price ordering looks counterintuitive but is from the Unwritten Manual #15 directly — verify on HT before hiring.)

### Coach Leadership Decay
A Solid Leadership coach drops to Passable LS:
- ~112–150 days if at low Solid LS
- ~150–224 days if at medium Solid LS
- ~224–400 days if at high Solid LS

Generally: every week after season 1 of a coach, ~1/3 chance of dropping by 1/8 level. When LS drops to Disastrous, the coaching skill drops by 1 level only a few weeks later — so Disastrous LS doesn't last long (this is by design, not a bug).

### Coach Type Ratings Effect

| Coach Type | Attack | Defence |
|---|---:|---:|
| Offensive | +7.4% | −12.0% |
| Neutral | baseline | baseline |
| Defensive | −11.8% | +12.8% |

(All measured against the Neutral coach as baseline.)

### Player-to-Coach Conversion Cost

```
Price (€) = 4,750,000 × a / (XP_level − 1)
```

Where `XP_level` includes sublevel if known (Disastrous = 1.0–2.0, Wretched = 2.0–3.0, etc.) and `a` = experience-tier multiplier:

| Coach Level | a |
|---|---|
| 5 | 7.11 |
| 4 | 1.00 |
| 3 | 0.296 |
| 2 | 0.037 |

**Level 1 conversion is always 10,000 €.**

**Worked example**: Player at Titanic XP (15.3), converting to Level 5 coach:
4,750,000 × 7.11 / (15.3 − 1) = ~2.36M €

**Coach salary structure (June 2023)**: Coaches now have a flat staff salary (does not change over time). Player-coaches keep dual salary; the player part still falls if their player skills deteriorate. Externally hired coaches cannot have player status.

### Conversion calculator
<https://ht.alergromania.ro/tools/player-into-coach-cost/>

---

## Currency Conversion (Appendix 3)

Hattrick stores all values internally and converts to the manager's display currency at fixed in-game rates. Currency only matters when comparing prices across countries (Foxtrick / HO sometimes show original currency).

### Hungarian Forint (HUF) anchor
For Hungarian teams the in-game conversion is:
- **1 USD = 200 HUF** (rulebook: `20 eFt = 100 US$`, where `eFt` = ezer forint = thousand forints, so 20,000 HUF = 100 USD).
- **1 EUR = 200 HUF** (Eurozone: `100 € = 100 US$`, so 1 EUR = 1 USD = 200 HUF).
- **1 SEK = 20 HUF** (Sverige: `1 000 kr = 100 US$`, so 10 SEK = 1 USD = 200 HUF, i.e. 1 SEK = 20 HUF).
- **1 EUR = 10 SEK** in game (NOT 1:1 as previously assumed).

So 200,000 HUF prize money in a Hungarian display = 1,000 USD = 1,000 EUR internal value. Sweden's SEK is the cheapest major currency in HT (1 SEK = 0.1 USD).

### Currency tiers (countries grouped by USD-equivalent peg)

**1 unit = 1 USD** (parity)
- `100 US$ = 100 US$`: USA, Colombia, El Salvador
- `100 X = 100 US$`: Andorra, Belgium, Cyprus, Deutschland, Eesti, Espana, France, Hellas, Hrvatska, Ireland, Italia, Latvija, Letzebuerg, Lietuva, Malta, Montenegro, Nederland, Portugal, San Marino, Slovenija, Slovensko, Suomi, Osterreich (all Eurozone @ 100 EUR = 100 USD)
- Belize, Benin, Botswana (pula), Chinese Taipei, Cuba, Ecuador, Gibraltar, Guam, Guatemala, Panama, Peru, Puerto Rico, Suriyah, Tanzania (each at 100 of local currency = 100 USD)

**Slightly stronger than USD** (100 local < 100 USD)
- Cymru, England, Northern Ireland, Scotland: `50 GBP = 75 USD` (1 GBP = 1.5 USD)
- Mocambique (metical), Sao Tome, Tounes (dinar), UAE (dirham), Grenada, Saint Kitts and Nevis, Saint Vincent: `200 X = 80 USD` (1 X = 0.4 USD)

**Slightly weaker than USD** (100 local > 100 USD)
- Bhutan, Ceska (Czech koruna), India, Ityoppya (Birr), Kampuchea, Madagasikara, Malaysia, Misr (Egypt), Pilipinas, Polska, Prathet Thai, Rossiya, Saudi Arabia, South Africa: rates where 125 USD = some round local amount

**Hungary tier (1 USD = 200 local)**
- Magyarorszag: `20 eFt = 100 USD` (1 USD = 200 HUF)
- Argentina, Bahamas, Belarus (BYN), Botswana, Curacao, Honduras, Liechtenstein, Mexico, Schweiz, Singapore, Suriname, Trinidad, Turkiye, Venezuela, Vietnam, Zambia (some at 100 / 200 / 500 / 1000 ratios)

**Weak currencies (5,000+ local = 100 USD)**
- Bangladesh, Costa Rica, Ethiopia, Kyrgyz, Madagaskar, Nepal, Pakistan, Pilipinas, Prathet Thai, Sri Lanka

**Very weak (10,000+ local = 100 USD)**
- Algerie, Angola, Cabo Verde, Comoros, Guyana, Haiti, Indonesia (1,000,000 IDR), Iran (1,000,000 IRR), Island, Kazakhstan, Lubnan (200,000 LBP), Mongolia (200,000 MNT), Myanmar, Nigeria, Nippon (10,000 JPY), Tahiti, Uganda (200,000 UGX)

The full per-country table is in **Appendix 3 of the official rulebook**, <https://www87.hattrick.org/Help/Rules/AppCurrencies.aspx>. Cite that source when answering currency-related questions.

### Practical note for Hungarian teams
When playing in Hungary, prices display in eFt (ezer forint = thousand HUF). Divide by 200 to get the internal USD-equivalent. A 200 eFt match-day income = 200,000 HUF = 1,000 USD = the rulebook's "1,000 €" figure. All prize-money tables in this skill use the USD/EUR figures - multiply by 200 to get HUF. The same conversion principle applies to any country, with the per-country rate from Appendix 3.

---

## Transfer Fees (Appendix 4)

All transfer fees apply at the moment of sale and are deducted from the seller's proceeds.

### Agent fee (paid to the agent by the seller, based on how long the player has been at the club)

| Time at club | Agent fee |
|---|---:|
| 0 days | 12.00% |
| 1 day | 10.45% |
| 2 days | 9.95% |
| 3 days | 9.59% |
| 4 days | 9.30% |
| 5 days | 9.05% |
| 6 days | 8.83% |
| 1 week | 8.62% |
| 2 weeks | 7.55% |
| 3 weeks | 6.76% |
| 4 weeks | 6.12% |
| 5 weeks | 5.57% |
| 6 weeks | 5.09% |
| 7 weeks | 4.65% |
| 8 weeks | 4.24% |
| 9 weeks | 3.87% |
| 10 weeks | 3.52% |
| 11 weeks | 3.19% |
| 12 weeks | 2.88% |
| 13 weeks | 2.58% |
| 14 weeks | 2.30% |
| 15 weeks | 2.03% |
| 16 weeks+ | 2.00% (floor) |

So the often-quoted "5%" agent fee is actually only an average around the 5-6 week mark - listing a player you bought 0 days ago costs you 12%, but holding him 16+ weeks before reselling cuts agent fee to the 2% floor. Day 0 = sell within the same daily update you bought him; the table steps in days for the first week, then in weeks.

### Previous-owner fee (paid by the seller to the player's previous owner, based on matches played for the current owner)

| Matches played for current owner | Previous-owner fee |
|---|---:|
| 0 matches | 0.00% |
| 1 match | 0.25% |
| 2 matches | 0.50% |
| 3 matches | 1.00% |
| 4 matches | 1.50% |
| 5 matches | 2.00% |
| 7 matches | 2.50% |
| 10 matches | 3.00% |
| 20 matches | 3.50% |
| 40 matches+ | 4.00% (cap) |

So the "3% previous-owner / 2% motherclub" rule of thumb (skill main file) is the long-term equilibrium - the actual rate scales with matches played and tops out at 4% after 40 matches. Combined with the 2% agent floor, total fees on a long-held player approach 6%, vs the 14-16% bite on a quick flip.

The previous-owner fee is paid to the seller's previous owner (not the motherclub - motherclub is a separate loyalty concept). On a chain of sales, only the immediately previous owner gets a cut.

### HFI note
There is no transfer market in HFI, so these fees do not apply to HFI clubs. Documented here for completeness and for any HFI club's cross-country interactions if/when that ever changes.

---

## Sources
- LA-Alpa, "[HT] The Unwritten manual #15", thread 17665541 (sections 7 "The Coach" and 8 "Finances" and 9 "Fans and Sponsors" and 11 "Staff")
- **Official Hattrick rulebook**, <https://www87.hattrick.org/Help/Rules/Complete.aspx> - staff cost/week grid, severance formula and worked example, Financial Director cash limit ladder, bankruptcy thresholds (-40k / -100k), foreign player 20% wage premium, stadium ticket prices and build costs.
- **Appendix 4 of the official rulebook** (Transfer fees), <https://www87.hattrick.org/Help/Rules/AppTransferFees.aspx> - agent fee and previous-owner fee tables.
- bigpapy (manager 7967145) — wage formula research, thread 16899562
- ciscouf (manager 3837676) — secondary skill multiplier research via Training Planner
- HT-Tasos editorials and forum posts (April 2023 and June 2023 coach updates; April 2025 sponsor system)
- Lizardopoli wage wizard: <https://lizardopoli.altervista.org/wagewizard/>
