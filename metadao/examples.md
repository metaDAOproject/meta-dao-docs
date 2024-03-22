---
description: Some example flows that demonstrate how MetaDAO works in practice
---

# 💻 Examples

### Example #1 - A bad proposal

Suppose that an attacker has just submitted a proposal that transfer’s all of MetaDAO’s assets to himself. How is the community incentivized to respond?

Well, if the proposal goes through, MetaDAO will be worth a lot less. Let's suppose that there are 100 million META in existence, the price per META is $1, and MetaDAO controls $40M of assets in its treasury. Then this proposal would decrease the value of META by \~40%.

So if you hold META and its spot price is $1, you are incentivized to mint conditional-on-pass META and sell it until its price reaches 0.6 conditional-on-pass USDC. On the other hand, the conditional-on-fail META should trade near 1 conditional-on-fail USDC. As such, autocrat should fail this proposal.

### &#x20;Example #2 - A good proposal <a href="#example-2---a-good-proposal" id="example-2---a-good-proposal"></a>

Now suppose that someone has just made a good proposal - a proposal to fund a project that would improve a MetaDAO-managed product. The proposal is requesting $5M paid over 2 years and analysts estimate that the improvements would add $25M to MetaDAO’s [enterprise value](https://en.wikipedia.org/wiki/Enterprise\_value), so the proposal would on net create $20M of value.

If META had a supply of 100 million and spot price of $1, traders would be incentivized to bid up conditional-on-pass META until its price reaches 1.2 conditional-on-pass USDC. If the price dips lower, say to 1.1 conditional-on-pass USDC, this represents a bargain opportunity: participants can buy $1.2 of [net present value](https://en.wikipedia.org/wiki/Net\_present\_value) for only $1.1! The proposal would create no value for MetaDAO if it failed, so we would expect conditional-on-fail META to trade near 1 conditional-on-fail USDC. That being the case, autocrat would pass this proposal.
