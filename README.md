# Awesome-Embedded-B2B-Payment-Processing

# Awesome-Embedded-B2B-Payment-Processing

**Top Embedded B2B Payment Processing (Opensource) 🌟 Star if you like it! 🌟**



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Platform Payments, Multi-Party Payouts, Bank Transfers & Self-Hosted Payment Infrastructure*

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Embedded B2B Payment Processing**. These tools enable platforms, marketplaces, and SaaS products to embed payments directly into their product—handling onboarding, split payouts, compliance, and money movement without becoming a payment processor themselves—from fully managed platforms with KYC/AML built in to open-source payment APIs that give developers complete control over their ledger and settlement.



**Examples** include Stripe Connect, Adyen for Platforms, Moov, Dwolla, Finix, Plaid, Helcim, Melio, HubSpot Payments, and PayPal B2B (the category leaders in commercial space).



**Open-source emphasis**: This section is expanded with every relevant project for self-hosted payment infrastructure, ledgers, and open B2B protocols. **Critical note**: True open-source embedded B2B payment processing is extremely sparse—**TPT Pay** is the only self-hostable Stripe-compatible payment API with a double-entry ledger, but it requires a card network adapter for production . **BCP** defines a B2B agent commerce protocol on x402, but it is a draft specification, not a production payment processor . No open-source project matches Stripe Connect's onboarding, compliance, or global payout network.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **Stripe Connect**

  **Platform payments infrastructure** for marketplaces and SaaS. **Pricing**: If Stripe handles seller pricing, **no Connect fees**—Stripe charges sellers directly. If you set your own pricing, **$2 per monthly active account** plus **0.25% + 25¢ per payout** (US, Oct 2026); **instant payouts 1%**; card processing **2.9% + 30¢** domestic, **+1.5% international**, **+1% currency conversion** . **Free tier**: No platform fees if Stripe handles pricing. **Best for**: marketplaces and platforms wanting the most mature embedded payments stack with flexible account models (Accounts v2)—**trade-off**: fee stacking can consume >25% of commission on low-value transactions .



- **Adyen for Platforms**

  **Enterprise financial operating system** for platforms and marketplaces. **Pricing**: Quote-only; take-rate dilution noted as blended take rate falls (~0.6 bps YoY) as platform volume grows . **Free tier**: None. **Best for**: large platforms wanting unified commerce and financial OS capabilities (loyalty, usage-based billing via Orb, agentic payments)—**trade-off**: enterprise sales-led; take-rate compression at scale.



- **Moov**

  **Developer-first payment API** with transparent pricing. **Pricing**: **$500 monthly minimum**; card payments **Interchange+ + 0.60% + 15¢** (US); **instant payments 0.95%** (50¢ min, $5 cap); **ACH 40¢**; **KYB $4.50/business**, **KYC $2.50/individual** (+$0.50/month) . **Free tier**: None. **Best for**: technical teams wanting full-stack money movement with published interchange-plus rates—**trade-off**: monthly minimum excludes low-volume platforms.



- **Dwolla**

  **Bank payment API** for platforms and enterprises. **Pricing**: **Volume-based, quote-only**—per-transaction cost decreases with volume; no per-API-call charges; ACH, same-day ACH, RTP, and FedNow included without extra rail fees . **Free tier**: None. **Best for**: platforms running high-volume bank payments wanting predictable, volume-scaled pricing—**trade-off**: no self-serve pricing; sales-led evaluation.



- **Finix**

  **Payment processing for platforms** with Invoices (Early Access). **Pricing**: **Invoices: 0.10% per successful transaction** during early access; **standard rate rises to 0.40% from July 1, 2026** . **Free tier**: None. **Best for**: platforms wanting a processor-agnostic stack with invoice payments—**trade-off**: invoice pricing increasing; broader pricing quote-only.



- **Plaid**

  **Bank data and payments infrastructure**. **Pricing**: **Subscription-based**—charged monthly even if no API calls are made; **not pro-rated** for mid-month Items . **Free tier**: Trial available. **Best for**: platforms needing bank account verification and balance checks before B2B payments—**trade-off**: subscription billing persists for active Items regardless of usage; delete unused Items promptly.



- **Helcim**

  **Interchange-plus payment processor** for SMBs. **Pricing**: **No monthly fee, no contract**; in-person **Interchange + 0.40% + 8¢** (≤$50K/month), falling with volume; **online/invoice Interchange + 0.50% + 25¢**; **Tap to Pay +10¢/transaction** . **Free tier**: Yes, no monthly fee. **Best for**: SMBs wanting transparent interchange-plus pricing without monthly commitments—**trade-off**: total cost depends on card mix; no enterprise platform features.



- **Melio**

  **B2B bill payments platform**. **Pricing**: **Free ACH payments** each month, **$0.50 per additional ACH**; premium plans **$22–$68/month** + $10/additional user . **Free tier**: Yes, free ACH allowance. **Best for**: SMBs wanting to pay vendors via ACH with cash-flow flexibility—**trade-off**: not an embedded payment API; more of a standalone AP tool.



- **HubSpot Payments**

  **Payments within HubSpot** ecosystem. **Pricing**: **0.5% platform fee** per transaction (vs. **0.75% for Stripe** processing within HubSpot) plus standard card fees . **Free tier**: Limited. **Best for**: HubSpot users wanting native payments with lower platform fee than Stripe—**trade-off**: HubSpot ecosystem lock-in.



- **PayPal B2B**

  **PayPal business payments** with invoicing and cross-border. **Pricing**: **4.4% + fixed fee** per international transaction + **3–4% FX markup** (India example; effective cost 5–8%) . **Free tier**: None. **Best for**: businesses already in PayPal ecosystem—**trade-off**: among the highest effective rates for cross-border B2B.



## Open-Source GitHub Projects



- **TPT Pay (TPT Platform)**

  **Open-source, self-hostable Stripe alternative** (MIT) — **the only open-source payment API with a double-entry ledger and Stripe-compatible REST API**, built in Go . **Features**: **Stripe API v2024-06-20 compatible**—drop-in replacement for existing Stripe integrations; **append-only double-entry ledger** in PostgreSQL for financial integrity; **webhook engine** via NATS JetStream; **HashiCorp Vault** for card tokenization and API key encryption; **CardNetworkAdapter** interface—ships with `SandboxAdapter` for testing; plug in `BankSponsorAdapter` or `DirectAcquiringAdapter` for production; **merchant dashboard** (Next.js) and **JS/Python SDKs** . **Tech stack**: Go, PostgreSQL, Redis, NATS, Vault. **Deploy**: Self-hosted (Docker Compose). **Trade-off**: **No production card acquiring path shipped**—sandbox only; requires bank sponsor or direct acquiring integration for live payments. **Best for**: developers wanting a Stripe-compatible payment API foundation they can self-host and extend—**not for production without a card network adapter**.



- **BCP (Business Commerce Protocol)**

  **Open-source B2B agent commerce protocol on x402** (Apache 2.0, Draft v0.1) — **the most forward-looking open-source B2B payment specification**, defining structured commerce conversations between AI agents . **Features**: **Message types**—INTENT, QUOTE, COUNTER, COMMIT, FULFIL, DISPUTE; **state machine** for negotiation lifecycle; **on-chain escrow** (BCPEscrow.sol) for ETH/ERC-20; **x402 bridge** for stablecoin settlement; **UBL 2.1 invoice generation**; **Ed25519 signatures** for message authentication . **Tech stack**: TypeScript, Solidity, x402 (Coinbase). **Deploy**: Self-hosted (npm). **Trade-off**: **Draft specification, not production**—no compliance, KYC, or fiat rails; stablecoin-only settlement. **Best for**: developers exploring agent-to-agent B2B commerce with programmable escrow—**not a Stripe Connect replacement**.



### Additional Strong Open-Source Options



- **No mature open-source embedded B2B payment platform exists.** Stripe Connect, Adyen, Moov, Dwolla, and Finix are proprietary. **TPT Pay** provides a payment API foundation but requires acquiring integration. **BCP** defines a protocol but not a processor. **For production B2B payments, commercial platforms are required.**



**Frameworks for building custom systems**: **TPT Pay** is the only functional open-source starting point for self-hosted payment APIs. **BCP** provides a protocol reference for agentic B2B commerce. **None of these match Stripe Connect's onboarding, compliance, or global payout network.**



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, license (for open-source), and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Embedded B2B payment platforms handling money movement and compliance must comply with **PCI DSS**, **KYC/AML** regulations, and money transmitter licensing requirements. **Open-source tools do not provide compliance**—you must obtain your own licenses or partner with a licensed sponsor.

- **The "platform payments" vs. "bank payment API" vs. "processor" vs. "payment protocol" distinction is critical.** **Stripe Connect, Adyen for Platforms, and Finix** are **platform payments**—they handle onboarding, split payouts, and compliance for marketplaces . **Moov and Dwolla** are **payment APIs**—they provide the rails (cards, ACH, RTP) but you build the platform logic . **Plaid** is **bank data infrastructure**—it verifies accounts and balances, not moves money . **TPT Pay** is a **payment API foundation**—self-hosted but requires acquiring integration . **BCP** is a **payment protocol**—it defines agent commerce messages, not a processor . **Choose based on whether you need managed compliance, raw rails, bank data, or a protocol.**

- **Stripe Connect's fee structure is conditional.** If Stripe handles seller pricing, **no platform Connect fees**—Stripe charges sellers directly . If you set pricing, **$2/monthly active account + 0.25% + 25¢ per payout** stacks on top of card processing. **A 15% commission on $50 bookings can see >25% consumed by payment and Connect fees** . **Model your commission against fee stack before committing.**

- **Moov's $500 monthly minimum** excludes low-volume platforms. **Interchange-plus pricing is transparent**—card payments at **Interchange+ + 0.60% + 15¢**—but the minimum requires volume to justify .

- **Dwolla's pricing is volume-based and quote-only.** No per-API-call charges; all rails (ACH, RTP, FedNow) included without extra fees . **For high-volume bank payments, it is the most predictable model—but evaluation requires sales.**

- **Plaid's subscription billing persists even with zero API calls.** Active Items are billed monthly regardless of usage; mid-month Items are not pro-rated . **Delete unused Items promptly to avoid indefinite billing.**

- **Helcim is the only processor with no monthly fee and published interchange-plus rates**—in-person **Interchange + 0.40% + 8¢**, online **+ 0.50% + 25¢** . **The trade-off**: total cost depends on card mix; not a platform payments solution.

- **HubSpot Payments is cheaper than Stripe within HubSpot**—**0.5% platform fee vs. 0.75%** . **For HubSpot users processing payments, it is a straightforward cost reduction.**

- **PayPal B2B is the most expensive option for cross-border**—**4.4% + fixed fee + 3–4% FX markup**, effective **5–8%** on India receipts . **Avoid for high-volume international B2B.**

- Self-hosted open-source solutions require proper infrastructure (PostgreSQL, Vault, NATS for TPT Pay), security hardening, and **licensed acquiring relationships**. **Payment APIs handle money and card data**—ensure your deployment meets PCI DSS requirements and your organization's compliance standards before processing live transactions.



---



**Made for platform engineers, fintech developers, and organizations building transparent embedded payment solutions.**

Let's make Embedded B2B Payment Processing more open, data-driven, and platform-friendly.
