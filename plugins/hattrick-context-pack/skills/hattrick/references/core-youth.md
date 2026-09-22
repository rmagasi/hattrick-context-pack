# Youth academy and scouting

Core section of the hattrick skill, loaded on demand. Deeper tables live in the other `references/` files it points to.

## Two youth systems (per rulebook, only one active at a time)
- **Scout Network**: the simpler, default system. 1-3 scouts each propose **one finished 17yo player per week**, you can sign at most one per week. Quick payoff, no training control. Weekly cost: 2,000 € for the first scout, 1,000 € for each additional scout.
- **Youth Squad / Youth Academy**: the involved system. You found a youth team (one-time 1,000 € fee), play matches in a youth league, train two skills/week (primary + secondary), reveal skills through matches and coach feedback, and promote players at 17+ to the senior squad (400 € promotion fee). Players are 15-16 years old at recruitment, max 18 in the squad. Players age 19+ can't play youth matches anymore. You can switch back to the Scout Network any time by closing the youth squad, you lose all current youth players, then must wait 6 weeks. "Restart youth team" option available every 48 weeks.
- **You cannot run both at the same time.** Costs spent on the academy also count as scout-network investment, so swapping back is cheaper than starting from zero.

## Youth Academy Mechanics
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

## Valid Primary/Secondary Training Combinations
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

## Pull Timing — The Critical Decision
- Optimal pull age: **17 years 0 days** (17.00)
- The younger the player at pull, the more senior training time available
- After 17.0, value and training efficiency in seniors is maximized
- Player should have hit relevant skill caps in YA before pulling — wasted training otherwise

## YA Development Philosophies
| School | Approach | Outcome |
|--------|----------|---------|
| **Xarnism** | One elite player, train primary to cap at 17.0 | One great player, uncertain supporting cast |
| **Berthlism** | Focus on highest-potential player, maximize primary | Similar to Xarnism but more flexible |
| **Zugism** | Group of multi-skilled players, train many skills broadly | Well-rounded squad, slower individual peaks |

**General best practice**: Pull at 17.0 with primary skill at cap (ideally Excellent+) and one capped secondary. Then continue training primary in seniors.

## Scout Network (parallel system)
Per HT-Tasos (Nov 2023):
- Average TSI of pulled academy player if you ignore the YA: ~155
- Average TSI if you fully optimize the YA: ~710
- Average TSI from Scout Network: ~490

Scout Network is the middle-ground for managers who don't want full academy commitment.

## Tools & Sites
- **Hattrick Youthclub**: <https://www.hattrick-youthclub.org/>
- **Scoutrick** (formerly Rate My Academy): <https://www.scoutrick.org/players>
- TSI (Total Skill Index) = rough measure of total skill value, affected by form changes. See `references/xp-form-loyalty.md` for the exact formula.
