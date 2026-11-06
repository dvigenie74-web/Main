# Alternatives to TBC Bank for accepting international online payments (Georgian IE / LLC)

Research date: 2026-11-06. Method note: WebFetch was blocked in this session for flitt.com, payze.io, quickpay.ge and insights.ge (hosts not allowed by the network), so every finding below comes from WebSearch result summaries and snippets. Full pages were NOT read. Figures should be re-checked on the official pages before they go into the final report. Source dates are given where the search exposed them.

## Q1. Per-provider facts: availability for IE/LLC, foreign owners, international cards, Apple/Google Pay, links, subscriptions, fees, payouts, onboarding, integrations

### Takeaway
Among local providers, Bank of Georgia (BOG) is the main independent bank alternative to TBC, at about 2% for local cards and 2.8-3.5% for international cards (third-party figures). Flitt is not an independent alternative: it is part of TBC Group and requires an active TBC business account. Payze has stopped onboarding entirely. UniPAY (built on Liberty Bank acquiring) and Keepz (built on Credo acquiring) are smaller PSP options. Among foreign options, Stripe is unavailable to a Georgian entity, and an Estonian e-residency company does not fix that for a Georgia-resident owner. Paddle appears to accept Georgian sellers, Lemon Squeezy bank payouts do not cover Georgia, and Wise and Payoneer receive transfers but do not run a card checkout.

### Cited Findings

**Bank of Georgia (iPay / BOG Payments, api.bog.ge)**
- api.bog.ge bundles card payment, internet banking, PLUS/MR loyalty points, Apple Pay and online installments behind one integration. The source article is about 4 years old (circa 2022). — [CBW](https://cbw.ge/business/bank-of-georgia-is-creating-4-new-technological-and-innovative-services-to-support-business); [BOG API Marketplace mirror](https://context7.com/websites/api_bog_ge_en)
- Fees, integrator page 1: 2.0-2.5% for local cards and 2.8-3.2% for international cards. Setup is free for BOG business account holders. — [Craftwebstudio, BOG iPay](https://craftwebstudio.ge/en/integrations/bog-ipay)
- Fees, integrator page 2: 2% (minimum 0.10 GEL) for Georgian Visa/Mastercard and 3.5% (minimum 0.15 GEL) for Amex credit/rewards cards. It attributes the figures to BOG's business site. This conflicts with page 1 on international rates. — [Integrals.ge](https://www.integrals.ge/en/integrations/bogpay)
- A Russian-language blog says BOG serves any legal entity or IE with no minimum turnover, funds arrive within minutes, and the fee is 2%. The post is undated, possibly 2023-2024. — [nlevshits.com](https://nlevshits.com/kak-i-ot-kogo-mozhno-podklyuchit-sistemu-platezhej-dlya-biznesa-v-gruzii/)
- Counter-anecdote from a forum: BOG approval for a foreign IE "tends to zero", the process is long and document-heavy, and the user was refused. Other users say TBC and BOG offered acceptance of Georgian cards only. These threads are old, roughly 1.5-4.5 years. — [TravelAsk thread 1](https://travelask.ru/questions/4657101_ge_otkryl-ip-v-gruzii-ochen-nuzhen-onlayn-ekvayring-kart-ne-mog); [TravelAsk thread 2](https://travelask.ru/questions/2747368_ge_vsem-privet-te-u-kogo-est-ip-v-gruzii-delali-li-vy-internet)
- WooCommerce: the Plug&Pay "BOG Aggregator" plugin supports Apple Pay and Google Pay, but the iPay and iPay Solo gateways do not. BOG must enable the wallets on its side first. Pre-authorization is supported. The sandbox handles cards only. — [Plug&Pay docs](https://docs.plugandpay.ge/woocommerce/credit-card/bog); [Plug&Pay Apple Pay plugin](https://plugandpay.ge/product/woocommerce-bog-apple-pay-payment-gateway/)
- A community PHP library exists (invays/bog-payments). — [Packagist](https://packagist.org/packages/invays/bog-payments)
- Third-party guides describe the onboarding flow as business account, then e-commerce merchant ID application, then sandbox credentials, then webhooks, then production. API docs are reportedly obtained through onboarding. — [search summary of integrator guides incl. Craftwebstudio](https://craftwebstudio.ge/en/integrations/bog-ipay)

**Flitt (formerly Fondy in Georgia)**
- Flitt's About page calls it "a fintech company under the TBC Group". Gappsy says it is operated by TPAY LLC, a licensed PSP backed by TBC. — [Flitt About](https://flitt.com/about-us/); [Gappsy review](https://www.gappsy.com/tools/flitt/)
- "An active TBC bank account is required to use Flitt's services" (Flitt site/FAQ). Eligibility is a registered LLC or IE in Georgia with a TBC business account plus a separate Flitt agreement. — [Flitt FAQ](https://flitt.com/faq/); [Flitt pricing](https://flitt.com/pricing/)
- Published pricing: 2.2% for 0-10,000 GEL per month, 2.0% for 10,000-50,000 GEL, custom above that. International cards are 2.5%. Open banking is up to 1%. A 4-month split/BNPL is funded by TBC at no extra commission. Quickpay calls Flitt the only Georgian provider with a fully published rate card. — [Flitt pricing](https://flitt.com/pricing/); [Quickpay comparison 2026](https://quickpay.ge/en/blog/georgian-payment-gateways-comparison); [nlevshits.com](https://nlevshits.com/kak-i-ot-kogo-mozhno-podklyuchit-sistemu-platezhej-dlya-biznesa-v-gruzii/)
- Payment methods: Apple Pay, Google Pay and cards come with one integration. Features include pay-by-link, subscriptions/recurring and payouts. — [Flitt international payments blog](https://flitt.com/blog/simple-and-versatile-international-payments-platform/); [Flitt subscriptions](https://flitt.com/subscription-payments/); [Gappsy](https://www.gappsy.com/tools/flitt/)
- Integrations: Shopify, Wix, WooCommerce, Tilda and more. — [Flitt FAQ](https://flitt.com/faq/); [Quickpay Flitt module](https://quickpay.ge/en/modules/flitt)
- Installments: TBC is live, and Credo, Liberty and BOG are listed as "coming soon". — [Flitt FAQ](https://flitt.com/faq/)

**Payze**
- Payze's own site says it is no longer operating in Georgia and is not onboarding new clients globally. Wix removed Payze as a provider in July 2024. — [Payze FAQ](https://payze.io/en/faq); [Wix support](https://support.wix.com/en/article/connecting-payze-as-a-payment-provider); [PaymentPop 2026](https://paymentpop.com/merchant-accounts/payze-reviews/)
- Historical figures: 2.5-3% depending on card origin (Bitrix24 listing, circa 2022) and 2.7% per successful purchase (Russian blog). One Russian user was accepted only after paying a 500 GEL deposit, after refusals elsewhere linked to Russian citizenship. — [Bitrix24](https://www.bitrix24.com/apps/app/11176606.payzenew/); [nlevshits.com](https://nlevshits.com/kak-i-ot-kogo-mozhno-podklyuchit-sistemu-platezhej-dlya-biznesa-v-gruzii/); [Boot and Pencil blog](https://bootandpencil.com/blog/%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82-%D1%8D%D0%BA%D0%B2%D0%B0%D0%B9%D1%80%D0%B8%D0%BD%D0%B3-%D0%B2-%D0%B3%D1%80%D1%83%D0%B7%D0%B8%D0%B8/)

**Keepz**
- Keepz POS page: no monthly fee, commission "from 0.5%" depending on the payment rail, the commission can be passed to the payer, and payment links are offered. — [Keepz app](https://app.keepz.me/?lng=en)
- Quickpay's Keepz module lists international cards at 2.5% and domestic cards at 2.5% for 0-10,000 GEL. This is a reseller figure. — [Quickpay Keepz](https://quickpay.ge/en/modules/keepz)
- Card acquiring behind Keepz runs through Credo Bank. Credo's "Keepz QR Terminal" carries no POS commission, with a 3,000 GEL turnover limit after registration for individuals and IEs. That is an offline QR product, not e-commerce. — [Credo Keepz QR](https://credobank.ge/en/services/keepz-qr-terminal); [Quickpay comparison](https://quickpay.ge/en/blog/georgian-payment-gateways-comparison)
- No independent reviews of Keepz e-commerce use by foreigners were found. — [nlevshits.com search result](https://nlevshits.com/kak-i-ot-kogo-mozhno-podklyuchit-sistemu-platezhej-dlya-biznesa-v-gruzii/)

**UniPAY**
- Wix integration page: 2.5% + 0.25 GEL per transaction, no setup fee, 1 GEL minimum. — [Wix support, UniPAY](https://support.wix.com/en/article/connecting-unipay-georgia-as-a-payment-provider)
- UniPAY pricing page (about 15 months old): domestic cards have a one-time 48 GEL fee, Apple Pay/Google Pay are 2.5% + 0.25 GEL, and foreign-issued Visa/MC are 4.0% + 0.35 GEL. It processes GEL, USD and EUR. The homepage shows different splits (3.0% + 0.35 domestic vs 2.5% + 0.25 international), so UniPAY's own pages are inconsistent. — [UniPAY pricing](https://unipay.com/pricing/); [UniPAY](https://unipay.com/)
- UniPAY supports recurring/subscription payments, and Shopify and Wix integrations exist. — [CartDNA Shopify guide](https://www.cartdna.com/shopify-payment-methods/UniPay); [UniPAY Wix integration](https://support.unipay.com/article/wix-integration)
- UniPAY sits on top of Liberty Bank acquiring. — [Quickpay comparison](https://quickpay.ge/en/blog/georgian-payment-gateways-comparison)

**Liberty Bank**
- Its e-commerce service accepts Visa, Mastercard, UnionPay and local cards with 3D Secure. Integration is free, there is a discounted rate on Liberty/partner-bank cards, setup takes "a few days", the application is by form, and support is at MerchantSupport@lb.ge. The T&C are dated 21 March 2024. — [Liberty e-commerce](https://libertybank.ge/en/produqtebi/chemi-biznesistvis/distantsiuri-momsakhureba/e-commerce); [Liberty T&C PDF](https://cdn.lb.ge/libertybank/files/02/49/41/cX9vjrw7CE6ZfjCruJ934g/v6-e-commerce-service-agreement-tc_21032024-eng-clean.pdf)
- A single source reports that Basisbank (Hualing Group) acquired about 96% of Liberty in April 2026 and that both banks remain separately licensed. This is unverified. — [Relocation.ge 2026](https://relocation.ge/en/list-of-banks-in-georgia/)

**Credo Bank**
- No Credo-branded e-commerce fee or onboarding page was found. Credo is the acquirer behind Keepz and offers installments that Keepz can trigger. — [Quickpay comparison](https://quickpay.ge/en/blog/georgian-payment-gateways-comparison); [Credo Keepz QR](https://credobank.ge/en/services/keepz-qr-terminal)

**Aggregator: Quickpay.ge**
- It offers acceptance through BOG, TBC, Credo and other Georgian banks with one integration, plus WooCommerce modules. — [Quickpay.ge](https://quickpay.ge/en)

**Stripe**
- Georgia is not a supported Stripe country. A Georgian ID, Georgian company or GEL account cannot open a standard Stripe account. — [Legal Vista 2026](https://legal-vista.com/georgia-ie-receive-payments-stripe-wise-paypal); [StartGlobal 2026](https://startglobal.co/us/international/georgia/stripe/); [AgentaOS 2026](https://agentaos.ai/answers/which-countries-does-stripe-not-support)
- Stripe's own help page supports Estonian e-residency companies, but the individuals on the account must live in a Stripe-supported country. This blocks the Estonia route for a Georgia-resident owner. The same page points unsupported-country founders to Stripe Atlas (US company). — [Stripe Support](https://support.stripe.com/questions/supporting-companies-that-registered-in-estonia-through-e-residency)
- Legarithm (a vendor) claims the Estonian OÜ route works. This conflicts with Stripe's help page and is unverified. — [Legarithm](https://legarithm.io/estonia/blog/stripe-unsupported-country/)

**PayPal**
- PayPal's developer documentation lists Georgia as "Send, receive, and withdraw". — [PayPal developer: countries](https://developer.paypal.com/payouts/supported-features)
- Third-party sources conflict. Some say withdrawal works only to a Visa card (not Mastercard, not a bank account) and that reports are mixed. Others say Georgia is "sending only" or limited for business receiving. — [Legal Vista 2026](https://legal-vista.com/georgia-ie-receive-payments-stripe-wise-paypal); [CS-Cart](https://www.cs-cart.com/blog/paypal-countries-availability/); [Skydo](https://www.skydo.com/people-ask/does-paypal-work-in-georgia); [StartGlobal PayPal 2026](https://startglobal.co/us/international/georgia/paypal/)
- Register-company.ge says a PayPal balance can be withdrawn to a Georgian card. — [Register-Company.ge](https://register-company.ge/blog/payment-processors-georgian-company/)

**Paddle / Lemon Squeezy / Gumroad (merchant of record)**
- Paddle: Georgia is not on Paddle's unsupported list, so a Georgian company can register as a seller and get payouts. AgentaOS marks Paddle "Yes" for Georgia. — [Register-Company.ge](https://register-company.ge/blog/payment-processors-georgian-company/); [AgentaOS MoR table](https://agentaos.ai/answers/which-merchant-of-record-pays-out-to-my-country)
- Lemon Squeezy: Georgia is absent from the bank-payout list, but PayPal payouts (200+ countries) remain possible. AgentaOS says "Limited". — [Lemon Squeezy supported countries](https://docs.lemonsqueezy.com/help/getting-started/supported-countries); [Register-Company.ge](https://register-company.ge/blog/payment-processors-georgian-company/); [AgentaOS](https://agentaos.ai/answers/which-merchant-of-record-pays-out-to-my-country)
- Gumroad: local bank deposits are available in most countries, and PayPal is the fallback elsewhere. Payoneer and Wise are not supported payout methods. The minimum payout is $100. No source names Georgia specifically. — [Gumroad Help](https://gumroad.com/help/article/13-getting-paid.html); [Grey blog](https://grey.co/blog/how-to-receive-payments-from-gumroad-as-an-international-creator)

**Wise Business / Payoneer**
- A Georgia-registered business can hold a Wise Business account. Wise "receives and converts; it does not take card payments from strangers". Some Wise country guidance appears to exclude Georgia, but this source says it works in practice. — [Register-Company.ge](https://register-company.ge/blog/payment-processors-georgian-company/); [Bauer Group Wise FAQ](https://bauer-group.ge/en/knowledge/banking/wise-account-georgia/)
- Wise supports holding GEL and withdrawing to a Georgian account. — [OneSafe](https://www.onesafe.io/blog/does-wise-work-in-georgia); [Expathub](https://expathub.ge/business-bank-accounts-georgia-country/)
- Wise cannot replace a Georgian bank account for tax or government obligations. — [JustAdvisors](https://en.justadvisors.ge/blog/mejdunarodnie-raschoti-v-gruzii)
- Payoneer is supported in Georgia with withdrawal to a local bank, but in-app currency conversion is not available for GEL. — [Bauer Group Payoneer](https://bauer-group.org/en/blog/how-to-use-payoneer-from-georgia)

**Market context**
- In 2026 BOG and TBC charge a 1.5% fee (capped at 10 GEL) when Georgian debit cards pay in GEL on international sites. This hits local customers paying foreign merchants such as a US LLC on Stripe, not local acquirers. — [Georgia Today](https://georgiatoday.ge/georgia-banks-introduce-fee-on-gel-payments-on-international-platforms/)
- General Georgia PSP benchmark: 1.5-3.0% per card transaction, and 100-500 GEL one-time integration at some PSPs. — [PayAtlas](https://payatlas.com/countries/georgia-ge)
- A 2023 startup account says it was refused online acquiring by "all 5 Georgian banks and providers", and banks offered only domestic-card acquiring. — [HackerNoon](https://hackernoon.com/setting-up-online-acquiring-as-a-startup-firsthand-round-1-failed)

### Inferences
- Flitt should not be framed as an alternative to TBC. It is TBC Group's PSP and requires a TBC account, so a merchant refused by TBC is unlikely to get Flitt. Its advantage is a better product (published tiered rates, Tilda/WooCommerce/Shopify plugins, links, subscriptions, wallets) on top of a TBC relationship.
- The only independent local bank-acquirer paths are BOG, Liberty (directly or via UniPAY) and Credo (via Keepz). Payze is gone.
- International card rates locally cluster around 2.5-3.5%, rising to 4% + 0.35 GEL at UniPAY's foreign-card rate, versus about 2% domestic.
- Merchant-of-record platforms (Paddle, Lemon Squeezy, Gumroad) generally target digital products and SaaS, not arbitrary services such as consulting. This comes from general product knowledge and was not verified in this session, so the report should flag it.

### Gaps
- Official current BOG e-commerce tariff, payment-link product, subscription/tokenization support, payout currencies, and Tilda/Shopify plugin availability. bog.ge pages were not retrieved.
- Liberty and Credo e-commerce fees.
- Keepz e-commerce onboarding requirements and recurring support.
- Payout currencies (GEL vs USD/EUR settlement) for most local providers. UniPAY is the only one with a source (GEL/USD/EUR).
- Exact onboarding times, except Liberty's "a few days".
- Paddle and Lemon Squeezy fee figures were not retrieved. Typical public figures are Paddle 5% + $0.50 and Lemon Squeezy 5% + $0.50, but these are unverified here.
- Stripe Atlas cost and the US tax implications were not researched.

## Q2. Which options are popular among expats and freelancers in Georgia, and why

### Takeaway
Russian-language forums and blogs most often discuss BOG, Payze (historically) and Flitt for local acquiring, and Wise, PayPal-to-Visa and a US LLC with Stripe for foreign income. The recurring theme is difficulty getting international-card acquiring approved as a foreign-owned IE, especially for Russian citizens.

### Cited Findings
- Russian expat posts cite BOG (2%), Payze (2.7%, now closed), Flitt (2.2%/2.0%) and UniPAY (2.5%) as the options to consider. — [nlevshits.com](https://nlevshits.com/kak-i-ot-kogo-mozhno-podklyuchit-sistemu-platezhej-dlya-biznesa-v-gruzii/); [Madloba](https://madloba.info/blog/business-in-georgia/work-with-foreign-customers-in-georgia/)
- IE owners on TravelAsk report that bank staff did not understand the request for "acquiring", that only Georgian-card acceptance was offered, and that BOG refused them. — [TravelAsk 2747368](https://travelask.ru/questions/2747368_ge_vsem-privet-te-u-kogo-est-ip-v-gruzii-delali-li-vy-internet); [TravelAsk 4657101](https://travelask.ru/questions/4657101_ge_otkryl-ip-v-gruzii-ochen-nuzhen-onlayn-ekvayring-kart-ne-mog); [TravelAsk 4830530](https://travelask.ru/questions/4830530_ge_u-kogo-est-ip-v-gruzii-podskazhite-dopustim-ya-sdelayu-inter)
- A Russian-citizen IE was refused by several providers and accepted by Payze only after a 500 GEL deposit. — [Boot and Pencil](https://bootandpencil.com/blog/%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82-%D1%8D%D0%BA%D0%B2%D0%B0%D0%B9%D1%80%D0%B8%D0%BD%D0%B3-%D0%B2-%D0%B3%D1%80%D1%83%D0%B7%D0%B8%D0%B8/)
- English expat and legal-service guides (2026) recommend Wise for receiving transfers, PayPal Business with a Visa card, or a US LLC for Stripe. Several of these firms (StartGlobal, Bauer) sell US LLC formation, so they have a commercial bias. — [Legal Vista](https://legal-vista.com/georgia-ie-receive-payments-stripe-wise-paypal); [StartGlobal](https://startglobal.co/us/international/georgia/stripe/); [Bauer Group](https://bauer-group.ge/en/knowledge/banking/wise-account-georgia/)
- A 2026 article argues that most Georgian businesses need more than one system (BOG + Flitt + Stripe). Only its title and snippet were seen. — [Insights.ge, 2026-07-17](https://insights.ge/en/blog/cloud/2026-07-17/payment-systems-in-georgia-bog-flitt-stripe-why-most-businesses-need-more-than-one)

### Inferences
- Freelancers who invoice B2B clients mostly use Wise, Payoneer or a direct SWIFT transfer to a Georgian account and avoid card acquiring. Businesses that sell to consumers with card checkout use BOG or TBC/Flitt locally, or move to a US LLC with Stripe.
- Most forum evidence is from 2022-2024, the period of the Russian relocation wave. Current approval rates may differ.

### Gaps
- No quantitative popularity data was found, such as surveys or merchant counts.
- No recent (2025-2026) expat forum threads specifically on Keepz or UniPAY were found.

## Q3. Pros and cons versus TBC

### Takeaway
BOG is the closest like-for-like alternative (a major bank, about 2% local, wallets, WooCommerce plugins) but has a reputation for slow, document-heavy approval for foreigners. UniPAY and Keepz are easier PSP routes at higher international rates. Foreign routes (Paddle, US LLC with Stripe) give full global functionality at the cost of higher fees or a separate entity.

### Cited Findings
- TBC/Flitt advantages: a fully published tiered rate card (2.2%/2.0%, 2.5% international), Tilda/WooCommerce/Shopify/Wix plugins, subscriptions, links and wallets. It requires a TBC account. — [Flitt pricing](https://flitt.com/pricing/); [Flitt FAQ](https://flitt.com/faq/); [Quickpay](https://quickpay.ge/en/blog/georgian-payment-gateways-comparison)
- BOG pros: no minimum turnover, fast crediting, about 2% local, and Apple/Google Pay via the aggregator gateway. Cons: rates are negotiated rather than published (international 2.8-3.5% per integrators) and approval for foreigners is reportedly hard. — [nlevshits.com](https://nlevshits.com/kak-i-ot-kogo-mozhno-podklyuchit-sistemu-platezhej-dlya-biznesa-v-gruzii/); [Craftwebstudio](https://craftwebstudio.ge/en/integrations/bog-ipay); [Integrals](https://www.integrals.ge/en/integrations/bogpay); [TravelAsk](https://travelask.ru/questions/4657101_ge_otkryl-ip-v-gruzii-ochen-nuzhen-onlayn-ekvayring-kart-ne-mog)
- UniPAY pros: no setup fee, Wix/Shopify support, recurring payments, GEL/USD/EUR. Cons: up to 4.0% + 0.35 GEL for foreign cards and inconsistent published rates. — [UniPAY pricing](https://unipay.com/pricing/); [Wix](https://support.wix.com/en/article/connecting-unipay-georgia-as-a-payment-provider)
- Liberty pros: free integration and setup in "a few days". Cons: no published rates were found. — [Liberty](https://libertybank.ge/en/produqtebi/chemi-biznesistvis/distantsiuri-momsakhureba/e-commerce)
- Stripe via a foreign entity: Estonia is not viable for a Georgia resident per Stripe, and a US Atlas company is the suggested route. — [Stripe Support](https://support.stripe.com/questions/supporting-companies-that-registered-in-estonia-through-e-residency)

### Inferences
- If TBC refuses or limits international cards, the realistic order of attempts is BOG, then UniPAY or Liberty, then Keepz. In parallel, consider Paddle for digital products, or a US LLC with Stripe if volume justifies a second entity.
- Wise and Payoneer complement acquiring for B2B invoicing. They do not replace a card checkout.

### Gaps
- No side-by-side 2026 approval-rate or timeline data for foreign-owned IEs at TBC vs BOG vs PSPs.
- Chargeback and rolling-reserve terms for any local provider.
