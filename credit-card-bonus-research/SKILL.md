# Credit Card Bonus Research

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/credit-card-bonus-research

## When this applies
- Apply when finding, comparing, or recommending credit card sign-up bonuses, or when judging whether a new card is worth opening.
- Apply card_account_verification first whenever the recommendation depends on which cards the user already holds.

## Find the current offer
- Never guess or construct issuer offer URLs.
- Find current bonuses on a listing site first. Doctor of Credit is the primary source; Frequent Miler and US Credit Card Guide are the alternates.
- Browse from the listing to the issuer's offer page, and confirm the bonus, the minimum spend, the spend window, and the annual fee there before reporting any figure.
- Note when the listing shows a higher offer through another channel (referral, targeted, in-branch, or a CardMatch-style tool), and name that channel.

## Check eligibility before ranking
- Check the issuer's eligibility rules against the user's current cards and recent openings before ranking an offer. Examples: Chase 5/24, Amex once-per-lifetime bonus language, and Citi or Barclays bonus-recency windows.
- Read the offer's own terms for bonus-eligibility exclusions, and treat the issuer's terms as the authority over any listing site's summary.
- Mark an offer ineligible, or eligibility unknown, rather than ranking it as available.

## Rank the offer
- Rank offers by first-year net value: bonus value plus usable credits minus the first-year annual fee.
- Value each credit at full face value when the user would spend that money anyway, at half when the user would likely use the credit but would not otherwise spend, and at zero when the credit is unusable.
- Value memberships at 25 percent of face value.
- Value the bonus per point or mile: transferable points at 1.0 cent, program-specific points at 0.8 cent, airline miles at 1.5 cents, and a hotel free-night award at half the cash rate of the night it would actually book.
- Treat a bonus that requires spending, whether paid in points or as cash, as a nontaxable rebate.
- Value a bonus at its after-tax amount only when it needs no spending, or when the issuer says it will send a 1099. Bank account bonuses are the common case.
- State the valuation you used for each line, so the user can substitute their own.

## Present the result
- Present every offer worth applying for, ranked, with its eligibility status, and let the user choose.
- Never apply, accept an offer, or switch anything on automatically.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites
- [Doctor of Credit](https://www.doctorofcredit.com/best-current-credit-card-sign-bonuses/): the primary listing of current sign-up bonuses, updated daily. Start here and follow its links to the issuer's offer page.
- [Frequent Miler](https://frequentmiler.com/best-credit-card-offers/): an alternate listing of the best offers, sorted by first-year value. Use it when Doctor of Credit has no entry for a card, or when a second source would settle a figure.
- [US Credit Card Guide](https://www.uscreditcardguide.com/): an alternate source for offer history and issuer eligibility rules.
