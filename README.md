---
description: An organization governed by markets, not politics
---

# The Meta-DAO

The Meta-DAO is the first market-governed organization in the history of human civilization. It uses [futarchy](https://mason.gmu.edu/\~rhanson/futarchy.html), a scheme devised by economist Robin Hanson wherein prediction markets make decisions.

At a high-level, Meta-DAO makes decisions as follows:

* Anyone can raise an _improvement proposal_, each of which contains a single Solana Virtual Machine (SVM) instruction. For example, one could create a proposal to transfer 50,000 USDC to a marketing company for a new campaign.
* For each improvement proposal, there are two [OpenBook](https://www.openbook-solana.com/) markets created. In one, you can trade conditional-on-pass USDC for conditional-on-pass META. In the other, you can trade conditional-on-fail USDC for conditional-on-fail META. Conditional-on-pass tokens can be redeemed for canonical tokens if the proposal passes. Conditional-on-fail tokens can be redeemed for canonical tokens if the proposal fails.
* Traders can mint conditional-on-pass and conditional-on-fail tokens using the conditional vault. For example, a trader depositing 10 USDC into the vault would receive 10 conditional-on-pass USDC and 10 conditional-on-fail USDC.
* Traders have 10 days to place trades in both markets.
* At the end of the 10 days, anyone can _finalize_ a proposal. The Meta-DAO programatically checks if the time-weighted average price (TWAP) of conditional-on-pass META, quoted in conditional-on-pass USDC, is higher than the TWAP of conditional-on-fail META, quoted in conditional-on-fail USDC. If it is, it executes the SVM instruction. If it isn't, it doesn't.
* After finalization, traders can redeem their relevant conditional tokens. For example, if the proposal passes, traders can redeem their conditional-on-fail tokens for canonical tokens.
