---
title: "Mountain Protocol - USDM Questions and Ideas"
date: 2025-02-21
tags: [Crypto, Payments]
permalink: /mountain-protocol-usdm-questions-ideas/
---

# **Mountain Protocol - USDM Questions and Ideas**

This post presents **questions and thoughts** I have after reviewing the [Mountain Protocol Documentation](https://docs.mountainprotocol.com/). Additionally, I explore potential structural changes to USDM, big-picture implications of stablecoins, and future directions for Mountain Protocol.

---

## **30-Second TL;DR**

- **Should USDM's peg fluctuate based on yield rewards instead of staying at 1:1?** Could this simplify rebasing, change how users time their investments, and improve the coin's utility?
- **Are stablecoins really decentralized, or is everything still built on Traditional Finance?** Even algorithmic stablecoins rely on fiat-based stablecoins - so where does DeFi really begin?
- **What happens if the S&P 500 launches a stablecoin?** Wouldn't it be classified as a security? Aren't all yield-bearing stablecoins securities? Did Gary Gensler have a point?
- **Is Circle's USDC model extractive?** While inflation hurts holders, it benefits Circle's owners through superior yield - does USDM present a fairer alternative?
- **What's next for USDM?** Can it expand through **PSMs, LPs, and fiat on/off ramps** to become a superior base stablecoin?
- **How should USDM reserves be stress-tested?** Could a risk-hedging agent profit when stablecoins face crises like USDC's SVB depeg?

---

## **Table of Contents**

1. **[Yield & Market Dynamics](#yield--market-dynamics)**
2. **[Stablecoin Classifications & Systemic Risk](#stablecoin-classifications--systemic-risk)**
3. **[USDM's Future & Competitive Positioning](#usdm-future--competitive-positioning)**
4. **[Reserve Management & Stability](#reserve-management--stability)**

---

## **Yield & Market Dynamics** {#yield--market-dynamics}

_Should USDM's peg fluctuate with yield rewards? Would this affect user behavior, simplify rebasing, and improve integrations in LPs & PSMs?_

### **Should the Peg Fluctuate Instead of Minting New Tokens?** \

<div style="background-color: #f4f4f4; padding: 10px; border-radius: 5px;"> <em>
Right now, Mountain follows: **balanceOf(account)USDM = shares(account) \* rewardMultiplier** \
\
This means:**balanceOf(account)USD = balanceOf(account)USDM \* (USD/USDM peg)**, where USD/USDM peg is always 1:1 on Mountain's platform and held through arbitrage on secondary markets. \
\
But what if the peg fluctuates based on the rewardMultiplier? \
\
If we redefine the equation as **USD/USDM peg = rewardMultiplier**, \
\
Then, **balanceOf(account)USD = balanceOf(account)USDM_Proposed \* (USD/USDM peg).** \
\
Ensuring **balanceOf(account)USDM_Proposed = shares[account]**.
</em> </div>

- Right now, USDM uses a **1:1 peg**, with rewards distributed separately.
- Could rewards be **baked into the peg itself**, eliminating the need to mint new tokens?
- Would this **change how users time their purchases**—like wanting to buy into the S&P 500 earlier rather than later?
- Would it make **rebasing less technically complex**, especially for wUSDM?

### **Liquidity & Arbitrage Considerations**

- Would a **fluctuating peg make USDM easier to integrate into liquidity pools (LPs) and peg stability mechanisms (PSMs)?**
- If this system is too complex, could **another linked token** be created where the price fluctuates instead of USDM?

### **Low-Yield Environments**

- If **Treasury yields decline**, how does USDM remain attractive?
- Does Mountain expect circulation to **fluctuate with yield levels**, or are alternative strategies in place?

### **When is "Day 0" for USDM?**

- When exactly does **USDM's lifecycle begin**—is it the day it's minted, transferred, or reset with each transaction?

---

## **Stablecoin Classifications & Systemic Risk** {#stablecoin-classifications--systemic-risk}

_Are stablecoins actually decentralized, or is everything still dependent on TradFi? If major financial indices launched a stablecoin, would it be classified as a security?_

### **What if the S&P 500 Launched a Stablecoin?**

- Would it be classified as a **security**?
- How does this compare to **USDM's classification**?

### **Is DeFi Just Traditional Finance in Disguise?**

- Even **algorithmic stablecoins** ultimately rely on collateralized stablecoins.
- Are all stablecoins just **TradFi wrapped in a DeFi interface**?
- If **governments still back everything**, but **markets make the decisions**, is this the real definition of DeFi?
- Could current stablecoins **unlock efficiency gains**?

---

## **USDM's Future & Competitive Positioning** {#usdm-future--competitive-positioning}

_Can USDM replace USDC as a fairer stablecoin? What integrations (PSMs, LPs, fiat rails) will drive its long-term adoption?_

### **The Non-Extractive Model – A Better USDC?**

- USDM is **not extractive**, unlike USDC, where **Circle's owners pocket all the yield**.
- Circle **profits from inflation**—as **interest rates rise, its yield grows**, while USDC holders lose purchasing power.
- Wouldn't it be better if **USDM replaced USDC as the default stablecoin**?

### **What's Next for USDM?**

- Mountain seems focused on:
  - **Swap pools**
  - **Lending market integrations**
  - **PSMs for stablecoin swaps**
  - **LP adoption for yield farming**
- PSMs and LPs are **likely the core use cases**, while swaps & lending require **higher volumes** than USDM currently has.
- Expanding **native USDM on multiple blockchains** could accelerate adoption.

### **Fiat Rails & Diversification Beyond USDC**

- Can USDM **add fiat on/off ramps** to convert **fiat directly into USDM**? It might serve as a good use case for **[cross-border-payments](/best-use-case-cross-border-stablecoin-payments)**
- Should USDM **diversify beyond USDC**, given its **single point of failure risk**?
- Would this make **USDM a more sustainable base stablecoin**?

---

## **Reserve Management & Stability** {#reserve-management--stability}

_How does Mountain Protocol manage liquidity and risk? Can stress-testing stablecoins unlock new profit opportunities?_

### **Liquidity & Maturity Management**

- What processes and automations does Mountain Protocol use to manage the **weighted average maturity (WAM) and weighted average life (WAL)** of USDM reserves?
- What does the **USDM minting-to-reserves workflow** look like?

### **Reserves Attestation & Stress-Testing Risks**

- Could a new **risk-hedging agent** profit by arbitraging stablecoin depegs?
- For example, if USDC **loses its peg due to a banking crisis**, could this agent **trade around such events?**
- Can this agent detect **interlinked risks**, like USDM holding USDC, which in turn may rely on the same banks as USDM's reserves?
- Could **[DebtCoin](/the-debtcoin-token)** hedge against **U.S. debt servicing risks** in the unlikely case of government defaults?

---

## **Final Thoughts**

Stablecoins are evolving, and USDM is proof that there's plenty of room for innovation beyond USDC and USDT!

---
