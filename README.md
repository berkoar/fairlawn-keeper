# Fair Lawn keeper calculator

Personal keeper and trade calculator for the Fair Lawn Fantasy Football League (12 teams, half PPR, 3 keepers).

Open it at https://berkoar.github.io/fairlawn-keeper/ and tap **Sync from Sleeper** to load the current rosters and 2027 pick ownership. Each player's next-year keeper cost is his 2026 draft round minus 2 (undrafted pickups cost a 10th).

In season, upload FantasyPros' Rest of Season rankings (Half PPR) each week: the Overall CSV plus the QB, RB, WR and TE CSVs (selected together) for projected points. The page ships with the Nov 4 files built in; any newer upload replaces them. A player's trade value is then:

- **now**: his rest-of-season rank on the pick-value curve, times the share of the season left (playoff weeks count 1.5x), times the pricing mode's weight
- **keep**: his 2027 keeper surplus, priced at his projected 2027 draft position (shown on each row with an 80% range, e.g. `'27 price 4.05 (2.12-7.02)`)

**2027 draft price** comes from a model backtested on six seasons (2020 to 2025). At week 9 of each season it took every player's FantasyPros dynasty rank, rest-of-season rank and points per game (each within his position) and fit, per position, how well they predicted his position rank in the next August's half-PPR ADP. That projected position rank is placed on the August 2026 half-PPR draft board. Across the backtest, half of projections landed within about 20 picks, and the ranges shown cover 80% of outcomes. Dynasty rank carries the most weight everywhere; points per game matters most for RBs and QBs, this season's rank for WRs and TEs. Points per game comes live from Sleeper's weekly scores on each sync (finished weeks only), with nflverse weeks 1-8 built in as a fallback and for players no one has rostered. Dynasty rankings are PPR-only, but so was the training data, so no conversion is needed.

**Pricing modes** set how much this season's production counts against 2027 value, with 2027 picks as the fixed yardstick: Rebuild 0.25x, Balanced 1x, Contend 2x, All-in 3x, or Auto (0.25x at 0% playoff odds up to 2x at 100%). The slider allows any weight from 0 to 3x. The same switch sits above the trade balance, along with one for the trade partner (Auto from their playoff odds, or set by hand), and the balance shows whether the deal works by each side's own measure.

**Deal check** (in season, above the trade balance) judges a trade from both sides. Your gain is measured in your pricing mode, the partner's gain in theirs (Auto from their playoff odds, or set by hand). Together they're the value the deal creates, and a fair deal splits it roughly evenly. It flags "You're underselling" when you keep under 30%, states the fair ask in 2027-pick terms, and suggests one-tap counter-offers (ask for one of their picks or players, keep something you were giving, add a pick, or drop something you were getting) that move the split toward even while leaving both sides ahead. It also ranks every team by what your outgoing package is worth to them, so you can shop it to the highest bidder first. The partner is detected from whose players are on the "You get" side. The old balance bar now reads "By your measure", because even by your own measure only means you got your walk-away price.

**Keeper slots**: with only 3 keepers allowed, a keeper you get adds only what he beats your 3rd-best keeper by, and one you give costs only what he beats the best keeper you'd otherwise leave behind. On by default; the toggle sits at the bottom of the page.

**Playoff odds** simulate the rest of the regular season 4,000 times on the real Sleeper schedule. Team strength is luck-adjusted scoring so far (70%) plus each starting lineup's projected points per week (30%); top 6 by wins make it, points for breaks ties. The odds set the Auto pricing mode and a Buy / Hold / Sell / Strengthen call, based on how much 5 extra points a week would move your odds.

Players drafted in rounds 1-2 can't be kept but still carry their full "now" value.

`fairlawn.html` is a self-contained build. The shared, league-neutral version lives at https://github.com/berkoar/keeper-workbench.
