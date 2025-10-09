---
title: "Quick Notes on BVNK Embedded Stablecoin Payouts"
date: 2025-02-11
tags: [Crypto, Payments]
permalink: /quick-thoughts-on-bvnk-embedded-stablecoin-payouts/
---

Fiddled around with BVNK's [developer sandbox](https://signup.sandbox.bvnk.com/create-dev-account) today and went through their developer documentation. They seem to have released an embedded stablecoin payouts feature, which caught my interest given my focus on payments and stablecoins.

Jotting down quick points I'd like to clarify.

## Adoption and Ecosystem Growth

- **Stablecoin Adoption and Yield Farming**: If stablecoin adoption grows, could this feature support more efficient account management via low-risk yield farming operators? That could boost adoption.
- **New Customer Acquisition**: Is this feature built to retain BVNK's existing customers (if so, are they increasing platform fees or relying on greater fees through increased transaction volumes)? Or are they actively targeting new customer segments?
  -- I imagine businesses in currency-volatile countries would be key targets?
- **Multi-Stablecoin Support**: Will BVNK eventually allow support for multiple stablecoins? That seems like a logical next step, if their customers want it.

## Regulation/Resilience

- **Regulatory Shifts**: Stablecoin regulations seem to be evolving. What happens to this feature when shifts occur? Has this been built keeping changes in mind?
- **Resilience**: During events like the SVB collapse when USDC depegged, how would this system handle payouts? Could stablecoin payments continue, or would it disrupt the flow entirely?

## Feature-Specific Questions

- **Settlement Speeds**: Curious about how fast these transactions settle. Faster than fiat? If so, I'd like to know what the tipping point for transaction times is for businesses to switch from fiat to stablecoin payments.
- **Stablecoin Purchases**: How are stablecoins being purchased? Are they working directly with Circle Mint or through third parties?
- **Tax and Reporting**: I didn't see any tax/reporting/analytics tool integrations on the developer sandbox. Are these supported? Most businesses I've worked with would want these features for compliance and financial tracking.
- **Compliance**: BVNK's recent features seem heavily focused on EU compliance? Wondering how much of their time and resources are going into this compared to other priorities.
- **KYC/KYB Pain Points**: KYC/KYB can be a real headache. How does BVNK streamline this for their EPs and EPCs? Are the flows any different for stablecoins?

## Role Distinctions

I'm a bit confused about the distinctions between Embedded Partner (EP), Embedded Partner Customer (EPC), and End User. Here's how I currently understand it:

- EP: I think of this as DoorDash, integrating BVNK's payments into their platform.
- EPC: A restaurant listed on DoorDash (would this also be listed in the Merchants section of the platform?).
- End User: A customer ordering food through DoorDash.

This framework started making sense when I saw that payout requests come through the EP, and the EPC only gets their share after BVNK performs the USD-to-USDC exchange. Still not entirely sure, though.

## Metrics!

Standard PM stuff:

- New EPCs/EPs onboarded
- Total transaction volumes
- Average transaction times
- Drop-off and failed payment rates
