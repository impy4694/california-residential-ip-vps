# California residential IP: a rotating pool by the GB, or one fixed CA address on your own VPS? Prices, closed ports and the checks that decide it (Sixtynet residential plans compared)

California residential IPs are sold in two shapes, and the price structures have nothing in common. Proxy providers meter them by the gigabyte: QuanticData's California pool runs $4.00/GB on a 1 GB package and drops to $2.20/GB at volume, while Hex Proxies starts at $4.25/GB. Sixtynet sells a different product: a KVM VPS with a residential IP attached, $25 a month for 2 cores, 2 GB RAM, 40 GB NVMe and 5 TB of monthly traffic.

What separates the two is how many addresses you need and whether they have to change. Hundreds of rotating California IPs for a crawler is proxy traffic. One California address that holds still while your own code runs on the same machine is a residential VPS. This page covers Sixtynet's four residential plans, what the closed ports rule out, where per-GB traffic beats a $25 box by a wide margin, and three things to confirm with support before you pay.

> **Quick pick:** if your project moves 10 GB a month or less, buy proxy traffic and skip this. Sixtynet makes sense once monthly volume reaches the hundreds of gigabytes and you want the compute sitting behind the same IP. For that, the entry plan covers most people: **Residential-STARTER at $25/month** with 2 cores, 2 GB RAM, 40 GB NVMe and 5 TB of traffic. 👉 [See what the $25 Residential-STARTER plan includes](https://sixtynet.net/aff.php?aff=39). You only need MEDIUM or LARGE if several scrapers or a headless browser stack will run at once and 4 GB of RAM is too tight.

## Sixtynet residential plans and prices

All four plans are KVM instances with a residential IP, root access and a monthly traffic allowance rather than per-GB billing. The rates below are the monthly prices listed on Sixtynet's residential product page.

| Plan | CPU · RAM · NVMe SSD | Traffic / month | Monthly price | Order |
| --- | --- | --- | --- | --- |
| Residential-STARTER | 2 cores · 2 GB · 40 GB | 5 TB | $25 | [Order Residential-STARTER](https://sixtynet.net/aff.php?aff=39) |
| Residential-MICRO | 4 cores · 4 GB · 80 GB | 10 TB | $45 | [Order Residential-MICRO](https://sixtynet.net/aff.php?aff=39) |
| Residential-MEDIUM | 8 cores · 8 GB · 160 GB | 20 TB | $85 | [Order Residential-MEDIUM](https://sixtynet.net/aff.php?aff=39) |
| Residential-LARGE | 16 cores · 16 GB · 320 GB | 40 TB | $165 | [Order Residential-LARGE](https://sixtynet.net/aff.php?aff=39) |

Annual billing cuts the rate by 13–16% on the plans where the yearly price is published: STARTER goes from $300 to **$260/year**, MICRO from $540 to **$460/year**, LARGE from $1,980 to **$1,660/year**. The MEDIUM yearly figure wasn't shown on the pages I checked, so read it at checkout or ask support. STARTER and MICRO list a 2G and 4G premium network respectively; MEDIUM and LARGE move to 10G.

One notice sits under all four plans, and it decides whether this product is usable for you at all: **ports 80 and 443 are closed** on residential IP products for risk-control reasons.

## What a California residential IP on a VPS lets you choose

Not the state, not the city, and not the carrier. Sixtynet's product pages have no location selector, so the residential IP is whatever gets assigned to your instance. The order links are filed under a store path labelled AT&T mobility residential, and a third-party writeup from July 2026 that benchmarked one of these boxes found its IP registered to Rancho Santa Margarita in Orange County on a Cox Communications upstream. Both point to a real US consumer line in California, but a sample of one isn't a guarantee, and nobody at Sixtynet promises Los Angeles or San Diego.

If California specifically is the point of the purchase, get the state confirmed in writing by support before paying. That one email is the difference between a working setup and a refund request.

The other structural limit is the count: one box, one residential IP. Proxy pools rotate a fresh address per request or hold a sticky session for a set number of minutes. Here the address is the machine's identity for as long as you keep the plan, which is what you want for account work, listing management or a logged-in session that must not jump cities mid-task.

## Closed 80/443: what still works, what doesn't

The port block kills public web hosting. You cannot serve a site, terminate TLS for a public domain, or receive webhooks on the standard ports from this box. Anything that needs to accept inbound public traffic is out.

Outbound work is unaffected. Scraping, price and stock checks, ad verification, API calls, automated browsers and account management all run normally, because they start from the box. Inbound access for yourself goes through a port-forwarding and whitelist panel, which is also how SSH or remote desktop stays reachable. If you need inbound ports opened to the public, plan for it before ordering, since this is a policy on the product line rather than a setting you can flip.

Sixtynet sells a separate LAX DDoS-protected line without the restriction. LAX-STARTER is $200/year for 2 cores, 2 GB RAM, 40 GB NVMe and 5 TB of traffic, and it is the right product if a public website is part of the plan. 👉 [Compare the residential plans and the LAX line](https://sixtynet.net/aff.php?aff=39).

## Break-even: per-GB proxy traffic against a $25 box

The comparison only turns in Sixtynet's favour at volume, and the crossover is earlier than most people expect.

| Monthly volume | Advertised per-GB proxy pricing | Sixtynet Residential-STARTER |
| --- | --- | --- |
| 1 GB | $4.00 (QuanticData 1 GB plan) | $25 |
| 10 GB | $30.00 (QuanticData 10 GB plan) | $25 |
| 25 GB | $70.00 (QuanticData 25 GB plan) | $25 |
| 500 GB | $875 (ProxyEmpire 500 GB list price) | $25 |
| 5 TB | roughly $11,260 at $2.20/GB | $25 |

Past about 10 GB a month, a $25 box with 5 TB included is cheaper than metered traffic, and at 500 GB the gap is two orders of magnitude. Two qualifiers keep that table honest. Per-GB pricing buys rotation, city targeting and a pool of addresses you can spread requests across; the $25 buys a single identity plus a machine. And a single IP cannot do the job of fifty: sites rate-limit per address, so a crawler that needs parallelism or anonymity across requests still needs a pool, whatever the box costs. Measure your actual monthly egress before deciding, because the answer flips depending on which of those two things you need.

If the numbers land on Sixtynet's side, the entry plan is the one to start with. 👉 [Start on the $25 plan and upgrade later if 5 TB stops being enough](https://sixtynet.net/aff.php?aff=39).

## Who should skip this and rent proxy traffic instead

- **You need city or ZIP targeting.** Los Angeles, San Diego and San Jose at city level is a proxy-pool feature. QuanticData lists 165 California cities, ProxyEmpire 556.
- **You need rotation.** A new IP per request, or dozens of parallel identities, is not what one VPS gives you.
- **You need mobile IPs.** ProxyEmpire targets mobile in 60 California cities including LA, San Diego and San Jose, but not Long Beach, Bakersfield, Santa Clarita, Chula Vista, Oxnard or Santa Barbara.
- **You're under 10 GB a month.** A $4 one-off gigabyte beats a $25 monthly commitment.
- **You need a public website.** Closed 80/443 rules it out.
- **You want a promise that nothing gets detected.** No provider can give you one. A residential IP removes the datacenter flag; behaviour, request rate and account history still get you blocked, and Sixtynet's own port policy exists because IP reputation is fragile.

## How Sixtynet compares with California proxy providers

Pure product information, since these are different categories. No provider below sells compute with the IP, and none of the proxy pools sell a guaranteed static California address.

| Provider | California targeting | Advertised rate | Static CA IP |
| --- | --- | --- | --- |
| QuanticData | 165 cities; sticky sessions up to 1,440 minutes | $4.00/GB down to $2.20/GB | No, static ISP IPs are country-level |
| ProxyEmpire | 556 cities and towns; mobile in 60 cities | $7.00/GB list on 1 GB, down to $1.50/GB at 1,000 GB | No, country-level |
| Hex Proxies | City-level across LA, San Francisco, San Diego, San Jose and more | From $4.25/GB | Not stated on its California page |
| Shifter | State and city level, deepest in LA, San Diego, San Jose | Advertises $1.00/GB | Not stated |

Sixtynet's position in that table is the odd one: the highest entry cost for the smallest number of addresses, and the only one that hands you a server. That is either exactly what you need or completely irrelevant, and the previous two sections are how you tell.

## Three checks before you pay

1. **State confirmation.** Ask support which state the IP sits in and whether it is exclusive to your instance. The product pages don't say, and it is the single fact the purchase rests on.
2. **Stock.** When I checked the residential product page, every plan displayed 0 available. Some store setups show that when stock isn't tracked, others when a batch is sold out. If you're on a deadline, ask before paying rather than after.
3. **Refund and payment.** The product pages don't spell out a refund window. A third-party writeup reports a 3-day money-back window, well under the 30 days most hosts offer, and notes card payments were suspended at one point for fraud checks. Confirm both at checkout.

## FAQ

### Can I get a static California IP from Sixtynet?

You get a residential IP attached to a VPS, and it stays with the instance for the billing term. That is not the same as the "static ISP proxy" sold per IP by proxy providers, which is generally country-level only. Sixtynet's pages don't let you choose the state, so confirm California before ordering.

### How much traffic is included?

5 TB a month on STARTER at $25, 10 TB on MICRO at $45, 20 TB on MEDIUM at $85 and 40 TB on LARGE at $165. Traffic is a monthly allowance rather than per-GB billing, which is where the cost advantage over proxy pools comes from.

### Can I host a website on a residential plan?

No. Ports 80 and 443 are closed on every residential plan. Use the LAX DDoS-protected line if you need public web hosting, or keep the residential box for outbound work only.

### Can I pick Los Angeles or San Diego?

No city selector exists on this product. If a specific metro matters, a proxy provider with city-level targeting is the correct tool, and sticky sessions are how you keep one California address for a long task, capped at 1,440 minutes with the providers that publish a limit.

### Is using a California residential IP legal?

Running a proxy or a remote server is legal in the United States; the legality sits in what you do through it. Public data collection, price monitoring, ad verification and testing your own sites are ordinary uses. Handling personal data of California residents brings CCPA and CPRA obligations, and bypassing access controls or committing fraud is not made acceptable by the IP type.

## Which plan to buy

Match the plan to the job rather than to the price ladder. A single scraper or an account that needs one steady California identity runs fine on **Residential-STARTER at $25/month**; the 2 GB of RAM is the real limit, not the 5 TB. Several concurrent headless browsers or a data pipeline that also needs to store and process locally puts you on **MICRO at $45** or **MEDIUM at $85**. **LARGE at $165** only pays off if 20 TB of monthly traffic is genuinely in play.

Two things to settle before checkout: the state your IP will sit in, and whether you need inbound ports opened. Get both answered in writing, then 👉 [order the Residential-STARTER plan at $25/month](https://sixtynet.net/aff.php?aff=39).
