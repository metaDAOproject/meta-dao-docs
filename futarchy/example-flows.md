---
description: Some example flows that demonstrate how the Meta-DAO will work in practice
---

# Example flows

### Example #1 - A bad proposal <a href="#example-1---a-bad-proposal" id="example-1---a-bad-proposal"></a>

Governance attacks, like [the one launched against Beanstalk Protocol](https://medium.com/immunefi/hack-analysis-beanstalk-governance-attack-april-2022-f42788fc821e), are relatively uncommon but do happen. It’s worth considering how the Meta-DAO would respond to such an attack. Suppose that an attacker has just submitted a proposal that transfer’s all of the Meta-DAO’s assets to himself. How is the community incentivized to respond?

Well, if the proposal goes through, the Meta-DAO will be worth a lot less. For example, if the Meta-DAO is currently worth $100M and the proposal would transfer $40M of the Meta-DAO’s liquid assets, then it should be worth $60M if the proposal goes through.

So if you hold META and its current price is $1, you are incentivized to mint conditional-on-pass tokens and sell them until their market price reaches $0.6. On the other hand, the conditional-on-fail tokens should trade near $1. As such, autocrat should fail this proposal.

Once autocrat fails the proposal, all trades in the conditional-on-pass market become reverted and all trades in the conditional-on-fail market become finalized.

### &#x20;Example #2 - A good proposal <a href="#example-2---a-good-proposal" id="example-2---a-good-proposal"></a>

Now consider what should happen when a good proposal emerges. Suppose that someone has just made a proposal to fund a project that would improve a product that the Meta-DAO manages. The proposal is requesting $5M paid over 2 years and analysts estimate that the improvements would add $25M to the Meta-DAO’s [enterprise value](https://en.wikipedia.org/wiki/Enterprise\_value), so the proposal would on net create $20M of value.

[Economically rational](https://www.britannica.com/money/topic/economic-rationality) participants would then be incentivized to bid up META in the conditional-on-pass markets until its price reaches $1.2. If the price dips lower, say to $1.1, this represents a bargain opportunity: participants can buy $1.2 of [net present value](https://en.wikipedia.org/wiki/Net\_present\_value) for only $1.1! Traders would be likely to take this trade until the price reached a level near $1.2 again. But again, the proposal would have no impact on the Meta-DAO if it were to fail, so we would expect META to trade near $1 in the conditional-on-fail markets. So autocrat would pass this proposal.
