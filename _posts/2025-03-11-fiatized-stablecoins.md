---
title: "Fiatized Stablecoins"
date: 2025-03-11
tags: [Crypto, Payments]
permalink: /fiatized-stablecoins/
---

There's been a transition in the crypto space from decentralized currencies like Bitcoin to fiat-pegged stablecoins. We're now witnessing the next transition - what I call the shift from "extractive" stablecoins (where a rise in inflation raises the yield on these coins, enriching the issuers while making holders poorer) to yield-bearing stablecoins. I believe we're only at the beginning of this shift and that this might just be the major crypto breakthrough that brings it into mainstream banking.

Stablecoins function similarly to ETFs in that they have separate layers for reserves and crypto protocols. The reserves are typically managed and invested in cash and treasuries, while smart contracts facilitate the minting and burning of tokens. These two layers are connected through careful liquidation processes and mechanisms.

The problem with stablecoins though is that they remain too technical for the average user.

I've been thinking of something I call "fiatized stablecoins" (as opposed to tokenized assets or deposits) to further bring the advantages of crypto into the mainstream. I don't particularly care about most developments in the crypto space - they're fun to analyze, but beyond that, what I'm personally driven by is crypto's potential to prevent median wealth erosion due to inflation, a challenge that societies, both rich and developing, constantly face.

To illustrate fiatized stablecoins, let's consider a mobile app called "Simple".

Consider this user flow:

### User Interacts with App

- The user initiates an action (e.g., deposit, withdrawal, transaction).

### App Interacts with Simple's Fiat Bank Account

- The app executes the user's actions and connects to a fiat bank account owned by Simple.
- This can involve ACH, wire transfers, or card payments.

### Simple Interacts with Stablecoin Protocol

- Simple owns a crypto wallet (or a set of crypto wallets, whichever is more secure from an operational standpoint) that has access to a yield-bearing stablecoin's protocol layer – let's use Mountain's USDM as an example, a crypto [I'm personally a fan of](/mountain-protocol-usdm-questions-ideas).
- Simple can interact directly with the stablecoin issuer to mint or burn stablecoins as needed.

### Stablecoin Issuer Manages Reserves

- The stablecoin issuer (e.g., Mountain) independently manages underlying fiat reserves, compliance and redemption processes, ensuring that all circulating stablecoins (and therefore, all Simple's fiat deposits) are properly backed.

Essentially, just as stablecoin issuers centrally operate reserves that are invested in treasuries, Simple will centrally operate the wallet that interacts with the stablecoin protocol. Simple's fiat money management can be optimized through streamlined batching and settlements. If Simple ensures that it always has more stablecoins in its crypto wallet than circulating fiat, it should have room to slow down settlements in favor of quicker user deposits/withdrawals.

**The idea is to therefore have a fiat layer on top of the stablecoin layer, which itself sits on top of another fiat layer—bringing it as close to the regular end-user as possible.** Picture an app that allows users to buy stablecoins with their cards and bank accounts. I've shared a few basic prototype screenshots so I could visualize this concept.

![Screenshot 1]({{ "/assets/img/22.Screenshot1.png" | relative_url | uri_escape }})
![Screenshot 2]({{ "/assets/img/22.Screenshot2.png" | relative_url | uri_escape }})
![Screenshot 3]({{ "/assets/img/22.Screenshot3.png" | relative_url | uri_escape }})

## Why does this matter?

Whatever crypto's promise has been, it hasn't succeeded in widespread adoption simply because it is too complex (note: institutional adoption isn't the same as widespread adoption). The biggest crypto successes haven't necessarily been decentralized. In fact, 80% of all crypto transactions happen with stablecoins, suggesting that crypto is perhaps more linked to government actions than ever before. It's also telling that the most successful companies in the space haven't been decentralized entities but centralized firms that offer a certain level of trust-Coinbase, Circle, etc.

I argue that the key differentiator in the crypto space, just like in the rest of the world, comes down to trust and simple design. Which is why I believe an app that keeps all the complexities of crypto under the hood - with no mention of wallets or chains - could be a breakthrough. The goal is to target regular banking users who simply want low-risk, better yields on their daily expenses and who might be more likely to replace their checking and savings accounts with Simple.

While the rebasing mechanism would ensure that the value of their money increases, if Simple's wallet can engage a tiny portion of its tokens in DeFi staking, the money earned could potentially exceed the actual rebasing yield of the stablecoin.

## Regulatory Concerns

The challenge with this approach is that it blurs the lines between HYSA neobanks and stablecoins. A service like Simple is almost indistinguishable from a high-yield savings account. The differentiation will ultimately come down to policy.
Governments have yet to classify yield-bearing stablecoins as securities. It therefore is difficult to categorize an app like Simple as a security since it only interacts with stablecoins. However, it also doesn't fully escape the Howey Test, as there is a clear expectation of profit.

Moreover, for a fiatized stablecoin like Simple,

- Are we a fintech company like Chime?
- Are we a Money Services Business (MSB) like Circle?
- What registrations would we need - FinCEN, SEC, FINRA, FDIC?

I believe there is something here and I want to explore it further. If you have thoughts or more information, let me know.
