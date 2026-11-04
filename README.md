# Fair Lawn keeper calculator

Personal keeper and trade calculator for the Fair Lawn Fantasy Football League (12 teams, half PPR, 3 keepers).

Open it at https://berkoar.github.io/fairlawn-keeper/ and tap **Sync from Sleeper** to load the current rosters and 2027 pick ownership. Each player's next-year keeper cost is his 2026 draft round minus 2 (undrafted pickups cost a 10th).

In season, upload FantasyPros' Rest of Season rankings (Half PPR, Overall, CSV) each week. A player's trade value is then:

- **now**: his rest-of-season rank on the pick-value curve, times the share of the season left (playoff weeks count 1.5x), times your win-now weight
- **keep**: his 2027 keeper surplus, priced against a blend of August ADP and his current rank

Players drafted in rounds 1-2 can't be kept but still carry their full "now" value.

`fairlawn.html` is a self-contained build. The shared, league-neutral version lives at https://github.com/berkoar/keeper-workbench.
