# Credit Card Bonus Research

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/credit-card-bonus-research

## Find the current offer

- Never guess or construct issuer offer URLs.

- Find current bonuses on a listing engine first, with Doctor of Credit as the primary source and Frequent Miler and US Credit Card Guide as alternates.

- Browse from the listing to the issuer's offer page and confirm the bonus, the minimum spend, and the annual fee there before reporting any figure.

## Rank the offer

- Rank offers by first-year net value: bonus value plus usable credits minus the annual fee.

- Value each credit at full face value when the user would spend that money anyway, at half when the user would likely use the credit but would not otherwise spend, and at zero when the credit is unusable.

- Value memberships at 25 percent of face value.

- Value the bonus itself with transferable points at full value, program-specific points at 80 percent, airline miles at 150 percent, and hotel free-night awards at half.

- Value an actual cash bonus after tax when comparing offers, since the net value is materially reduced in a high tax bracket.

- Treat points-based bonuses as tax-free rebates even when marketed as a dollar cash bonus.

## Present the result

- Present everything worth activating and let the user choose.

- Never switch anything on automatically.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites

- [Doctor of Credit](https://www.doctorofcredit.com/best-current-credit-card-sign-bonuses/) for the primary listing of current sign-up bonuses, updated daily. Start here and follow its links to the issuer's offer page.

- [Frequent Miler](https://frequentmiler.com/best-credit-card-offers/) for an alternate listing of best offers sorted by first-year value. Use it when Doctor of Credit has no entry for a card or when a second source would settle a figure.
