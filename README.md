# Is DMIT Reliable? What the 99% SLA, the 3-Day Refund Rule, and the Pro/Eyeball/Tier 1 Split Actually Mean (Full Plan and Price Table)

Short answer: DMIT is reliable at the one job it was built for, which is carrying China-bound traffic over its Premium network. It is a much weaker bet if you buy the cheap Tier 1 plan and expect the same behaviour. Between those two statements sit a 99% uptime commitment with a published compensation ladder, a refund window with real conditions attached, and three separate networks that share a logo and not much else.

What follows is what the terms actually say, what the plans cost, and how to work out in advance which version of DMIT you are about to buy.

> **Quick pick.** China-facing traffic → **LAX.Pro.STARTER** at $29.90/mo (2 vCore, 2GB RAM, 80GB SSD, 3TB at 10Gbps, CN2 GIA both directions). Same budget but more monthly transfer and you accept CMIN2's "reasonable effort" routing → **LAX.EB.STARTER**, also $29.90, 5TB. General-purpose VPS, no China requirement → **LAX.T1.STARTER** at $12.90.
> 👉 [Check current LAX plan prices and stock](https://www.dmit.io/aff.php?aff=9081)

Plan availability moves around and DMIT runs seasonal promotions, so the checkout page is the final word on price. The figures below are the listed monthly rates for the plans on sale.

## Full plan and price comparison

| Plan | Network | CPU / RAM / SSD | Transfer / Port | Price/mo | Order |
| --- | --- | --- | --- | --- | --- |
| LAX.T1.STARTER | Tier 1 | 1 vCore / 2GB / 40GB | 4000GB / dynamic | $12.90 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.T1.MINI | Tier 1 | 2 vCore / 2GB / 60GB | 8000GB / dynamic | $21.90 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.T1.MICRO | Tier 1 | 4 vCore / 4GB / 80GB | 16000GB / dynamic | $32.90 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.STARTER | Premium (CN2 GIA) | 2 vCore / 2GB / 80GB | 3000GB / 10Gbps | $29.90 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.MINI | Premium (CN2 GIA) | 4 vCore / 4GB / 80GB | 5000GB / 10Gbps | $58.88 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.Pro.MICRO | Premium (CN2 GIA) | 4 vCore / 4GB / 160GB | 7000GB / 10Gbps | $74.99 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.STARTER | Eyeball (CMIN2) | 2 vCore / 2GB / 80GB | 5000GB / 10Gbps | $29.90 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.MINI | Eyeball (CMIN2) | 4 vCore / 4GB / 80GB | 10000GB / 10Gbps | $58.88 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| LAX.EB.MICRO | Eyeball (CMIN2) | 4 vCore / 4GB / 160GB | 14000GB / 10Gbps | $74.99 | [ Order](https://www.dmit.io/aff.php?aff=9081) |

Every plan includes one IPv4 and one IPv6 (/64 on Pro and Eyeball, a single address on Tier 1), instant setup and basic DDoS filtering. Annual billing is listed below twelve monthly payments: LAX.Pro.STARTER shows $322.99/yr against $358.80 for twelve months at the monthly rate.

Hong Kong and Tokyo run the same three-series structure across several sizes. The entry Premium plans are the ones with prices confirmed here:

| Plan | Location | CPU / RAM / SSD | Transfer / Port | Price/mo | Order |
| --- | --- | --- | --- | --- | --- |
| HKG.Pro.STARTER | Hong Kong | 1 vCore / 2GB / — | 800GB / 1Gbps | $79.90 | [ Order](https://www.dmit.io/aff.php?aff=9081) |
| TYO.Pro.STARTER | Tokyo | 1 vCore / 2GB / — | 500GB / 1Gbps | $39.90 | [ Order](https://www.dmit.io/aff.php?aff=9081) |

The Hong Kong premium buys latency, not capacity. It is roughly two and a half times the Los Angeles Pro entry price for a fraction of the transfer, and that maths only works if milliseconds to southern China decide the outcome for you.

## What DMIT actually commits to in writing

Section 14.3 of DMIT's Terms of Service reads: "At present, dmit is only able to provide 99% SLA." That is a lower ceiling than the 99.99% plastered across most hosting homepages, and it is the honest number for a business running premium transit on shared hardware.

The valuable part is what happens when the ceiling is missed. Compensation is tiered and published:

| Uptime achieved | Compensation |
| --- | --- |
| Below 99%, above 95% | Half a month of service credit |
| Below 95%, above 90% | One month of service credit |
| Below 90% | Two months of service credit |

Two things about this matter more than the percentages. First, you have to ask: claims follow the SLA notification procedure and must be filed within three days of the incident. No system flags it for you. Second, 99% allows about **7.2 hours of downtime per month**. For a personal proxy, a blog, a dev box or most small business sites that is plenty of slack. If an hour of outage costs you real money, a 99% commitment is not the contract you want, and you should be layering your own monitoring and a failover node on top regardless of which host you pick.

The tiered credits also tell you something about the operator's self-assessment. A host selling 99.99% and quietly refunding nothing has a worse track record on this specific question than one that writes 99% into the contract and defines the payout.

## The refund window is not "no questions asked"

Blog posts repeat "72-hour no-reason refund" as if it were a blanket promise. The actual terms are narrower and, in exchange, more useful.

- **Full refund within 3 days of purchase**, provided you have used less than 30GB of transfer.
- **Partial refund within 30 days**, calculated on remaining service time or remaining transfer quota, whichever works out more favourably for DMIT.

The 30GB cap is generous for testing. Two days of ping, traceroute and speed tests will not come close. Pulling a few hundred gigabytes through the box to "see how fast it really is" will void the full refund, and that is the single most common way people lose it.

Three cases are explicitly non-refundable: a service that has taken a DDoS attack, an IP geo-blocking problem that was not reported on day one, and an account that has already triggered three refunds on the same product series. That last clause is aimed at serial trial users, not at you.

The practical rule: **test IP reachability from your target region on the day the server comes up.** If the address is blocked where you need it, open a ticket immediately. Reporting on day three instead of day one can cost you the refund on geo-blocking grounds.

👉 [Start with a STARTER plan and test it inside the 3-day window](https://www.dmit.io/aff.php?aff=9081)

## The three networks decide whether "reliable" is even the right word

This is where most disappointed DMIT customers went wrong, and where most reviews fail to be specific enough to help.

**Premium (Pro).** Tier 1 transit plus DMIT's own backbone plus China Telecom CN2 GIA, in both directions. Mainland latency typically lands in the 140–180ms range from Los Angeles and holds close to that during evening peak, when cheaper routes start to sag. Bidirectional optimisation matters for uploads, not just downloads.

**Eyeball (EB).** Tier 1 transit plus CMIN2 and similar Chinese eyeball ISPs. DMIT's own wording is "reasonable effort for China routing", which is a fair description of what you get: clearly better than raw Tier 1 into China, without the Pro-grade guarantee behind it.

**Tier 1 (T1).** Standard internet routing with no China optimisation at all. DMIT states it does not guarantee that new-order IPs are globally reachable, naming China, Russia and countries with national network censorship, unless you add the `IP Guarantee+` add-on.

So when someone says DMIT "doesn't work in China", the useful follow-up question is which series they bought and whether they added the IP guarantee. A fresh T1 IP frequently will not connect from the mainland. A Pro plan almost always will.

👉 [Compare the Pro, Eyeball and Tier 1 listings side by side](https://www.dmit.io/aff.php?aff=9081)

## Pro and Eyeball cost the same at entry level. The trade is quota against route

Look down the STARTER, MINI and MICRO rows in the table and the pattern is hard to miss: LAX.Pro.STARTER and LAX.EB.STARTER are both $29.90. So are the MINI pair at $58.88 and the MICRO pair at $74.99. Identical hardware, identical price, different network and different transfer allowance.

Eyeball hands you more monthly traffic at every tier: 5000GB against 3000GB at STARTER, 10000GB against 5000GB at MINI, 14000GB against 7000GB at MICRO. Premium hands you the better route on the same money.

The decision therefore comes down to one question. If the traffic is mostly China-bound and latency-sensitive, the smaller quota on Pro is a fair swap. If you are pushing large volumes toward Chinese mobile users and can live with "reasonable effort", Eyeball gives you roughly double the headroom for the same invoice. Buying Pro and then throttling yourself to stay under 3TB is the worst of both.

Above MICRO, DMIT lists larger Pro configurations (8GB, 16GB, 24GB with 14TB to 50TB of transfer) and matching Eyeball sizes up to 100TB. Those are for people running production workloads, and the price ladder climbs quickly.

## The fine print that decides how it feels day to day

Uptime percentage is the number people quote. These four policies are what they actually experience.

**IP replacement.** On Pro and Eyeball, DMIT guarantees first-connection reachability in every country, barring force majeure like a national outage. On monthly billing without the `IP Care+` add-on you get one free IP swap every 15 days. With `IP Care+` that shortens to every 7 days, or $5 for an immediate change. On Tier 1 there is no global reachability guarantee at all unless you buy `IP Guarantee+`. If your use case involves an address that might get blocked, budget for the add-on rather than discovering the gap during an outage.

**Support.** Most services are unmanaged, with a stated target ticket response of up to 72 hours. That is the commitment. Forum anecdotes about faster replies exist, but they are anecdotes, and you should plan around three days rather than three hours.

**Backups.** Snapshots and online backup exist in the control panel at $0.45/GB/month and up. They are not included, and the TOS puts data protection on you. A host that sells you backup space as an extra is at least being clear about where the responsibility sits.

**Traffic overage.** Exceeding the monthly quota throttles the connection rather than shutting the server down. The plan listings quote the reduced speed after the cap, and it drops hard. Set a usage alert in the panel so the throttle never arrives as a surprise during a busy evening.

Hardware is quietly improving too. DMIT has been moving the LAX Tier 1 series onto its AN5 platform (AMD EPYC 9005), with AN4 (EPYC 9004) still running some volume plans. Newer silicon means better single-thread performance and fewer noisy-neighbour problems on shared nodes, which is a real reliability gain that never shows up in an SLA table.

👉 [Check which add-ons apply to the plan you're considering](https://www.dmit.io/aff.php?aff=9081)

## What public reviews do and don't tell you

Trustpilot shows DMIT at **2.5 out of 5**, which sounds alarming until you notice the score rests on four reviews. Trustpilot itself notes the company has not invited customers to review it and that the score may not be representative. Four data points is not a reliability measurement.

The forum picture is more informative. Across threads on Reddit and LowEndTalk, three points come up repeatedly: the CN2 GIA routing on the Pro series is genuine and stays stable through evening peak; DMIT is routinely compared with BandwagonHost's CN2 GIA tier and treated as the closest technical equivalent; and complaints cluster around price, support response times and occasional IP reachability problems on Tier 1. That last complaint is the exact failure mode DMIT's own terms warn about, which suggests the product behaves as documented rather than as advertised.

Read the pattern as series-dependent. Pro buyers mostly report what they paid for. Tier 1 buyers expecting China access mostly do not.

## Who should not buy DMIT

Skip it if any of these describe you.

- **You need 99.99% uptime for revenue-critical systems.** DMIT commits to 99%, and no amount of routing quality changes that clause.
- **You expect a reply within the hour.** Unmanaged tickets target 72 hours.
- **You want the cheapest generic VPS and don't care about China routing.** Tier 1 at $12.90 is decent, but the premium you are paying still funds a China-optimised network you will not use. Vultr's hourly billing and wider location list suit experimentation better.
- **You are buying Tier 1 specifically to reach mainland China** and skipping `IP Guarantee+`. This is the single most common way to conclude, wrongly, that the whole provider is unreliable.

The honest comparison point for Pro is BandwagonHost's CN2 GIA plans, which target the same buyers with the same routing logic and a longer track record with English-speaking customers. DMIT's edge sits in the Eyeball tier, where CMIN2 routing at $29.90 with 5TB is a combination that is harder to match, and in Hong Kong and Tokyo, where the premium buys latency that Los Angeles cannot deliver.

## Questions people ask before ordering

**Will DMIT disappear overnight?** Nobody can promise that about any host. What can be checked: the company has operated for years, runs its own backbone rather than reselling someone else's capacity, and sells to a niche that pays specifically for routing quality. That is a more durable business model than $2 KVM boxes, and it is not a guarantee.

**Does it slow down at 8pm?** Pro holds roughly 140–180ms from Los Angeles through peak hours. Eyeball is a best-effort China route. Tier 1 has no China optimisation and should not be judged on Chinese latency at all.

**Hong Kong or Los Angeles?** Hong Kong wins on latency to southern China, with Shenzhen reachable in single-digit milliseconds on a good path, and loses badly on price and transfer allowance: $79.90 for 800GB against $29.90 for 3TB. Start in Los Angeles unless the millisecond gap changes what your application can do.

**Can a beginner run it?** The control panel is WHMCS-based, so booting, reinstalling the OS and watching bandwidth all happen in a familiar interface. Everything above the operating system is your problem, which is what "unmanaged" means.

**Are there discount codes?** DMIT runs seasonal promotions, and the terms live on the promotion page rather than buried in a FAQ. Two conditions worth knowing before you plan around a code: they generally apply to new customers only, and any cashback component is paid as account credit in monthly instalments, not as cash. Confirm what actually applies at checkout instead of trusting a coupon list published months ago.

## How to decide, and two things to check before you pay

Match the plan to the traffic, not to the spec sheet. Users in mainland China → Pro, starting at LAX.Pro.STARTER. Same users, tighter budget, more transfer needed → Eyeball, starting at LAX.EB.STARTER. No China requirement → Tier 1, and buy the smallest size that fits. Latency to southern China is the whole product → Hong Kong Pro, accepting the price.

Before you pay, confirm two things. Test IP reachability from your actual target region on day one and open a ticket the same day if it fails, because the refund depends on it. And check whether the series you chose includes a reachability guarantee, or whether it needs `IP Guarantee+` on top.

👉 [View current DMIT plans, prices and availability](https://www.dmit.io/aff.php?aff=9081)
