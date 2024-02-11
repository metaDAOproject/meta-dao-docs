---
description: Common questions or things people have asked more than once.
---

# Frequently Asked Questions

## I’m new here. What is this place? Is…is this heaven?

No. We get that a lot. But this is actually the Meta-DAO.&#x20;

## Ohhh right. I see the logo in the top left corner. What is the Meta-DAO?

The Meta-DAO is a collection of intellectuals and free-thinkers that aims to fundamentally reform human coordination by proving a system called “futarchy.” The protocol they’ve built is an ongoing experiment that uses market insights to inform the DAO’s governance and investing decisions.

## Sounds intimidating…

It’s not. It’s really just a DAO comprised of terminally online Solana nerds that aims to make money by building and investing in the Solana ecosystem and uses insights gleaned from the market to guide those processes.

## Okay cool. You said the word “futarchy” earlier. What is that?

Futarchy is a system of governance that gives decision making authority to the market rather than to an elected official or the voting populace. Because asset prices in an efficient market reflect all known information at any given time (see Efficient-market hypothesis), they should provide the best prediction of future events based on all available current knowledge. Futarchy aims to capitalize on this superior predictive power by using the market to guide its governance and investing decisions.

Although the concept of futarchy is not new - it was first described by economist Robin Hanson (not Chris Hansen or the drummer “mmmmmbop”) in 2000 - the Meta-DAO is the first organization in the world (to our knowledge) to employ a futarchical system of governance.

## How is futarchy implemented within the protocol? Give me the ELI5.

Currently the flow exists something like this:

1. A topic / issue / initiative is discussed within the Discord or external parties
2. A proposal enters a draft in Discord (see proposal format)
3. Details of the proposal are posted online (Medium / HackMD etc)
4. If there is sufficient attention and responsible parties are aligned then a proposal is submitted on chain (this creates markets for the pass and fail conditions of the proposal) with transaction instructions for on pass.
5. Participants have 5 days to place bid / ask limit orders in the order books, or trade accordingly.
6. Upon the expiration each of the market’s Time Weighted Average Price (TWAP) is evaluated and if the pass market is > 5% of the price of the fail market, the proposal passes and the on chain instruction is executed.

## Can anyone submit a proposal? And can anyone trade in the conditional markets?

Yes and yes.&#x20;

## How can I get involved, what help do you need?

We need people to suggest proposals and ideas. We need content writers, we need UI designers, we need evangelists, we need supporters, we need traders, we need market makers. There’s likely no skill you possess we couldn’t leverage. The code repositories and contributions are open for any and all (if you code). The Discord is open discourse. The internet extends far and wide. X formerly known as Twitter has those thirsty for understanding and knowledge. Currently our primary focus&#x20;

Here are some points of contact if you’re interested in the following categories:

Dean & Nico - Community

Blockchainfixesthis - Content Production

Proph3t - Core Smart Contracts / General

0xNallok - Business Development / General

Dodecahedr0x - Core Codebase (UI & Smart Contracts)

We’re still interested in finding more support for the following categories: Social Media, Marketing, Philosophy, Onboarding, Engagement and Research.

Easiest way to get started is read the current and past draft proposals, review the ongoing conversations, and start talking to people in whatever medium you have available. If you have ideas, don’t be afraid to speak your mind regardless of contention. If you have a skill, deploy it, we accept PRs and suggestions, but nothing stopping you from getting started today.

Beyond that, vote by trading the markets of the proposals. Which you can learn more about below!

## How do I trade in the conditional markets? Start from the top.

To trade in the conditional META/USDC markets, you need to mint conditional tokens. To mint conditional tokens, you’ll first need to attain USDC and/or META.&#x20;

Once you’ve secured a bag of either/both, go to the Meta-DAO dApp, click on the proposal market you want to trade in, find the “Mint” section on the left side of the page, enter the number of tokens you want to deposit and click “Mint.”&#x20;

For every USDC or META deposited, two tokens are minted, one conditional pass token (a pToken) and one conditional fail token (a fToken.) The type of token minted matches the type of token deposited (USDC deposits mint pUSDC and fUSDC; META deposits mint pMETA and fMETA.) Each conditional token can then be used to trade in its respective market; fUSDC can be used to buy fMETA, pUSDC can be used to buy pMETA, and vice versa pMETA can be sold for pUSDC and fMETA for fUSDC.&#x20;

## Okay, now I’ve got my tokens. How do these conditional markets work?

At a technical level, trading in conditional markets is no different than trading in any other market. The machinery - market orders and limit orders, bids and asks, order matching, settlement - is all the same. &#x20;

Where conditional markets diverge from traditional markets, though, is in the implications of the trades being made. This part can get a little confusing so bear with me.

When a proposal is submitted, two conditional META/USDC markets are created - one that represents a world where the proposal has passed and one that represents a world where the proposal has failed. Both markets coexist for a set time period (currently 5 days.) During that time, anyone with conditional tokens can trade in either or both markets.

The pass market represents the expected impact of the proposal. The fail market represents the status quo. Assuming an efficient market (and a sufficiently impactful proposal), the price of META in the pass and fail markets should diverge across the trading period in a way that can inform the Meta-DAO as to whether the market views the proposal as EV+ or EV-.

## So the conditional markets are a means to tap into the predictive power of markets that you were talking about earlier?

Exactly. While trading is taking place in the conditional markets, the price of META in each market is being tracked by a TWAP oracle. At the end of the trading period, the market with the higher TWAP is finalized and the action associated with that market (pass or fail) is executed.

## What does “finalized” mean in this context? What happens to the conditional markets and all of the conditional tokens at the end of the trading period?

Only trades in the market that wins, either the pass market or the fail market, become “real”. By “real” we mean the underlying tokens get converted into USDC or META. For example let’s say the pass market won, pUSDC and pMETA would both be converted into USDC and META. Balances in the losing market are ignored, in this example that is the fail market so fUSDC and fMETA balances are burned. If the fail market won instead, fUSDC and fMETA would be converted to USDC and META, while pUSDC and pMETA balances get burned.

If you remember back to the minting process, for every USDC or META that is deposited, two conditional tokens are created - one for the pass market and one for the fail market. The underlying deposit and value only exists when the pass or fail market is resolved when one of them wins. There is no value creation when these tokens are minted as only one market will settle into the deposited token value.

While trading is taking place on the conditional markets, it isn’t known which conditional tokens will receive asset backing (giving them the equivalent value of the underlying assets) and which tokens will not (rendering them worthless.) When a conditional market is finalized, the deposited tokens become associated with that market, giving its conditional tokens a one-to-one backing with the underlying assets that can be redeemed on the UI. The tokens in the market that was not finalized have no backing and therefore have no value.

The trades that occurred in both markets were “real” - tokens were exchanged - but because backing value is only given to tokens in one of the two markets, the effect is that one market’s trades become meaningful while the other’s become meaningless.

## What should I be considering while trading?

Primarily your role as a participant is to evaluate the value the proposal may or may not add to the Meta-DAO. This boils down to the price of META. Is the price of META reflective of your perspective? If it’s underpriced, you may want to BUY META as it would be “cheap” in your perspective. If it’s overpriced, you may want to SELL META as the dollar value is too high. One thought is to look at the price and say to yourself, this is what the market (aggregate of all participants) values META as, what do I think, and WHY do I think that way. And those reasons or motivations for you as an individual can be varied and diverse. When enough participants come together with these reasons, that is information flowing into a single output, price. Some may be far more advanced in their reasoning, some not so much, but in aggregate it creates a pressure in both the buy and sell direction such that it settles around a middle price. This is what you bring to the market.

## How do you value the Meta-DAO?

MOST proposals will include a financial model with a breakdown of potential revenues, but many may not. Ideally this information, while speculative, is provided and given that information you may think about how that might affect the value in the short, medium and long term of META. Some may be much more impactful in the long term (building a revenue generating business which depends on larger markets) vs the short (releasing funds from the treasury for payment for services rendered). We encourage evaluations, discussions and debate regarding these models, many people may have their own models they apply as well, it’s a fair and free market after all and competitive edge is in information flows.

Some examples of valuation methods:

* Comparable valuations of similar projects (e.g., DeFi project market capitalization, conversion cap of a pre-seed web3 start-up)
* The [VC method](https://sharpsheets.io/blog/venture-capital-valuation-method/), where you back into the current valuation based on the exit value and your required rate of return
* The Berkus method, where you try to assign dollar amounts to intangibles like a high-quality team, a good idea, or strategic relationships
