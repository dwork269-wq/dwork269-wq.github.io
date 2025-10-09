---
title: "Quick Notes on the Terra and Anchor Whitepapers"
date: 2024-09-21
tags: [Crypto, Payments]
permalink: /notes-terra-money-anchor-protocol-whitepapers/
---

# Quick Notes on the Terra and Anchor Whitepapers

Exploring some stablecoin history today.

In this post, I jot down quick comments and immediate impressions while reading the Terra Money and Anchor Protocol whitepapers.

## Terra Money

### Instant Currency Swaps

> A user can swap TerraKRW for TerraUSD instantly at the effective KRW/USD exchange rate. This allows all Terra currencies to share liquidity and macroeconomic fluctuations; a fall in demand by one currency can quicky be absorbed by the others.

Key flaw in the assumption that a fall in demand can quickly be absorbed by the others? This assumes the integrity of the overall Terra ecosystem and that there are no net outflows from the system.

### Measuring Stability with Miner Oracles

> Since the price of Terra currencies in secondary markets is exogenous to the blockchain, the system must rely on a decentralized price oracle to estimate the true exchange rate. We define the mechanism for the price oracle as the following:
> For any Terra sub-currency in the set of currencies 𝐶 =TerraKRW, TerraUSD, TerraSDR, .., miners submit a vote for what they believe to be the current exchange rate in the target fiat asset.
> Every 𝑛 blocks, the vote is tallied by taking the weighted medians as the true rates.
> Some amount of Terra is rewarded to those who voted within 1 standard deviation of the elected median. Those who voted outside may be punished via slashing of their stakes. The ratio of those that are punished and rewarded may be calibrated by the system every vote to ensure that a sufficiently large portion of the miners vote.

Issues to consider:

- Median price may not always reflect true price
- If Terra loses its value, voters may be disincentivized to align with the true/median price
- Risk of voters colluding to coordinate on a false price

### Achieving Stability with Consistent Mining Rewards

> Once the system has detected that the price of a Terra currency has deviated from its peg, it must apply pressures to normalize the price. Like any other market, the Terra money market follows the simple rules of supply and demand for a pegged currency. That is:
> Contracting money supply, all conditions held equal, will result in higher relative currency price levels. That is, when price levels are falling below the target, reducing money supply sufficiently will return price levels to normalcy.
> Expanding money supply, all conditions held equal, will result in lower relative currency price levels. That is, when price levels are rising above the target, increasing money supply sufficiently will return price levels to normalcy.

Flaws:

- "All conditions held equal"
- Contracting/expanding money supply requires (1) leveraging reserves (2) minting. 1 has its limits, 2 doesn't necessarily stabilize price if buyers aren't interested in buying/selling anyway

I'm still confused with what the peg actually is!

### Luna's Stabilization Role

> Luna also serves as the most immediate defense against Terra price fluctuations. The system uses Luna to stabilize the price of Terra by agreeing to be the counterparty to anyone looking to swap Terra and Luna at Terra's target exchange rate. More concretely:

> When TerraSDR's price < 1 SDR, users and arbitragers can send 1 TerraSDR to the system and receive 1 SDR's worth of Luna.
> When TerraSDR's price > 1 SDR, users and arbitragers can send 1 SDR's worth of Luna to the system and receive 1 TerraSDR.

Flaws:

- Assumes Luna and Terra may not lose their values simultaneously
- Over-reliance on miners to stabilize/correct the system. But what if they exit? Without them, no reliable method to determine price either?

### Concluding Thoughts

After reading the paper, am I more confused than I should be?

Can't quite grasp what the system's fundamental peg is. It feels like a mathematical balancing act between Luna, Terra, and miners to stabilize values.

And without any circuit breakers in place!

---

## Anchor Protocol

### Cyclicality in DeFi

> Upswings in Ethereum's price increase demand for leveraged long positions on Ethereum, which results in increased borrowing from stablecoin money markets. The opposite is true during Ethereum price downswings: a decrease in leveraged long demand, in combination with liquidations of Ethereum debt positions, results in less stablecoin borrowing. See the Appendix for data on this pattern collected from the past 12 months of stablecoin borrowing on Compound. The interest rate equations demonstrate the cyclicality in utilization ration directly translates to cyclicality in borrower and depositor rates. We believe that cyclicality of interest rates on DeFi protocols is a key barrier to broad adoption.

This is interesting, but how about focusing yield farming on TradFi channels, to build trust and adoption for crypto (especially stablecoins), with a strong emphasis on price stabilization?

There seems to be a heavy focus on the utilization ratio (akin to TradFi bank reserve ratios). Feels risky - it might require constant artificial APY boosts.

### Anchor Rate Stability

> In the absence of a printing press, Anchor uses block rewards across blockchains to derive DeFi's benchmark rate. With Anchor, the return that depositors can expect is a function of borrowers' on-chain income. The Anchor money market is a unique enabler of "yield transfer" from borrower to depositor by accepting bAssets on collateral. The resulting diversified yield, the Anchor Rate, reflects the market's preferred sources of yield on the blockchain. For this reason the Anchor Rate has the potential to be more stable than any individual yield, or any fixed collection of yields.

Anchor says "market preferred yields" but isn't this just bull market interest rate arbitrage? borrow from anchor → buy crypto → stake for rewards → profit. If cryptos crashed, people would sell and deposit stablecoins in anchor for superior APY?

### Concluding Thoughts

Lesson I'm learning: Cryptos need to closely monitor yield farming activities involving their tokens. The APYs offered directly influence demand, which in turn affects the price of the crypto. Wonder how Yield Farming affects fiat pegged cryptos though 🤔
