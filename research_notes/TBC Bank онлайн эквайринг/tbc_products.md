# TBC Bank (Georgia) online acquiring / e-commerce products (research as of 2026-11-06)

**Method note:** Direct page fetches failed for developers.tbcbank.ge, flitt.com and cbw.ge: the session's network allowlist blocks those hosts. Every finding below comes from search-engine summaries and excerpts of the listed pages, not from reading the full pages. Most tbcbank.ge pages carry no visible date. Treat exact numbers as "reported on the official page per search excerpt" and confirm them on the live page before relying on them. Where two official TBC pages give different numbers, both are listed.

## 1. Which products exist (gateway/API, hosted checkout, payment links, QR, recurring/saved cards, split, installments)?

### Takeaway
TBC has two current lines for online card acceptance. The bank's own "TBC E-Commerce" (TBC Checkout, the "tpay" API) offers a hosted checkout via REST API, Pay by Link, pre-authorization, saved-card/recurring payments, split payments, installments, QR/BNPL and Apple Pay / Google Pay. Flitt is a separate TBC Group payment platform with similar features, aimed at businesses in Georgia, Uzbekistan, Armenia and Moldova. TBCPay (tbcpay.ge) is a third, separate bill-payment/terminal channel.

### Cited Findings
- TBC's developer site describes TBC E-Commerce as a payment system for managing online payments on a website or in an app, with pre-authorization and "Pay by link" (accepting online payments without a website). Integration steps: register the company as a merchant to get Merchant Credentials, then create a developer account to get an API key. — [TBC Developers: e-commerce](https://developers.tbcbank.ge/page/e-commerce); [Checkout overview](https://developers.tbcbank.ge/docs/checkout-overview)
- API: the token endpoint is `https://api.tbcbank.ge/v1/tpay/access-token`. The developer `apikey` goes in a header and the merchant client_id/client_secret in the form body. The response is a Bearer token valid for 86400 s (1 day). The merchant credentials are separate from the Developer Portal API key. — [Get access token](https://developers.tbcbank.ge/docs/checkout-get-checkout-access-token); [Checkout API overview](https://developers.tbcbank.ge/docs/checkout-api-overview)
- Documented API methods include "Create E-Commerce payment with SPLIT", "Execute recurring payment" and "Get E-Commerce payment details". — [Split](https://developers.tbcbank.ge/docs/checkout-create-checkout-payment-with-split); [Execute recurring](https://developers.tbcbank.ge/docs/checkout-execute-recurring-payment); [Get details](https://developers.tbcbank.ge/docs/checkout-get-checkout-payment-details)
- Saved cards / recurring: the card is saved during a first payment, which returns a recId. Later charges go through the execute-recurring endpoint with that recId. WebQR, Apple Pay and installments pay methods cannot be used in a save-card request. — [Execute recurring payment](https://developers.tbcbank.ge/docs/checkout-execute-recurring-payment); [Split payment doc](https://developers.tbcbank.ge/docs/checkout-create-checkout-payment-with-split)
- Pay methods listed in the docs include cards, Apple Pay, Google Pay, QR, installments and BNPL. QR and BNPL methods must be activated for the merchant in the back office (contact sales). Installments need a separate registration as an Installments merchant, plus a campaignID and MerchantKey set in the merchant dashboard. — [Payment methods](https://developers.tbcbank.ge/docs/payment-methods)
- Separate TBC QR Payment API docs exist. — [TBC QR Payment overview](https://developers.tbcbank.ge/docs/overview)
- Pay by Link is described as a way for online sellers to take payments without a website. — [TBC Pay by link](https://tbcbank.ge/en/card-payments/pay-by-link)
- There is an "E-commerce service provider" (payment facilitator / PSP) product with sub-merchants. — [TBC E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider)
- Flitt is "a fintech company and a member of the TBC Group". One integration gives access to all its payment methods: cards, Apple Pay, Google Pay, open banking, and TBC installments/BNPL (Credo, Liberty and BOG installments "coming soon"). Pay by link supports all methods, including Apple Pay and Google Pay. It also offers payouts. — [Flitt About](https://flitt.com/about-us/); [Flitt card payments](https://flitt.com/card-payments/); [Flitt payouts](https://flitt.com/payouts/)
- Background: according to TBC's own account, its online payment service held a significant market share, and TBC then "acquired an international payment platform, adding global professionals to the local team". Georgian press coverage dates to about Sept 2024. — [Georgia Today, 2024-09-30](https://georgiatoday.ge/simple-and-versatile-international-payment-platform); [GBC](https://gbc.ge/en/news/finanse/simple-and-versatile-international-payment-platform); [Forbes Georgia](https://forbes.ge/en/simplify-the-management-of-end-to-end-payments/)
- TBCPay (tbcpay.ge) is a separate channel: "Start receiving payments in just 5 days", a 300 GEL integration fee and an online payment fee of 1.2% + 0.9 GEL (per search excerpt). — [tbcpay.ge for business](https://tbcpay.ge/en/for-business)

### Inferences
- For a Stripe-like setup (API, hosted page, links, subscriptions), the fitting product is TBC E-Commerce / Checkout. TBCPay looks like a bill-payment/kiosk aggregator, so its 1.2%+0.9 GEL rate probably does not apply to card acquiring for a website.
- Flitt seems to be where TBC Group's merchant acquiring is heading. A new merchant may be pointed to Flitt rather than TBC Checkout. The third-party Magento module "TBC card payments through Flitt" supports this reading.

### Gaps
- Whether TBC Checkout is being migrated into Flitt, and on what timeline: not confirmed.
- Exact Flitt launch date: not stated in the results.
- Subscription management features (plans, retries, dunning): no evidence found. Only token-based merchant-initiated recurring charges are documented.

## 2. International cards, Apple Pay / Google Pay, currencies, settlement currency

### Takeaway
Officially, cards issued by foreign banks are accepted at a higher rate of 2.5%, plus a security reserve and longer settlement. Apple Pay and Google Pay are supported. Settlement is in GEL by default, and the bank can open accounts in other currencies. Multi-currency acceptance exists (merchant accounts per currency, currency enabled per merchant), but I found no published list of currencies.

### Cited Findings
- E-commerce tariff: 2% for Visa/Mastercard cards from TBC and other Georgian banks, 2.5% for cards issued by foreign banks. — [TBC E-Commerce page](https://tbcbank.ge/en/card-payments/e-commerce); [TBC Online Payments for Business](https://tbcbank.ge/en/business/payment-systems/online-payments)
- Settlement timing: Georgian-card payments are credited the following day, foreign-card payments within 3 days at most. — [TBC Online Payments for Business](https://tbcbank.ge/en/business/payment-systems/online-payments)
- Foreign-card risk reserve: an insurance reserve of 10% of the transaction amount held for 6 months, plus a fixed 500 GEL (per search excerpt). — [TBC Online Payments for Business](https://tbcbank.ge/en/business/payment-systems/online-payments); [TBC E-Commerce](https://tbcbank.ge/en/card-payments/e-commerce)
- TBC's Google Pay integration guide: Purchase-type authorizations only, Visa and Mastercard networks, 3DS mandatory. — [TBC Google Pay documentation (2023, PDF on developers.google.com)](https://developers.google.com/static/pay/api/download-assets/unitedfinancialcorporation-gpay-integration.pdf)
- No Amex mentioned anywhere. Flitt also says "Visa and Mastercard cards are supported." — [Flitt card payments](https://flitt.com/card-payments/)
- Currency: payments in a given currency must be enabled for the merchant. TBC's business page says customers can pay with their preferred card in the currency of their choice. — [TBC Developers](https://developers.tbcbank.ge/docs/checkout-api-overview); [TBC Online Payments](https://tbcbank.ge/en/business/payment-systems/online-payments)
- The official WooCommerce plugin changelog mentions "merchant accounts per currency". — [TBC E-commerce for WooCommerce (tpay-ge-woocommerce)](https://fair.pm/packages/plugins/tpay-ge-woocommerce/); [wpdavies mirror](https://wpdavies.dev/plugin-directory/tpay-ge-woocommerce/)
- The merchant terms say proceeds go to the merchant's account in national currency (GEL). The bank may open an account in any currency if one is needed for settlement. — [TBC E-Commerce terms PDF](https://assets.eu.ctfassets.net/psnuheg7hu1m/4q799WaAbx3Mf1NK3ojcJO/9b3da13ae2bb00d465a44df9a2dffe4a/29.02_eng.pdf)

### Inferences
- Charging in USD or EUR is likely possible (per-currency merchant IDs), but it has to be enabled separately. The default and the documented settlement is GEL.
- The reserve (10% for 6 months plus 500 GEL) will tie up a lot of cash for a service business mostly paid by foreign cards.

### Gaps
- No published list of supported transaction currencies; USD/EUR inferred from the plugin changelog and general statements only.
- Amex, UnionPay and other networks: not confirmed.
- FX rate and spread used when converting foreign-currency proceeds: not found.

## 3. Fees, setup and monthly fees, payout timing

### Takeaway
Official rates are 2% for Georgian cards and 2.5% for foreign cards. Integration is free, with a monthly minimum fee: 50 GEL on the newer page, 30 GEL on an older page. The two pages also differ on wallet surcharges. Flitt's published rates are 2.2% / 2.0% for local cards by volume, 2.5% for international cards and up to 1% for open banking. Payouts are T+1 for local cards and up to T+3 for foreign cards at TBC, and "within 24 hours" at Flitt.

### Cited Findings
- Newer TBC e-commerce page: 2% / 2.5%, a recurring monthly fee of at least 50 GEL, no transaction fee on Apple Pay and Google Pay, free integration. — [TBC E-Commerce](https://tbcbank.ge/en/card-payments/e-commerce)
- Older TBC business page: same 2% / 2.5%, a minimum of 0.1 per transaction, a 30 GEL minimum monthly fee, and a 0.4% digital-wallet surcharge on top. This conflicts with the "no fee" for wallets above. — [TBC Online Payments for Business](https://tbcbank.ge/en/business/payment-systems/online-payments)
- Pay by Link: same 2% / 2.5%, Apple Pay / Google Pay free, registration free. — [TBC Pay by link](https://tbcbank.ge/en/card-payments/pay-by-link)
- Service-provider (PSP) model: final conditions depend on the platform's annual turnover and business category (MCC). — [TBC E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider)
- Standard limits: 3,000 GEL per transaction and 10,000 GEL per day, adjustable by merchant profile and turnover. Stated for service-provider sub-merchants; the search summary also attributed them to the online payments page. — [TBC E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider)
- Third party (Craftwebstudio, 2026): TBC local-card commission 1.9–2.4% vs BoG 2.0–2.5%; BoG about 60% market share, TBC about 30%. — [Craftwebstudio BoG vs TBC](https://craftwebstudio.ge/en/compare/bog-vs-tbc-payment)
- Third-party integrator: "No additional fee is applied for Apple Pay / Google Pay". — [Integrals.ge](https://www.integrals.ge/en/integrations/tbcpayments)
- Flitt pricing: local cards 2.2% (0–10,000 GEL monthly volume) and 2.0% (10,000–50,000 GEL); international cards 2.5%; open banking up to 1%; payments reflected within 24 hours. Above 50,000 GEL pricing is custom. An active TBC bank account is required. — [Flitt pricing](https://flitt.com/pricing/); [Gappsy Flitt review](https://www.gappsy.com/tools/flitt/)

### Inferences
- Realistic all-in cost for a services business paid mainly by foreign cards: about 2.5% plus the monthly minimum, plus the cash-flow cost of the 10% reserve. Discounts are negotiable by MCC and turnover.

### Gaps
- Official tariff PDF with a date: not obtained, since the fetch was blocked. Chargeback fees and refund fees: not found.

## 4. Integrations: plugins, API docs, sandbox

### Takeaway
The official plugins are WooCommerce, CS-Cart, Storera.ge and Kovzy. Magento, OpenCart and Shopify options are community or third party. The REST API is documented on developers.tbcbank.ge (with a theneo.io mirror). A sandbox host is reported only by a third-party SDK.

### Cited Findings
- The TBC portal lists these plugins: WordPress–WooCommerce, CS Cart, Storera.ge, Kovzy. — [TBC plugins overview](https://developers.tbcbank.ge/docs/checkout-plugins-overview)
- Official WooCommerce plugin "TBC E-commerce for WooCommerce" (slug tpay-ge-woocommerce). Setup: enter Client ID and Client Secret, paste the callback URL into the merchant dashboard, enable "TBC Checkout". The changelog mentions per-currency merchant accounts and a pre-authorization method. — [TBC WooCommerce doc](https://developers.tbcbank.ge/docs/checkout-woocommerce); [fair.pm listing](https://fair.pm/packages/plugins/tpay-ge-woocommerce/)
- An old unofficial WooCommerce plugin for the legacy TBC gateway (.p12 → .pem certificate) has not been updated in over 2 years. — [ChoosePlugin](https://chooseplugin.com/plugin-info/woo-tbc-payment-gateway/); [GitHub Mamaduka](https://github.com/Mamaduka/woocommerce-tbc-credit-card-payment-gateway-free)
- Magento 2: community module from mage2pro, plus a module from shubo that routes TBC card payments via Flitt (needs a Flitt Merchant ID and Secret Key from TBC). — [mage2pro/tbc-bank](https://github.com/mage2pro/tbc-bank); [packagist shubo/module-tbc-payment](https://packagist.org/packages/shubo/module-tbc-payment)
- OpenCart: a community "TBC Bank – эквайринг" module. — [OpenCart Club](https://opencart.club/files/file/503-tbc-bank-ekvayring/)
- Shopify: CartDNA (a third party) offers a TBC payment app, with descriptions that contradict each other. Craftwebstudio claims TBC released official Shopify and WooCommerce plugins in 2024, which the TBC portal does not confirm. — [CartDNA](https://www.cartdna.com/shopify-payment-methods/tbc-bank); [Craftwebstudio TBC integration](https://craftwebstudio.ge/en/integrations/tbc-ecommerce)
- SDKs: Laravel (laravel-tbcpay, legacy), .NET (helixge), and a Python SDK that claims sandbox `https://test-api.tbcbank.ge/v1`. The Python SDK's own issue tracker says its sandbox flow is still unvalidated. — [laravel-tbcpay](https://github.com/Lotuashvili/laravel-tbcpay); [TbcBank.EcommerceClient.Net](https://github.com/helixge/TbcBank.EcommerceClient.Net); [tbc-sdk-python](https://github.com/astronomiwe/tbc-sdk-python); [Issue #14](https://github.com/astronomiwe/tbc-sdk-python/issues/14)
- API docs mirror on theneo. — [TBC API Documentation (theneo)](https://app.theneo.io/tbc/ecommerce/Overview)
- Aggregator QuickPay.ge lets merchants plug in their own BOG, TBC, Credo or Flitt credentials. — [Quickpay comparison 2026](https://quickpay.ge/en/blog/georgian-payment-gateways-comparison)

### Gaps
- Tilda: no TBC integration found; Flitt or Tilda native support not checked.
- Official sandbox URL and test cards: not confirmed from TBC.

## 5. Onboarding: how to apply, documents, website requirements, review time

### Takeaway
Any registered taxpayer can apply, individual or legal entity, so an Individual Entrepreneur (IE) is eligible. A website is required except for Pay by Link. The site must show T&C, a return policy, a privacy policy, a delivery policy and contacts with an address. I found no official review time. TBCPay advertises "5 days".

### Cited Findings
- E-commerce eligibility: you only need to be registered as a taxpayer, regardless of whether you are an individual or a legal person. Service providers (PSPs) must be a Georgian legal entity with an NBG payment-service-provider licence, active business status and a Visa certificate. — [TBC E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider); [TBC E-Commerce](https://tbcbank.ge/en/card-payments/e-commerce)
- A website is needed for gateway integration. The exception is Pay By Link (one-time links, no website). — [TBC E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider)
- Required website content: terms and conditions, a return policy (conditions under which product or money is returned), a privacy policy, a delivery policy (conditions, timeframe, fee) and contact details, including a physical or legal address. — [TBC Checkout overview](https://developers.tbcbank.ge/docs/checkout-overview)
- Agreement excerpts: the merchant's trade name must appear on the site before payment. The merchant needs confidentiality, transaction-security, payment and legislative-compliance policies. Records must be kept for 180 days. The merchant must fully refund chargebacks. — [TBC E-Commerce key terms PDF](https://assets.eu.ctfassets.net/psnuheg7hu1m/2XgPcxANQtwBmlLjvQsGJw/8efc508deca6a65de0b23c0ea4e53a8f/6f6bfe13-fb73-49c5-ac66-13e6aaf19ae7); [TBC E-Commerce PDF](https://assets.eu.ctfassets.net/psnuheg7hu1m/1t3uuvUtF1daC4nJvnaIRs/ff9752146c3a2ca1077d40461682acfb/eng.pdf)
- PSP applicants may be asked for a risk management policy, integration policy, chargeback policy and AML policy. — [TBC E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider)
- Flitt requires an active TBC bank account and serves businesses officially registered in Georgia, Uzbekistan, Armenia and Moldova (API docs also list Kazakhstan). — [Flitt pricing/FAQ](https://flitt.com/pricing/); [Flitt supported countries](https://docs.flitt.com/supported-countries/)
- User reports (older and undated, Russian-language): IE owners said TBC and BoG staff did not understand "internet acquiring" or offered only Georgian-card acceptance or a POS terminal. Stripe was unavailable; PayPal and Payoneer were used instead. — [Travelask Q1](https://travelask.ru/questions/2747368_ge_vsem-privet-te-u-kogo-est-ip-v-gruzii-delali-li-vy-internet); [Travelask Q2](https://travelask.ru/questions/4657101_ge_otkryl-ip-v-gruzii-ochen-nuzhen-onlayn-ekvayring-kart-ne-mog)
- 2026 blogs give conflicting reports on whether TBC currently opens accounts for Russian/Belarusian citizens. One says TBC no longer does; others report high approval. — [card-open.ru 2026](https://card-open.ru/blog/gruzinskie-banki-dlya-rossiyan-2026); [Klerk](https://www.klerk.ru/blogs/EasypayWorld/713869/)

### Inferences
- The older user reports conflict with today's official tariff, which explicitly prices foreign cards at 2.5%. The "Georgian cards only" experience is either outdated or reflects a branch-level or risk decision. Applying online with a compliant website is likely to work better than walking into a branch.

### Gaps
- Official review or approval time for TBC E-Commerce: not found.
- Exact document list for an IE applicant: not found.

## 6. Prohibited / restricted business types (MCC), esp. remote services / consulting / digital

### Takeaway
TBC's agreement prohibits anything banned by Georgian law or bank policy, and names examples such as unlicensed digital content, replicas and prescription drugs. I found no full MCC list. Pricing and terms depend on MCC. I found nothing that bans consulting or remote services outright.

### Cited Findings
- The merchant agreement lists prohibited e-commerce categories including unlicensed digital content, replica "fake" products and prescription drugs, plus anything prohibited by Georgian law or the bank's policy (seen only as fragments). — [TBC E-Commerce PDF](https://assets.eu.ctfassets.net/psnuheg7hu1m/6LvBlV3ZxCtHKb1sBvh04s/45b9018afdc1c8824652ee317ad28d56/b6a2acc5-bdc3-48ae-98f5-449e22f6dc51.pdf)
- Final conditions depend on annual turnover and business category (MCC). — [TBC E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider)
- Third-party guide (not official): most standard e-commerce faces no special restrictions. Illegal gambling, unlicensed financial services and some crypto operations are restricted or need approval. — [PayAtlas Georgia](https://payatlas.com/countries/georgia-ge)
- Crypto-related account freezes at Georgian banks were reported in 2026 (third party). — [gecrypto.com](https://gecrypto.com/news/bank-account-freezes-for-crypto-in-georgia/)

### Inferences
- Consulting, IT and digital services are likely acceptable as long as the website clearly describes the service, the price, delivery (how and when the service is provided) and refunds. Expect heavier risk review and the foreign-card reserve if most customers are abroad.

### Gaps
- Full TBC prohibited or high-risk MCC list: not publicly found. It has to be requested from the bank.

## 7. TBC Uzbekistan / Payme: merchant acquiring for international cards

### Takeaway
TBC owns 100% of Payme (51% from 2019, the remaining 49% bought in 2023). Payme's merchant acquiring is domestic (UZCARD/HUMO, with Visa and Mastercard cards inside the app). I found no evidence that Payme Business accepts foreign-issued cards for merchants. Flitt says it serves businesses registered in Uzbekistan and supports Visa and Mastercard, with no detail on Uzbekistan.

### Cited Findings
- TBC got an Uzbek banking licence and 51% of Payme in 2019. — [Wikipedia TBC Bank](https://en.wikipedia.org/wiki/TBC_Bank); [bm.ge](https://bm.ge/en/news/tbc-bank-acquires-leading-uzbek-payment-platform-payme/32393)
- In 2023, TBC bought the remaining 49% for $55.7M, valuing Payme at $113.6M (per search summary). — [FinChannel](https://finchannel.com/tbc-acquires-top-payment-platform-of-uzbekistan-payme/)
- TBC Uzbekistan partnered with Mastercard for cards, international purchases and transfers. This concerns issuing, not merchant acquiring. — [The Paypers](https://thepaypers.com/payments/news/tbc-uzbekistan-partners-with-mastercard)
- 2026 tourist guide (blog): foreign Visa/Mastercard cannot fund Payme or Click QR payments. — [uz-safar.com](https://www.uz-safar.com/blog/uzbekistan-cashless-payme-click-uzum-qr-guide-2026)
- Apple Pay and Google Pay went live in Uzbekistan around 27 Oct 2026 for Visa/Mastercard cards from local banks. — [Gazeta.uz 2026-10-27](https://www.gazeta.uz/en/2026/10/27/google-apple-pay-uzbekistan/)
- Flitt serves businesses registered in Uzbekistan; Visa and Mastercard are supported. — [Flitt About](https://flitt.com/about-us/); [Flitt supported countries](https://docs.flitt.com/supported-countries/)

### Gaps
- Whether Payme Business or TBC Uzbekistan offer e-commerce acquiring of foreign-issued cards, and on what terms: no source found.
