# Card Account Verification

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/card_account_verification

## When this applies
- Apply before reporting or recommending any downgrade, cancellation, product change, annual-fee action, or credit play on a credit card account.
- Apply before claiming that a card is the only one providing a protection or benefit, such as rental car coverage, trip delay, purchase protection, lounge access, or a free night.

## Check freshness before acting
- Check the last-updated date of each card account itself before using its number or status.
- Treat a recent cache sync as proof that the sync ran, not as proof that any single account is current.
- When a listed tail (last four digits) is absent from the current issuer view, or cannot be confirmed as live, stop and verify it elsewhere.

## Check inventory completeness before claiming a sole card
- List every card that could provide the protection before claiming that one card is the only provider.
- Compare the card map against Monarch accounts, tracker rows, and issuer mail, and flag any account that appears in one source but not in the map.
- Treat a card with no row in the card map as unknown, not as absent. Check for it before recommending a new card.
- Name each protecting card with its live tail and its source before presenting a cancel or downgrade that would remove protection.

## Collapse a reissue chain
- Search issuer mail for replacement, reissue, and welcome messages for the same account before treating two tails as two cards.
- When issuer mail shows a replacement chain, collapse the successive tails into one live entry and keep the earlier tails only as history.
- Carry fees, renewal dates, and actions forward only to the live tail, and withdraw any action tied to a superseded tail.

## Re-verify a forward credit method before recommending it
- Check the current terms for a credit method before recommending it as a future play. Never carry a credit realized last year forward on the strength of an old memo alone.
- Search recent research and the user's corrections for a finding that the method is dead before repeating it.
- For each recommended credit play, state the method, the trigger, the timing, and a dated current source. Label the play unverified when no current source confirms it.
- When a correction or current research shows a method no longer triggers, withdraw it from the plan. Present a replacement only when a current source confirms the replacement.

## Present only verified actions
- Report a renewal or anniversary date as unknown when no source states it, and label any date derived from a fee or statement date as a hypothesis.
- Name the holder of each card from a current source. Never assign a card to a person from an old tracker row alone.
- For each action in the report, give the live tail, its last-updated date, and its source. Omit any card you could not verify, and say that you omitted it.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- When mail, the tracker, and the cache disagree, ask the user to read the live tail from the issuer app. That one read settles the chain fastest.
- Re-read the tracker whenever a card value will change a decision, rather than reusing a remembered balance or status.
