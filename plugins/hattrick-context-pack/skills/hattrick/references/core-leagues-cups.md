# Cups, national teams and league system

Core section of the hattrick skill, loaded on demand. Deeper tables live in the other `references/` files it points to.

## League Series System
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

## League prize money (1-4 place, per division)
| Division | 1st | 2nd | 3rd | 4th |
|---|---:|---:|---:|---:|
| I | 400,000 | 235,000 | 165,000 | 100,000 |
| II | 270,000 | 210,000 | 150,000 | 90,000 |
| III | 240,000 | 185,000 | 135,000 | 80,000 |
| IV | 180,000 | 140,000 | 100,000 | 60,000 |
| V | 120,000 | 95,000 | 65,000 | 40,000 |
| VI | 105,000 | 80,000 | 60,000 | 35,000 |
| VII+ | 90,000 | 70,000 | 50,000 | 30,000 |

## Promotion bonus (in addition to league prize money)
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

## National Cup vs Divisional Cup vs Challenger Cup
- Match XP: **7 XP points** per cup match (vs 3.5 for league), Challenger Cup gives only **1.75 XP**.
- 100 XP = 1 visible XP level.
- Red card in cup match = miss next **competitive (League) match**, not cup.
- Cup draw is now done **2 rounds at a time** (since Nov 2022) — easier-path effect from upsets only lasts one round.

## Cup prize money (current, per official rulebook)
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

## National Teams (post-Season 77 format)
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
