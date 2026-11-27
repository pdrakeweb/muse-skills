# Card Account Verification

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/card_account_verification


## Check freshness before acting

- Check the last updated date for each card account itself before using its number or status.

- Treat a recent cache sync as proof of sync only, not as proof that a single account is current.

- Stop and verify elsewhere when a listed tail is absent from the current issuer view or cannot be confirmed as live.

## Check inventory completeness before claiming a sole card

- List every card that could protect the outcome before you claim one card is the only protector.

- Compare the card map against Monarch accounts and tracker rows and issuer mail and flag any account that appears in one source and not in the map.

- Treat a card with no row in the card map as unknown, not as absent, and do not recommend opening a new card until you have checked for it.

- Name each protecting card with its live tail and its source before you present a cancel or downgrade action that would remove protection.

## Collapse a reissue chain

- Search issuer mail for replacement, reissue, and welcome messages for the same account before treating two tails as two cards.

- Collapse successive tails into one live entry when issuer mail shows a replacement chain, and keep earlier tails only as history.

- Carry fees, renewal dates, and actions forward only to the live tail, and withdraw any action tied to a superseded tail.

## Re-verify a forward credit method before recommending it

- Check the current terms for a credit method before you recommend it as a future play, and do not carry a prior year realized credit forward on the strength of a past memo alone.

- Search recent research and user corrections for a dead method finding on that credit before you repeat the method.

- State the method and the trigger and the timing and the dated current source for each recommended credit play, and label the play unverified when no current source confirms it.

- Withdraw a dead method from the plan when a correction or current research shows it no longer triggers, and present a replacement only when a current source confirms the replacement.

## Present only verified actions

- Report a renewal or anniversary date as unknown when no source states it, and label any date derived from a fee or statement date as a hypothesis.

- Name the holder for each card from a current source, and do not assign a card to a person from an old tracker row alone.

- Present the live tail, its last updated date, and the source for each action in the report, and omit any card you could not verify.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Ask the user to read the live tail from the issuer app when mail, tracker, and cache disagree, since that read settles the chain fastest.

- Re-read the tracker fresh whenever a card value will change a decision, rather than reusing a remembered balance or status.
