# Economy and arena

Core section of the hattrick skill, loaded on demand. Deeper tables live in the other `references/` files it points to.

## Weekly Income Sources
- **Match takings**: Attendance × ticket price (home games + mid-week matches)
- **Sponsor income**: weekly fixed amount, scales with league level and fan count. Formula: `((sm × number_of_fans / index) × 185 + 27200)` €/week, where `sm` = sponsor mood, `index` = division coefficient (Div I = 14.85, II = 21, III = 25.72, IV = 29.69, V = 33.19, VI = 36.37). Higher division → smaller index → bigger payout.
- Since Apr 2025, sponsor pay also includes a short-term performance component (last season's league position + cup round reached). Per HT-Tasos: division and fan club still count more than results — a higher-division team finishing last earns more from sponsors than a lower-division team finishing first.
- Promotion or relegation triggers a one-season **sponsor mood adjustment** (slightly more or less); fully resets after one season.
- **Player sales**: Transfer income (minus agent fee).
- **Transfer commissions**: 3% as last owner, 2% as original club when player is sold.
- **Fan membership fees**: Annual, based on fan club size (€30 / 6 eFt per member per season).
- **Rich-team fan reaction penalty (Rules 08)**: large cash reserves make fans *harder to please*. Rich teams' fan club mood reacts **more harshly to losses and less positively to wins** than poorer clubs. The effect scales with money on hand. For low-confidence/low-TS situations this argues for not hoarding cash, spend on training infrastructure (staff rotation, Specialist hires) or transfer market activity rather than letting it pile up.

## Weekly Expenses
- **Player wages**: Base 250€/player + skill/age premium. Specialists earn +10% wage bonus (phased in over 5 seasons starting season 83 / Oct 2022; +2% per season).
  - Set Pieces adds a small per-level bonus (~0.25%/level); Divine SP = +5%.
- **Staff wages**: 204 - 6,768 €/week per staff member, depending on level (1-5) and contract length (1-16 weeks). Longer contract = lower weekly rate. Per-level reference (16-week contract): L1 204, L2 408, L3 816, L4 1,632, L5 3,264 €/week. Per-level (1-week contract): L1 423, L2 846, L3 1,692, L4 3,384, L5 6,768. See `references/economy-detail.md` for the full 16×5 grid.
- **Staff severance**: 2× the savings vs the shortest contract you could have signed instead. Example: 13-week L3 contract, fire after 8 weeks - you paid 8 × 960 = 7,680 €; the equivalent 8-week contract would have cost 8 × 1,200 = 9,600 €; savings 1,920 €; severance 2 × 1,920 = **3,840 €**. Staff cannot be fired in the **first or last week** of their contract (only the middle weeks).
- **Staff slot limit**: maximum 4 staff at once. Up to 2 Assistant Coaches; all other types are limited to 1.
- **Arena maintenance**: Paid weekly regardless of home match.
- **Youth squad**: Running costs depend on size (None/Small/Medium/Large) or Scout wages.

## Key Financial Rules
- **-40,000 €**: spending freedom narrows (no expensive purchases that would push your post-purchase balance + 1 week wage below this).
- **Credit line: -100,000 €** (per rulebook). Beyond → bankruptcy warning. If still below -100k two weeks later → team lost. Teams with enough open bids on transfer-listed players to clear the threshold, or with Board Reserves, are protected from bankruptcy (but still pay interest).
- Interest on negative balance is heavy.
- **Financial Director**: increases the manager cash limit and the weekly amount the Board releases from Reserves. Level 1: cash limit 3,000,000 €, release 20,000/wk. Level 5: limit 5,000,000 €, release 200,000/wk. When cash exceeds the limit, 2% of total cash moves to Reserves per week. See `references/economy-detail.md` for the full ladder.
- Transfer agent fee: 5% (3% last owner + 2% original club from the remaining 95%)
- Fan happiness affects attendance income directly — win matches, meet expectations.
- **Board Reserves rule (Mar 2021, updated Nov 2021)**: When selling a "Gold Bar" player (GK Solid+, OR Solid leadership + Inadequate experience) who hasn't been a regular starter (60+ minutes once a week), part of the proceeds may be diverted to Board Reserves rather than cash. Recovery: 3 weeks of competitive play recovers 2 weeks of inactivity (friendlies-only takes 2× as long). **Homegrown players (own youth) and players bought in last 2 weeks are exempt** — all proceeds go to cash. You're warned before listing if Board intends to take part of the proceeds.

## Arena Management
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

## Fan & Sponsor Management
- Fans set expectations at season start (based on last season result).
- Sponsors also adjust based on team performance and league level.
- Win consistently → fan mood up → bigger crowds → more income.
- Newly promoted teams: fans expect little, easy to exceed expectations.
- Stagnant teams: expectations creep up each season.

## TS Effects from Buying / Selling Players
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

## Expense Reduction Priorities (if in trouble)
1. Fire Psychologists immediately (rarely useful)
2. Reduce assistant coaches to 2 (level 3 acceptable)
3. Keep squad at ~20 players max
4. Don't upgrade arena during financial difficulty
5. Avoid transfer market spending until stable
6. Fire staff after Thursday training, before weekend economy update (maximize their benefit)

## Advanced: 5-Staff Rotation Trick (Henribbo Method)
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
