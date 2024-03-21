---
description: How the Meta-DAO implements futarchy
---

# Implementation

### Overview <a href="#overview" id="overview"></a>

The Meta-DAO is composed of [3 open-source programs](https://github.com/metaDAOproject/meta-dao) on the Solana blockchain:

* a _conditional vault_ program,
* a _time-weighted average price (TWAP)_ program,
* and _autocrat_, the program that orchestrates futarchy. All programs are open-source and verifiable.

The Meta-DAO is built on top of [OpenBook V2](https://www.openbook-solana.com/)’s central limit order book. _META_ is the native token of the Meta-DAO.

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

### &#x20;Conditional vault program <a href="#conditional-vault-program" id="conditional-vault-program"></a>

As described in [futarchy](https://metadaoproject.github.io/docs/mechanics/futarchy.html), futarchy requires the ability to ‘revert’ trades in a market so that everyone gets back their original tokens. Unfortunately, blockchains don’t allow you to revert transactions after they’ve been finalized, so we need a mechanism to _simulate_ reverting transactions. That mechanism is conditional tokens.

Before minting conditional tokens, someone needs to create a _conditional vault_. Conditional vaults are each tied to a specific _underlying token_ and _settlement authority_. In our case, the underlying token would be either META or USDC, and the settlement authority would always be the Meta-DAO.

Once a vault is created, anyone can deposit underlying tokens in exchange for conditional tokens. You receive two types of conditional tokens: ones that are redeemable for underlying tokens if the vault is finalized and ones that are redeemable for underlying tokens if the vault is reverted. For example, if you deposit 10 USDC into a vault, you will receive 10 conditional-on-finalize USDC and 10 conditional-on-revert USDC.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

At any time, the settlement authority can either _finalize_ or _revert_ a vault.

If a settlement authority finalizes a vault, conditional-on-finalize token holders can redeem their conditional tokens for underlying tokens. Conversely, if a settlement authority reverts a vault, conditional-on-revert token holders can redeem their conditional tokens for underlying tokens. Because the finalization and reverting are mutually exclusive, total vault liabilities will never exceed total assets.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

For each proposal, the Meta-DAO creates two vaults: one for USDC and one for META. If a proposal passes, it finalizes both vaults. If a proposal fails, it reverts both vaults. So we call the conditional-on-finalize tokens _conditional-on-pass tokens_ and the conditional-on-revert tokens _conditional-on-fail tokens_.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

This allows us to achieve the desired reverting of trades. For example, if someone mints conditional-on-pass META and trades it for conditional-on-pass USDC, either the proposal will pass and they can redeem conditional-on-pass USDC for USDC or the proposal will fail and they can redeem their conditional-on-fail META for their original META.

So we create two markets per proposal: one where conditional-on-pass META is traded for conditional-on-pass USDC and one where conditional-on-fail META is traded for conditional-on-fail USDC. This allows traders to express opinions like “this token would be worth $112 if the proposal passes, but it’s only worth $105 if the proposal fails.”

### &#x20;TWAP program <a href="#twap-program" id="twap-program"></a>

All Meta-DAO markets are on [OpenBook v2](https://github.com/openbook-dex/openbook-v2). There didn’t exist a TWAP oracle for OpenBook or for any other Solana AMM or CLOB, so we [built our own](https://github.com/metaDAOproject/openbook-twap). It uses the same design as [Uniswap V2](https://docs.uniswap.org/contracts/v2/concepts/core-concepts/oracles), and uses several mechanisms to ensure manipulation-resistance.

### &#x20;Autocrat <a href="#autocrat" id="autocrat"></a>

The last piece of the puzzle is _autocrat_, the program that orchestrates futarchy.

Anyone can interact with autocrat to create a _proposal_, which contains fields such as a proposal number, proposal description link, and an executable Solana Virtual Machine (SVM) instruction. For example, someone could create a proposal to transfer 150,000 USDC to a development team to improve a product that’s managed by the Meta-DAO.

The requisite conditional vaults and markets are created at the same time.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

After a configurable amount of time (currently 10 days), anyone can trigger proposal finalization. In finalization, autocrat checks if the TWAP of the pass market is higher than the TWAP of the fail market. If it is, it executes the SVM instruction, finalizes the pass market, and reverts the fail market. If it isn’t, it marks the proposal as failed, finalizes the fail market, and reverts the pass market.

![](http://themetadao.org/img/autocrat-finalize.png)
