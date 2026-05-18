# Tournaments, Cups, National Teams & League System Reference

Sourced from the Unwritten Manual #15.

---

## League Series System

### Fixture Matrix (8-team league, 14 weeks)

| Week | Matches |
|------|---------|
| 1 | 1–2, 3–4, 5–6, 7–8 |
| 2 | 4–1, 2–7, 6–3, 8–5 |
| 3 | 1–8, 3–5, 4–2, 7–6 |
| 4 | 6–1, 2–3, 5–7, 8–4 |
| 5 | 1–7, 4–5, 3–8, 2–6 |
| 6 | 5–1, 7–3, 6–4, 8–2 |
| 7 | 1–3, 2–5, 4–7, 6–8 |
| 8 | 3–1, 5–2, 7–4, 8–6 |
| 9 | 1–5, 3–7, 4–6, 2–8 |
| 10 | 7–1, 5–4, 8–3, 6–2 |
| 11 | 1–6, 3–2, 7–5, 4–8 |
| 12 | 8–1, 5–3, 2–4, 6–7 |
| 13 | 1–4, 7–2, 3–6, 5–8 |
| 14 | 2–1, 4–3, 6–5, 8–7 |

(Numbers are league rank/position, not team IDs.)

### Bot / Ownerless Team Rules
- A team that has been ownerless for 7 weeks (14 weeks if the manager has played for >1 year) becomes "without owner."
- Such a team turns into a **bot** at the next of: before round 1 of the Cup; after round 7 of the league; after round 14 of the league.
- Supporters never have their account locked due to inactivity.

**April 2024 update — "In Administration":**
- During-season ownerless teams now keep their squad and label as "In Administration" rather than immediately becoming bots.
- They perform far worse from week 8 onward.
- Original owner can return mid-season and reclaim the team.
- At week 16, In-Administration teams are replaced by a bot or new manager.
- New signups now usually take a bot's place rather than displacing In-Administration teams.

### Promotion / Demotion
- "More flexible" league pyramids since July 2024 — promotion and demotion rules can vary by league. Always check the league information page.
- Promotion calculator (predicts your next season's series): <https://sourceforge.net/projects/hattrick-pm/>

### End-of-season bot promotion/demotion (per rulebook)
- Bot teams in **division VI or below** are demoted to the lowest division at season's end.
- **Exception**: a bot team that wins its division-VI group is allowed to promote (or play the promotion play-off).
- Bot teams in **division V or higher** follow the same promotion/relegation rules as owned teams.
- Slots freed up by demoted bots are filled by "lucky losers" - mostly play-off losers and sometimes directly-relegated teams. You can opt out via team settings.
- If there are more bot teams in higher divisions than there are managers in the lowest division, the lowest division is automatically **closed** and held in reserve.

### Promotion thresholds (based on relative division sizes, per rulebook)
| Your division vs the one above | Direct promote | Play-off |
|---|---|---|
| Yours is 4× larger | Half of group winners | Other half of group winners |
| Yours is 2× larger | 1st only | 2nd |
| Same size | 1st and 2nd | 3rd and 4th ("top 4 promote") |

### Relegation
- 7th and 8th: relegate directly.
- 5th and 6th: relegation play-off (one match to stay up).
- Lowest division: no relegation.

---

## National Cup, Divisional Cup, Challenger Cup

### Match XP per cup type
- National Cup match: **7 XP points** (~2× league)
- Divisional Cup match: **7 XP points**
- Challenger Cup match: **1.75 XP points** (½ league)
- League match: **3.5 XP points**
- 100 XP points = 1 visible XP level.

### Card consequences
- Yellow/red in a cup match → miss the next **competitive (League)** match (not just the next cup match).
- Challenger Cups and Consolation Cup are also subject to cards.

### Cup Draw (post Nov 2022)
The draw is now done **2 rounds at a time**, so the next round's matchups are visible before the current round is played.

If a lower-ranked team upsets a higher-ranked team in round N, that lower team **inherits the higher team's slot** for round N+1. But for round N+2 onward, the original cup ranking is re-applied — so a single upset doesn't grant a permanent easier path.

**Worked example** (16-team cup):
Round 1 matchups follow rank order: Rank 16 vs Rank 1, Rank 15 vs Rank 2, ..., Rank 9 vs Rank 8.

Expected Round 2 (assuming favourites win): Rank 8 vs Rank 1, Rank 7 vs Rank 2, Rank 6 vs Rank 3, Rank 5 vs Rank 4.

If Rank 16 and Rank 14 win their R1 matches (upsets), the actual Round 2 becomes:
- Rank 8 vs Rank 16 (Rank 16 inherits Rank 1's seat)
- Rank 7 vs Rank 2
- Rank 6 vs Rank 14 (Rank 14 inherits Rank 3's seat)
- Rank 5 vs Rank 4

But for Round 3, the system re-uses original cup rank — if Rank 16 wins again, it acquires Rank 8's spot for Round 3 (which is the original favourite's slot in that bracket).

### Cup Ranking Within a Division
1. Active demoted teams
2. Active teams that neither demoted nor promoted
3. Teams promoted by their own strength
4. Teams promoted "for free" (replacing a demoted bot)
5. Bots (filling vacant spots)

Within each tier: ranking from end of last season. Stays fixed for the duration of the cup.

### Cup Prize Money (per current official rulebook)

Note: the rulebook authoritative tables differ from older Unwritten Manual values. Numbers below are the current in-game amounts.

**National Cup track**

| Round Exit | National Cup | League Cup (Smaragd/Rubin/Zafír) | Consolation Cup |
|---|---:|---:|---:|
| Winner | 300,000 | 60,000 | trophy only |
| Runner-up | 200,000 | 30,000 | - |
| Semi-final | 150,000 | 20,000 | - |
| Quarter-final | 100,000 | 10,000 | - |
| Round of 16 | 50,000 | 5,000 | - |
| Round of 32 | 40,000 | - | - |
| Round of 64 | 36,000 | - | - |
| Round of 128 | 32,000 | - | - |
| Round of 256 | 28,000 | - | - |
| Round of 512 | 24,000 | - | - |

**Divisional Cup track** (in countries with 7+ divisions; for divisions 7 and below)

| Round Exit | Divisional Cup | Divisional League Cup | Divisional Consolation |
|---|---:|---:|---:|
| Winner | 60,000 | 30,000 | trophy only |
| Runner-up | 30,000 | 20,000 | - |
| Semi-final | 20,000 | 10,000 | - |
| Quarter-final | 10,000 | 5,000 | - |
| Round of 16 | 5,000 | - | - |

**HFI**: all of these prizes are **reduced by 25%**. HFI uses its own cup structure (Hattrick Femme International Cup), not the Hungarian National Cup. Hungarian women's clubs in HFI play HFI cup matches on Tuesday 17:00 HT-time and league matches on Saturday 18:30 (divisions 1-6) or 18:45 (division 7), per the HFI local-schedule page.

**Top scorer prize**: 2,000 € per cup, paid at season's end. If two players tie and one is yours, you get the prize. If both are yours, you still only get one prize.

### League Cup placement after early Cup exit
The three League Cups (in Hungary called Puskás Ferenc/Smaragd, Bozsik József/Rubin, Hidegkuti Nándor/Zafír) draft losers from the National Cup:

| Lost in NC round | Goes to |
|---|---|
| 1 or 6 | Smaragd / Puskás (1st-tier League Cup) |
| 2 or 5 | Rubin / Bozsik |
| 3 or 4 | Zafír / Hidegkuti |

Teams that lose in round 1 of Smaragd or Rubin drop into the Consolation Cup. The Consolation Cup awards a trophy but no money.

### Cup capacity ladder (week by week)
Maximum cup size is chosen as the smallest one that fits all owner-managed teams; remaining slots filled with bots.

| Week | National | Smaragd | Rubin | Zafír | Consolation |
|---|---:|---:|---:|---:|---:|
| 1 | 16,384 | - | - | - | - |
| 2 | 8,192 | 8,192 | - | - | - |
| 3 | 4,096 | 4,096 | 4,096 | - | 4,096 |
| 4 | 2,048 | 2,048 | 2,048 | 2,048 | 4,096 |
| 5 | 1,024 | 1,024 | 1,024 | 2,048 | 2,048 |
| 6 | 512 | 512 | 1,024 | 1,024 | 1,024 |
| 7 | 256 | 512 | 512 | 512 | 512 |
| 8 | 128 | 256 | 256 | 256 | 256 |
| 9 | 64 | 128 | 128 | 128 | 128 |
| 10 | 32 | 64 | 64 | 64 | 64 |
| 11 | 16 | 32 | 32 | 32 | 32 |
| 12 | 8 | 16 | 16 | 16 | 16 |
| 13 | 4 | 8 | 8 | 8 | 8 |
| 14 | 2 | 4 | 4 | 4 | 4 |
| 15 | - | 2 | 2 | 2 | 2 |

### Cup income split
- **Early rounds**: 67% home / 33% away (same as league for the home team's perspective).
- **Final 6 rounds**: neutral venue, 50/50 split.
- Crowd size scales with cup type: National/Divisional Cup later rounds draw league-level crowds; League Cup ~3× a friendly; Consolation ~2× a friendly; Divisional League Cup ~2× a friendly; Divisional Consolation ~1.5× a friendly.

### Cup-specific effects on the team
- **National Cup and Divisional Cup**: full effect on Team Spirit, Confidence, and supporter mood (just like league matches).
- **League Cup and Consolation Cup**: TS, Confidence, and supporters react as if these were friendlies.
- **Cards and injuries**: fully apply in every cup. A yellow card in any cup match can still trigger the next-league-match ban.
- **XP per cup match**: National Cup / Divisional Cup gives 2× a league match (7 XP); League Cup and Consolation Cup give ½ a league match (1.75 XP).

---

## Hattrick Femme International (HFI) - schedule and rules

HFI is the country-equivalent league for women's teams (LeagueID=3000). It runs as a separate "country" inside Hattrick with its own series system, cup, and update timeline.

### HFI weekly schedule (HT-time, CET-equivalent)

| Event | Day & time |
|---|---|
| Cup matches | Tuesday 17:00 |
| Secondary cups (Smaragd/Rubin/Zafir equivalents) | Tuesday 17:15-17:45 (15-45 min after the main cup) |
| Training update + daily update | Thursday 10:30 |
| Daily updates (post-friendly) | Thursday 16:30, then daily at 10:15 / 17:15 / 09:15 etc. |
| Weekly + daily update (economy) | Friday 13:15 |
| Saturday daily update | Saturday 09:15 |
| League matches, divisions 1-6 | Saturday 18:30 |
| League matches, division 7 | Saturday 18:45 |

So the HFI weekly cycle is **Tuesday cup, Thursday training, Friday economy, Saturday league** - shifted from the main-HT pattern but with the same logical sequence.

### HFI-specific rules
- All league, cup, and promotion prize money is **reduced by 25%** vs the standard rulebook tables.
- Match-day income and sponsor pay are also smaller (separate reduction).
- No open transfer market - HFI clubs cannot buy or sell players to/from non-HFI clubs, and the in-HFI transfer market is heavily restricted. Players are recruited via Scout Network or Youth Academy only.
- Cup structure: HFI runs its own National Cup (not the Hungarian one), with the same bracket sizes, round names, and league-cup spillover system (Smaragd/Rubin/Zafir equivalents), just with reduced prize money.
- Off-season length, bankruptcy thresholds, staff costs, training mechanics, and YA mechanics are **identical to the main game** - HFI is not a different ruleset, just a different country with reduced economy.
- Season alignment: HFI runs on the **same season numbering and same week-1-to-week-16 schedule** as the main Hattrick world. Season 79 -> 80 transition happens on the same calendar week for HFI as for Hungary.

### What is NOT confirmed from the new clippings
- Exact end-of-season HFI prize money - the 25% reduction is documented but per-division HFI numbers are not separately published; apply 0.75x to the standard tables.
- HFI title bonus and HFI promotion bonus - same as standard tables x 0.75.
- HFI bankruptcy thresholds - assumed identical to main game (-40k / -100k USD) until proven otherwise. The clipping does not address this.
- Off-season week count - not in the HFI clipping; assume same as main game.

---

## Hungary (men's main league) - schedule

Country code: LeagueID=51. Source: <https://www.hattrick.org/World/Leagues/Events.aspx?LeagueID=51>.

### Hungary weekly schedule (HT-time, CET-equivalent)

| Event | Day & time |
|---|---|
| Daily update | Monday 07:20 |
| Daily update | Tuesday 07:20 |
| Daily update | Tuesday 23:00 |
| Daily update | Thursday 09:45 |
| Training update + daily update | Thursday 17:45 |
| Daily update | Friday 07:14 |
| Weekly + daily update (economy) | Friday 23:15 |
| Cup matches (main + secondary, secondary 15-45 min later) | Wednesday 09:45 |
| Friendlies, domestic, normal rules | Wednesday 09:45 |
| Friendlies, domestic, cup rules | Wednesday 09:45 |
| International friendlies, normal rules | Wednesday 09:45 |
| International friendlies, cup rules | Wednesday 09:45 |
| League matches (Level 6 and higher) | Saturday 15:30 |

So the Hungary weekly cycle is **Wednesday cup + friendlies, Thursday training, Friday economy, Saturday league**. Hungarian friendlies (both domestic and international, both rule sets) all share the Wednesday 09:45 slot alongside cup matches, the country has consolidated all midweek competitive and friendly play into a single time window.

### Hungary vs HFI - same season, different week

For a manager running both a Hungarian men's team and an HFI women's team (e.g., a multi-team account), the cycle is staggered, training falls Thursday 17:45 in Hungary versus 10:30 in HFI, economy falls Friday 23:15 versus 13:15, league falls Saturday 15:30 versus 18:30. The HRF download and order-setting deadlines therefore differ by country, plan workflows around the earlier-of-the-two cutoffs if managing both.

---

## Friendlies

International friendly schedule and times: see <https://wiki.hattrick.org/index.php?title=Friendly>.

Some country times were updated April 2024 — check the country-specific schedule from the country page.

### Per rulebook (current)
- **Types**: Normal rules, or Cup rules (cup-rule friendlies that end as draw go to extra time and possibly penalties).
- **International friendly travel cost**: 1,200 € (but bigger crowd). Departure Tuesday 18:00 CET; return Thursday 8:00 CET. You cannot book the next friendly until the team is back. Mid-week friendlies must be booked by Tuesday 18:00; domestic-only friendlies bookable from Thursday 6:00.
- **Weekend friendlies in weeks 15 and 16**: bookable Monday 06:00 to Friday 23:59, provided you don't have a play-off the same weekend.
- Friendly results do **not** affect TS, Confidence, supporters, or sponsors. Injuries can still happen at the normal rate.
- Neutral venue: possible if both teams agree. If the chosen neutral pitch is in your own region, you still get the home-field bonus even as the listed away team. Ticket revenue: not paid to the stadium owner if it's a friendly on neutral ground.

---

## Hattrick Arena Tournaments

| Aspect | Behaviour |
|--------|-----------|
| Team Spirit | Fixed at "content" |
| Confidence | Fixed at "wonderful" |
| Injuries | None occur; existing injuries still prevent play |
| Training | None gained |
| Experience | None gained |
| Cards | Tournament-specific (don't carry over to/from regular HT). Ladders: cards don't apply at all. |
| Formation XP | Uses your normal HT formation XP, but doesn't gain new XP from tournament games |

---

## National Teams (post-Season 77 format)

### Squad Eligibility
- Main NT: players **22+ years old**
- U21: players **19–21 years old**

### NT Coach
- Standard NT coach Leadership = exactly **6.95** (per HT-Tasos).
- The NT coach's offensive/defensive bias can be freely adjusted per match between 100% defensive and 100% offensive.

### NT Match Mechanics
- Home in qualification: only **111.493%** midfield bonus (the derby-away coefficient), not the full 119.892%.
- Daily updates: **03:00 HT time**.
- Players cannot get injured in **Nations Cup** games or **friendly NT/U21** matches.
- Yellow/red cards in NT matches → quarantine for next NT match only, not for club matches.
- For Nations Cup, cards behave like other tournaments (see arena rules).

### TS / TC Resets
- Wednesday before first Continental match (Week 3 of the season).
- Wednesday before first World Cup Round 1 match (Week 13).
- Monday of Week 12 for teams playing Wild Card play-off games.
- Reset & midpoint values: **5.0** for both TS and TC.

### TS loss when removing a player from NT roster (none when adding)
| Character | Loss |
|-----------|-----:|
| Nasty | 0–4.5% |
| Controversial | 4.5–9.0% |
| Pleasant | 9.0–13.5% |
| Sympathetic | 13.5–18.0% |
| Popular | 18.0–22.5% |

### POE TS loss
After Paradise on Earth in NT: **−0.66 per TS update**.

### Fog of War (FOW)
Closed window before NT/U21 matches when no NT data is publicly visible: **8 hours** (since Oct 2017, raised from 4).

### Formation XP for NT
- Each NT has its own formation experience.
- At the start of every Continental Championship and World Cup, NT coaches have ~1 week to designate **6 formations** to start at Formidable; the rest start at Poor.
- If they don't decide, formation XP is whatever it was before the reset.
- Nations Cup carries XP over from the Continental Championship and updates normally afterwards.

### Benefits when your player is in the NT
- The NT covers **33% of his wage** (player at a domestic club) or **40%** (foreign legionnaire).
- He earns XP at the very generous NT rates (see XP table in `xp-form-loyalty.md`).
- If he gets injured in an NT competitive match, your club receives the **normal wage compensation plus 100% of his wage** multiplied by the expected weeks out, on top of the normal compensation. NT friendly matches cannot injure players.
- NT match days are different from club match days, so you never lose him for a club match.
- He gets no club training in any week he plays a NT match.

### NT player conduct
NT match cards are tracked in a separate ledger from club cards. Cards earned in NT or U21 don't affect club eligibility and vice versa. Cards clear at the end of each NT competition or when the team is eliminated.

### Player Release Rules (HT-Tasos)
**If team is ownerless:**
- Player has 3+ caps and is in prospect list → NT coach can auto-release.
- Player has been in prospect list >1 season → NT coach can auto-release.
- Otherwise → coach must create a ticket to NTAs.

**If team is not ownerless but inactive (last login 41+ days, or supporter 6 months minus 1 week):**
- Player in prospect list → ticket to NTAs required.
- Player not in prospect list → no auto-release.

**When a team becomes ownerless/bot:**
- Player in prospect list → NTA auto-releases.

For non-ownerless teams, the regular limit is 48 days / 6 months; the link is enabled a week earlier to allow NTA discussion time.

---

## NT Ranking Formula

```
P = M × I × T
```

Where:

**M (Match Result)**
| Outcome | Points |
|---------|-------:|
| Win | 3 |
| Draw | 1 |
| Loss | 0 |
| Win on penalties | 2 |
| Loss on penalties | 1 |

**I (Match Importance)**
| Match | Points |
|-------|-------:|
| World Cup Semi/Final | 4 |
| WC other rounds | 2.5 |
| Continental Final | 3 |
| Continental other matches | 2 |
| Nations Cup | 1 |
| Contender League | 2 |
| Friendlies | 0 |

**T (Opponent strength)**:
```
T = 250 − opponent_ranking
```

Final ranking = average of last 5 seasons' P, weighted: **100% / 70% / 50% / 30% / 20%** (current → 4 seasons ago). Rankings update after every match.

---

## World Cup Format (post-S77)

### Continental Cup → World Cup qualification slots
| Continent | Total NT teams | WC slots |
|-----------|---:|---:|
| Europe | 48 | 32 (4 promotions / group) |
| Asia-Oceania | 42 | 21 (3 promotions / group) |
| Africa | 24 | 12 (3 promotions / group) |
| America | 30 | 20 (4 promotions / group) |

### Wild Cards
- 11 Wild Card slots awarded via play-off.
- Best 20 non-qualifying teams + best 2 from Contenders League → 22 teams play down to 11 winners.

### World Cup Structure (96 teams)
- Round 1: 16 groups of 6, round-robin home/away. Top 4 advance.
- Round 2: 16 groups of 4, round-robin. Top 2 advance.
- Round 3: 8 groups of 4, single match per opponent at neutral venue. Top 2 advance.
- Round 4: 4 groups of 4, single matches at neutral. Top 2 advance.
- Round 5: 2 groups of 4, single matches at neutral. Top 2 advance.
- Semis & Final: neutral venue.

### Tiebreakers in groups
1. Points
2. Goal difference
3. Goals scored
4. Last WC ranking (qualification) / ranking before final group match (later rounds)

### Continental Cup Format
- 6 teams per group, double round-robin (home/away), 10 weeks.
- Quarter, semi, finals in last week (best 8 in each region).
- Non-qualifiers can schedule friendlies on Fridays.

### Nations Cup
- For NT teams that didn't qualify for the World Cup.
- Swiss-format tournament running parallel to the WC.

### Contender League (since Jan 2025)
- For newly-added nations.
- Swiss-style tournament parallel to the Continental Cups.
- Top 2 → Wild Card play-off slots.
- Ranking points from CL flow into NT ranking, determining if a team plays Continental Cup or CL the next NT season.

### NT Coach Restrictions
- A manager cannot be NT coach for two NTs (or two U21s) at the same time.
- Can be both NT coach and U21 coach for the same country.

### NT "Save default lineup" trick (rarely useful nowadays due to FOW)
If you forgot to send orders for a NT match, you can set the lineup for the *next* match and tick "Save as default lineup" — this might also apply to the imminent match if NT match generation hasn't happened yet (NT matches generate ~19:52 HT-time; window closes ~19:50). Risky, and FOW makes this less reliable since 2017.

---

## Hattrick Masters

- Cards: only red cards in match have consequences (no quarantine across matches).
- Injuries: registered as in any tournament.
- Team Attitude: PIC effect halved (+25% TS instead of +33%); MOTS effect halved (−33% TS instead of −50%). The in-match effect is the same.
- Training: no effect.
- Monday matches play at **16:00 HT-time** instead of the regular 20:00 (since June 2021).
- Open to **cup winners + national champions** only. 256+ team field, knockout, 9 rounds. Draw fully random, neutral venues. If the same team wins both cup and league in a country, only that one team represents the country. Lost-owner cup/league winners are excluded.
- 4-week event starting after league round 4. Matches Mondays 16:00 and Thursdays 20:00 CET.
- Match XP: **17.5 points** (5× a league match).

### HT Masters prize money
| Round Exit | Prize (€) |
|---|---:|
| Winner | 160,000 |
| Runner-up | 80,000 |
| Semi-final | 40,000 |
| Quarter-final | 20,000 |
| Round of 16 | 10,000 |

Gate revenue is split 50/50.

---

## Additional Club

The 16-week rule (must wait 16 weeks before opening a new additional club after a previous one was launched) is **temporarily removed** by HTs when new nations are created (during offseason). In that case, only one closing + opening is allowed to prevent abuse.

### Eligibility
- **Diamond Supporter**: up to **3 additional clubs** by default, no licenses required.
- **Platinum Supporter**: **1 additional club** by default. Buy **Extra Club Licenses** to expand up to **3** additional clubs.
- Additional clubs start with the same cash as any new team but skip the Manager Training.

### Rules across your clubs
- **No transfers** between your own clubs.
- You cannot collect motherclub or previous-owner commission when one of your clubs later sells a player your other club had.
- Your clubs **cannot share a league group**, cannot meet in play-offs, cannot meet in the cup except in the **final**.
- If both your clubs would qualify to the top division at the same time, only the primary promotes; the other team's slot goes to the highest-placed relegated team.

### Foreign additional clubs
- "Foreign-managed" additional clubs are capped per league: by default 50% of slots reserved for local managers. In small leagues (≤4 divisions and <50 local managers managing ≤20% of teams), more slots open up.
- Check the "Request additional team" link in your manager profile - country dropdown shows available slots per country.

### Bankruptcy + license expiry
- If your **primary** team goes bankrupt, you lose access to additional clubs too.
- If an **additional** team goes bankrupt, you can start a new one once 16 weeks have passed since you launched the current additional.
- When you close an additional team manually, you also have to wait 16 weeks before opening another.
- **Cannot close** an additional team while it has players on the transfer market.
- If your Platinum/Diamond/Extra License expires: you keep ownership for 1 week, then lose control. After 7 weeks the team is removed permanently unless you re-subscribe.

### Voting (additional clubs in other countries)
First vote after 2 seasons; "senior" vote after 10 seasons (and that is the cap - max 2 votes per additional team, vs 4 for a primary). Hattrick International and Self-Made Players League don't grant any voting rights.

### Other edge cases (Rules 20)
- **Platinum default**: by default Platinum gets **1** additional club, you can purchase **Extra Club Licenses** to raise this up to **3**. Diamond starts at 3 with no licenses required.
- **3 of your teams in the same cup semi-final** is rare but possible, in that case two of your sister teams will face each other, the rulebook does not exempt you. The "no meeting before the final" rule has this exception baked in.
- **Switching window between seasons**: additional clubs can switch series in the same series-switching window as primary clubs, with one constraint, you cannot switch INTO a series where another of your clubs already plays.
- **Flags**: each club collects its own flag set, playing against your sister team rewards both clubs with their respective new flags.
- **Achievements**: tracked per **manager**, not per club. Earning an achievement on the additional team adds it to your single manager achievement list.
- **Switching country**: not directly possible, you have to close the additional club (16-week cooldown) and open a new one in the new country. The cooldown is **waived** when Hattrick launches a brand-new nation, in those windows you can close-and-reopen once without waiting.

---

## Divisional Battles & seasonal Trophies (Rules 17)

These are official Hattrick Arena competitions, free to participate in if invited, that sit alongside league and cup play.

**Divisional Battles**, your league series collectively competes against another series in the same division each week. Every participating team plays one team from the other series in a parallel friendly-style match. Goal, finish the season as the **best series in your division**. Useful as a side metric and for bragging rights, no league or cup implications.

**Generation Trophy**, pre-season invitational tournament where managers who joined Hattrick around the same time bracket against each other. Free entry for those invited.

**Supporter Trophy**, pre-season invitational tournament open to all current Hattrick Supporters (Bronze and up).

All three competitions run under standard Hattrick Arena rules, fixed TS (content) and Confidence (wonderful), no training, no XP, no injuries, no formation experience changes, neutral venue with no gate income.

---

## Elections (National Team coach)

- Elections run early in the season, starting 2 days after the World Cup final.
- Alternates each cycle: senior NT coach one season, U21 NT coach the next.
- Each coach serves 2 seasons; the term ends ~1 week after the next WC final.
- Must have been in Hattrick at least **1 season** to vote.

### Voting power (Hungarian/local primary club)
- 1 vote after season 1
- 2 votes after season 5
- 3 votes after season 10
- 4 votes (max) after season 15

Each user can also earn up to **2 extra "activity" votes** if their team management is sufficiently active (HT keeps the exact criteria opaque to prevent gaming).

---

## Hattrick Arena - ladder challenge rules

You can only challenge teams a limited distance ahead of you on the ladder. The window scales with your rank:

| Your rank | Can challenge | But not higher than |
|---|---|---:|
| 2-5 | only directly above | - |
| 6-11 | 1-2 positions ahead | rank 5 |
| 12-18 | 1-3 ahead | rank 10 |
| 19-39 | 1-5 ahead | rank 16 |
| 40-63 | 1-7 ahead | rank 35 |
| 64-99 | 1-10 ahead | rank 57 |
| 100-129 | 1-15 ahead | rank 90 |
| 130-169 | 1-25 ahead | rank 115 |
| 170-199 | 1-35 ahead | rank 145 |
| 200-249 | 1-50 ahead | rank 165 |
| 250-599 | 1-75 ahead | rank 200 |
| 600-1099 | 1-100 ahead | rank 525 |
| 1100-2499 | 1-250 ahead | rank 1000 |
| 2500-5499 | 1-500 ahead | rank 2250 |
| 5500+ | 1-1000 ahead | rank 5000 |

- Challenger pays the credits; match auto-accepts; played 24 h after challenge (or sooner if both teams tick "Quick start", not available in ranks 1-100).
- Win → you take the challenged team's slot, everyone in between shifts down by 1. Lose → no movement.
- After being challenged or after challenging, 12 h cool-down before either party can be involved in another challenge.

---

## Daily / Weekly Update Timeline

### After League match — 1st daily update
TS, Confidence, Arena, Weather, Injuries, TSI changes for injured, Supporters coming/going.

### After League match — 2nd daily update
Same as above (no Supporters event).

### After League match — 3rd daily update
Same as 2nd.

### After Cup/Friendly match — 1st daily update
TS, Confidence, Arena, Weather, Injuries, TSI changes, Supporters, **and engine takes into account training intensity for next week**.

### After Cup/Friendly match — 2nd daily update + TRAINING
TS, Confidence, Arena, Weather, Injuries, TSI changes.
**Training occurs (takes a few minutes).**
**Skill drops for older players** (since Dec 2024 merged here).
**Bruises can occur during training** (since Sept 2024).

### After Cup/Friendly match — 3rd daily update
Same as 2nd (no training).

### After Cup/Friendly match — 4th daily + WEEKLY update
TS, Confidence, Arena, Weather, Injuries, TSI changes.
**Economy update** (income + expenses).
**Youth Academy update.**
**Supporters' mood update.**
**Youth pull** happens.

### At end of every match
For everyone:
- Player experience
- Formation experience
- New injuries

End of official matches (League and Cup) only:
- Team Spirit
- Background Team Confidence
- Supporters' mood
- Sponsors' mood
- Yellow/red cards

---

## Sources
- LA-Alpa, "[HT] The Unwritten manual #15", Hattrick Global English Forum thread 17665541 (sections 19 "Series System", 20 "Cup System", 21 "Friendlies", 22 "Arena Competitions", 23 "National Teams", 24 "Hattrick Masters", 25 "Additional Club")
- **Official Hattrick rulebook**, <https://www.hattrick.org/Help/Rules/Complete.aspx> - current league, cup, promotion prize money tables and HFI 25% reduction (clipped May 2026). League prize, promotion bonus and cup prize tables now use these authoritative numbers.
- **HFI local-schedule page**, <https://www.hattrick.org/World/Leagues/Events.aspx?LeagueID=3000> - HFI match times and update timeline.
- HT Editorials: April 2024 (Team creation), July 2024 (Flexible league system), November 2023 & November 2024 (YA/Scout system updates), May 2025 (overconfidence tweaks), Feb 2025 (substitute conditional orders).
- HT-Tasos comments on World Cup forum (NT release rules)
