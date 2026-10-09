# Build tools that prove things work

The best underserved SaaS opening for you in 2026 is an **e-invoice preflight API**. It checks German electronic invoices (and later French and Polish ones) against the official rules, explains each error in plain language, and turns simple invoice data into valid XRechnung or ZUGFeRD files. The law creates the demand. German firms with more than €800,000 turnover must issue structured e-invoices from **1 January 2027**, and all other German firms from 2028. French SMEs must issue them from **September 2027**, and Polish penalties start in January 2027. In one March 2026 survey, only **7%** of French firms had finished preparing. The idea also has the highest hiring score of the seven (22 of 24). Building it makes you write an async file pipeline, manage rule sets that change every six months, test against a corpus of real invoices, and add an AI step whose output a strict validator checks. The other six ideas share one trait with it: each one **proves that something that should work actually does**. That means a backup that restores, a background job that produced real output, a cookie banner whose "reject" button really blocks trackers, a webhook that arrived, AI spending that stays inside each customer's budget, and a website that is accessible. The evidence points to this "verification" pattern. The obvious categories (AI-search visibility tracking, LLM observability, uptime monitors, status pages) are already full of well-funded or free tools. Treat the scores as informed judgment, not measurement. The researchers could not reach Reddit, Hacker News points show curiosity rather than willingness to pay, and most competitor prices come from third-party sites. Revenue is a bonus. What moves a hiring manager is a few real users and a clear write-up of your design decisions.

## A shrinking junior market rewards proof that AI can't fake

Hiring has split in two. At the end of 2025, US tech job postings were **34% below** their February 2020 level, but postings that mention AI were about **45% above** it. More than 20% of software-development postings now mention AI ([Indeed Hiring Lab](https://hiringlab.indeed.com/2026/01/22/january-labor-market-update-jobs-mentioning-ai-are-growing-amid-broader-hiring-weakness/)). Employment of software developers aged 22–25 fell **nearly 20%** from its late-2022 peak, and new graduates now make up about **7% of Big Tech hires**, down from 15% before the pandemic ([SF Standard](https://sfstandard.com/2025/08/27/ai-entry-level-jobs-decline/)). Hiring managers say AI tools have weakened live-coding and take-home tests as signals. One scaleup made 4 of its last 5 hires through referrals. The signals that still worked were direct, specific outreach and proof of real work ([Pragmatic Engineer](https://newsletter.pragmaticengineer.com/p/tech-hiring-inflection-point)).

Hiring advice agrees on what counts: **real users or measurable results**, technical depth (scale, failure handling), and written evidence of judgment such as design write-ups. To-do, weather and clone apps, basic CRUD projects and half-finished repos count against you ([techinterview.org](https://www.techinterview.org/post/3233474610/side-projects-open-source-engineering-resume/)). Recruiters "recognize clones within seconds". What does impress is a useful app with one small AI feature that does a single, limited job ([Arslan Ahmad](https://arslandg.substack.com/p/3-portfolio-projects-that-actually)). A SaaS is the most direct way to show all of this at once. It has to be deployed. Its users are other people. It needs login, separate data for each customer, billing, background jobs and monitoring, which are the parts every tutorial skips. It also gives you a concrete reason to email a hiring manager: "I built X, 30 businesses use it, here is my design write-up."

Set your expectations honestly. Experienced founders say "distribution is the whole game". B2B products typically take **18–24 months** to become self-sustaining, and most obvious niches now have 10–20 competitors ([HN](https://news.ycombinator.com/item?id=47803524)). Do not expect a salary from this in year one. Even a few paying customers is a strong hiring signal, so the two goals support each other. Build on the stack employers use. Among Python developers, FastAPI use rose from 29% to **38%** and PostgreSQL to 49% ([JetBrains](https://blog.jetbrains.com/pycharm/2025/08/the-state-of-python-2025/)), and 71% of developers use Docker ([Stack Overflow](https://survey.stackoverflow.co/2025/technology/)).

## The open gaps are verification tools, not new categories

The research covered four areas: AI-era problems, developer tooling, new regulations and small-business pain. The open spaces in all four looked alike.

- **Developer tooling.** The specific "nothing does this" complaints were about checking whether a job's result was correct, whether a backup restores and whether a webhook arrived.
- **Regulation.** The safe solo products sit beside the regulated process as validators, scanners and evidence logs. Becoming a certified intermediary is too heavy for one person.
- **AI.** The most-discussed threads were about agents causing damage and costs running out of control, not about missing dashboards.

Verification products suit a solo developer. They are narrow, they plug into tools customers already run, and their value takes one sentence to explain: "we check X so you don't find out the hard way."

Two more patterns shaped the shortlist. First, Python-specific tools did better than generic ones. Django Control Room, which adds Celery and Redis panels to the Django admin, reached 134 points on Hacker News ([HN](https://news.ycombinator.com/item?id=47151995)), while generic uptime, status-page and email launches drew 14–29 points ([HN](https://news.ycombinator.com/item?id=46617114)). Second, open-source tools you can host yourself got the strongest response. Healthchecks.io shows the model works: its code is open source, and it sells a paid hosted version ([Capterra](https://www.capterra.com/p/249957/Healthchecksio/pricing/)). Each pick below therefore includes an open-source part.

Several popular-sounding ideas were cut because they are too crowded or a poor fit for one person.

| Idea | Why it was cut | Source |
|---|---|---|
| Tracking brand visibility in AI search answers (GEO) | 100+ tools, $200M+ in VC funding and a $1B leader; Adobe/Semrush and Ahrefs bundle it | [Market analysis](https://guptadeepak.com/geo-compass/guides/geo-tooling-market-2026/) |
| LLM observability, evals and gateways | Langfuse (36k GitHub stars, free to self-host) was bought by ClickHouse; Braintrust is valued at $800M | [Langfuse](https://langfuse.com/blog/joining-clickhouse); [Axios](https://www.axios.com/pro/enterprise-software-deals/2026/02/17/ai-observability-braintrust-80-million-800-million) |
| Permission firewall for AI agents | Biggest pain (an agent deleting a production database drew 860 points), but well-funded teams and Infisical are already there, and buyers won't trust a security product from one unknown developer | [HN](https://news.ycombinator.com/item?id=47911524); [HN](https://news.ycombinator.com/item?id=47865822) |
| Uptime checks, status pages, feature flags, email APIs | Free leaders exist (Uptime Kuma has about 90k stars), and developers say feature flags are easy enough to hardcode | [Notifier](https://notifier.so/guides/freshping-shutdown/); [HN](https://news.ycombinator.com/item?id=42899778) |
| On-call paging for tiny teams | A real gap since Opsgenie's shutdown was announced, but a pager can never go down, and phone and SMS costs are unknown | [HN](https://news.ycombinator.com/item?id=43285105) |
| AI tool for answering security questionnaires | A good AI project, but Vanta, Conveyor and SafeBase (now owned by Drata) already sell it | [Wolfia](https://wolfia.com/blog/vanta-reviews-pricing-alternatives) |
| Booking, review and inventory tools for small businesses | Users are angry about price hikes, but flat-priced challengers already exist, and non-technical buyers need sales calls | [SortTheClicks](https://sorttheclicks.com/fresha-reviews-reddit/); [InventoryQuick](https://inventoryquick.com/vs/inflow) |
| DMARC report analyzer (email authentication) | The gap is real (about 526k of 938k DMARC records still sit at p=none, which only monitors), but EasyDMARC, dmarcian and Valimail crowd it | [EasyDMARC](https://easydmarc.com/blog/dmarc-adoption-report-2026/) |

## Seven ranked opportunities, scored on both rubrics

Each idea is scored with the two rubrics from the hiring research. Each criterion gets 0–3 points. The hiring-value rubric has 8 criteria (maximum 24) and the solo-viability rubric has 7 (maximum 21). Four hiring criteria depend on how well you build: Used, Hygiene, Judgment and Defensible. For those, the score shows how strongly the idea pushes you toward them. Ideas are ranked by combined score (maximum 45). Ties are broken first by hiring score, because that is your main goal, and then by crowding, because you asked to avoid crowded categories.

| Rank | Opportunity | The problem in one line | Hiring /24 | Viability /21 | Total /45 |
|---|---|---|---|---|---|
| 1 | E-invoice preflight API | "Will this invoice pass the new legal format checks?" | 22 | 16 | 38 |
| 2 | Postgres restore drills | "Will our backups actually restore?" | 21 | 17 | 38 |
| 3 | Job outcome monitor for Python | "The job ran, but did it do its work?" | 21 | 17 | 38 |
| 4 | Consent behaviour monitor | "Does our cookie 'reject' button really block trackers?" | 22 | 13 | 35 |
| 5 | Webhook delivery for small SaaS | "Did our customers receive our events?" | 20 | 14 | 34 |
| 6 | Per-customer AI cost guard | "Is one customer eating our AI margin?" | 21 | 12 | 33 |
| 7 | Accessibility evidence scanner | "Can we show the work if someone sues under the EU Accessibility Act?" | 19 | 13 | 32 |

**Hiring-value scores**

| # | Opportunity | Not a clone | Used | Depth | Hygiene | AI | Judgment | Defensible | Stack | Total |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | E-invoice preflight API | 3 | 2 | 3 | 3 | 3 | 3 | 2 | 3 | **22** |
| 2 | Postgres restore drills | 3 | 2 | 3 | 3 | 1 | 3 | 3 | 3 | **21** |
| 3 | Job outcome monitor | 2 | 2 | 3 | 3 | 2 | 3 | 3 | 3 | **21** |
| 4 | Consent behaviour monitor | 3 | 2 | 3 | 2 | 3 | 3 | 3 | 3 | **22** |
| 5 | Webhook delivery | 2 | 2 | 3 | 3 | 1 | 3 | 3 | 3 | **20** |
| 6 | AI cost guard | 3 | 1 | 3 | 3 | 3 | 3 | 2 | 3 | **21** |
| 7 | Accessibility evidence scanner | 2 | 2 | 3 | 2 | 2 | 2 | 3 | 3 | **19** |

The columns mean:

- **Used:** the idea can realistically get real users, or at least show measurable usage.
- **Depth:** the backend work goes beyond CRUD: queues, retries, scheduling, caching.
- **Hygiene:** the idea forces tests, CI, logs and careful handling of secrets.
- **AI:** there is a natural place for an LLM to do one limited job, and the product still works without it.
- **Judgment:** there are real trade-offs worth writing up.
- **Defensible:** you can explain every decision in an interview.
- **Stack:** the idea fits Python, FastAPI or Django, Postgres, Redis, Docker and AWS.

**Solo-viability scores**

| # | Opportunity | Business buyer | Channel | Your access | Existing spend | Few rivals | Small scope | No ads needed | Total |
|---|---|---|---|---|---|---|---|---|---|
| 1 | E-invoice preflight API | 3 | 2 | 1 | 3 | 2 | 2 | 3 | **16** |
| 2 | Postgres restore drills | 3 | 2 | 3 | 2 | 2 | 2 | 3 | **17** |
| 3 | Job outcome monitor | 3 | 2 | 3 | 2 | 1 | 3 | 3 | **17** |
| 4 | Consent behaviour monitor | 3 | 1 | 1 | 2 | 2 | 2 | 2 | **13** |
| 5 | Webhook delivery | 3 | 1 | 2 | 3 | 1 | 2 | 2 | **14** |
| 6 | AI cost guard | 3 | 1 | 1 | 2 | 1 | 2 | 2 | **12** |
| 7 | Accessibility evidence scanner | 3 | 1 | 1 | 3 | 1 | 2 | 2 | **13** |

The columns mean:

- **Business buyer:** the customer is a business, not a consumer.
- **Channel:** there is a built-in way to reach users, such as an app marketplace, PyPI or one community you can reach.
- **Your access:** you are a user yourself, or you can easily reach buyers.
- **Existing spend:** buyers already pay for this, or work around the problem by hand.
- **Few rivals:** there are fewer than about 10 direct competitors, or you have a clear angle they miss.
- **Small scope:** you can ship it in 4–8 weeks.
- **No ads needed:** it can grow through communities and search.

### 1. E-invoice preflight API: laws with deadlines create the demand

**Demand.** Since January 2025, every German business must be able to *receive* structured e-invoices. *Issuing* them becomes mandatory on **1 January 2027** for firms above €800,000 turnover and on **1 January 2028** for the rest ([Advisori](https://www.advisori.de/en/blog/e-invoicing-mandate-germany)). France has required all firms to receive e-invoices since 1 September 2026, and SMEs must issue them from **1 September 2027** ([SoftCo](https://softco.com/blog/france-e-invoicing-2026-september-update/)). French reports put the fine at **€15 per non-compliant invoice** ([Journal de l'Économie](https://www.journaldeleconomie.fr/facturation-electronique-obligatoire-des-septembre-2026-9-millions-dentreprises-sur-11-nont-encore-rien-prepare-et-lamende-tombe-a-15e-par-facture/)). In Poland, penalties under the national KSeF system can reach 100% of an invoice's VAT from 1 January 2027 ([Crowe](https://www.crowe.com/pl/insights/ksef-jakie-kary-i-jak-ich-uniknac)).

Businesses are not ready. In one 2026 survey only 7% of French firms had finished every preparation step, and in another 38% said they were not ready ([Le Journal des Entreprises](https://www.lejournaldesentreprises.com/article/facturation-electronique-38-des-entreprises-ne-sont-pas-pretes-mais-letat-fera-preuve-de-tolerance-2146577); [Solutions Numériques](https://www.solutions-numeriques.com/facturation-electronique-obligatoire-en-2026-ou-en-sont-les-entreprises/)). A 2024/25 Bitkom survey found that only **45%** of German firms with 20 or more staff could receive e-invoices ([it-daily.net](https://www.it-daily.net/shortnews/weniger-als-die-haelfte-deutscher-unternehmen-empfaengt-e-rechnungen)). German users report invoices that fail validation, and embedded XML that disagrees with the PDF people see ([mehrwertsteuerrechner.de](https://www.mehrwertsteuerrechner.de/e-rechnung-pflicht/)). A 76-comment Hacker News thread on Peppol, the EU network many countries use to send e-invoices, called per-invoice fees "more expensive than the postal service". Commenters saw a gap for SMEs "that don't want to buy a comprehensive financial management solution" ([HN](https://news.ycombinator.com/item?id=42777669)).

**Competitors and gaps.** Free browser validators exist (mediaatelier, ecosio). Apify sells pay-per-use APIs at $4 per 1,000 Peppol checks and $50 per 1,000 parsed invoices ([Apify](https://apify.com/kamerozkan/peppol-bis-preflight-validator); [mediaatelier](https://www.mediaatelier.com/en/Tools/EInvoiceValidator/)). German bookkeeping suites such as lexoffice and sevdesk include e-invoice features ([mehrwertsteuerrechner.de](https://www.mehrwertsteuerrechner.de/e-rechnung-pflicht/)). The gap is twofold: Python tooling and plain-language explanations. The two main Python libraries, drafthorse and factur-x, check only the file structure (XSD). They do not check the business rules (Schematron) that real receivers enforce ([drafthorse](https://github.com/pretix/python-drafthorse); [factur-x](https://pypi.org/project/factur-x/2.2)). The official reference validator, from Germany's KoSIT, is a Java tool, and new rule versions come out every February and August ([toolkit notes](https://root.packagist.org/packages/daniel-jorg-schuppelius/php-erechnung-toolkit)). One HN commenter pointed out that access points (the services that pass invoices onto the Peppol network) check that "intermediate values are calculated and rounded correctly". That is exactly the kind of error a preflight check should catch first.

**Why it fits you.** The work is API-first XML and file processing, which Python handles well, and it needs little frontend. You stay legally safe by doing technical validation only. Becoming a Peppol access point or a French accredited platform requires audits or state approval, so you should not try to become one ([HN](https://news.ycombinator.com/item?id=42777669)).

**MVP.** Start with Germany only. Users upload or POST an invoice (XML or ZUGFeRD PDF). They get a full rule check with a plain-language fix for each error, plus a check that the XML matches the PDF. Add a generator that turns JSON or CSV into XRechnung or ZUGFeRD and validates its own output before returning it. A free web page brings in users, and API keys are the paid product.

**Skills shown.** An async processing pipeline, wrapping a Java tool inside a Python worker, versioned rule sets, an idempotent API with keys and rate limits, a test corpus in CI, and a limited AI step whose output a strict validator checks.

### 2. Postgres restore drills: backups nobody has tested

**Demand.** Restoredrill's Show HN (August 2026, 50 points, 23 comments) produced a story that sums up the problem. A daily cron job ran `pg_dump`, but when a restore was needed the backups "did not work", because the disk had filled up and new dumps were cut off ([HN](https://news.ycombinator.com/item?id=49465291)). Another developer said Postgres backup tools "all claim to support [point-in-time recovery] but then you actually need to restore and it's a mess" ([HN](https://news.ycombinator.com/item?id=46410656)). A self-hoster said they "would pay for that in a heartbeat" for easy recovery after a failure ([HN](https://news.ycombinator.com/item?id=46281391)). An Ask HN thread listed "Backup cron runs, exit code 0, but creates empty files" ([HN](https://news.ycombinator.com/item?id=46717618)).

**Competitors and gaps.** SimpleBackups charges $49/month for 5 backups and $299 for 100 ([SimpleBackups](https://simplebackups.com/pricing)). Open-source tools such as pgBackRest, Barman and WAL-G take backups but do not prove that they restore. Few products focus on verification, and Restoredrill is the one direct rival. A Postgres consultant in the same thread said "nearly nobody uses dumps as backups". To be taken seriously beyond small teams, the product will need to support WAL-based backups (copies of Postgres's write-ahead log, which allow point-in-time recovery).

**Why it fits you.** You are the first user, because every project you have built has a Postgres database. Python can run `pg_restore` into a throwaway Docker container, run SQL checks against it and report the results.

**MVP.** Connect an S3 bucket of `pg_dump` files. On a schedule, restore the newest dump, check row counts, the newest timestamp and any custom SQL, then send an alert and keep a dated report. The restore runner should be an open-source agent that runs inside the customer's own infrastructure, so you never hold their database credentials. This also keeps compute costs off your bill, which matters while Hetzner raises prices by 30–40% ([HN](https://news.ycombinator.com/item?id=47120145)).

**Skills shown.** Container orchestration, Postgres internals, secrets handling, scheduled jobs with timeouts and retries, and a strong security trade-off to write up (an agent in the customer's infrastructure versus restores you host). AI fits poorly here. At most, an LLM could summarise a failed restore log.

### 3. Job outcome monitor for Python: "exit code 0" is not success

**Demand.** A January 2026 Ask HN described the problem exactly: "my cron jobs 'succeed' but don't actually do their job correctly… Data sync completes successfully but only processes a fraction of records" ([HN](https://news.ycombinator.com/item?id=46717618)). That thread was small, but the complaint recurs. Another thread described "a scheduled job that someone wrote once and nobody fully trusts" ([HN](https://news.ycombinator.com/item?id=47868481)). The Django Control Room launch (134 points) drew a comment that the lack of a built-in monitor "is often a source of friction" ([HN](https://news.ycombinator.com/item?id=47151995)).

**Competitors and gaps.** This is the most crowded idea on the list, and the closest to the uptime monitor you rejected. Existing tools include Healthchecks.io (free for 20 jobs, $20 for 100) ([Capterra](https://www.capterra.com/p/249957/Healthchecksio/pricing/)), Cronitor ($2 per monitor plus $5 per user) ([Pulsetic](https://pulsetic.com/cronitor-alternative/)), Sigabrt (81 points in September 2026) ([HN](https://news.ycombinator.com/item?id=49765354)), CeleryRadar ([hunted.space](https://hunted.space/product/celeryradar)) and Flower. The difference is what gets checked. Heartbeat tools confirm that a job *ran*. This would check what it *produced*, such as rows, bytes and freshness, against the job's own history: "0 rows today, normally 10,000". A Sigabrt commenter asked for failure details beyond a heartbeat.

**Why it fits you.** It is Python-native. A decorator on a Celery, RQ or arq task sends a result record. The users are Python developers like you, so you can test it on your own projects.

**MVP.** A pip-installable SDK, a FastAPI endpoint that receives results, a baseline of normal output for each job, Slack and email alerts, and a heartbeat that warns you if the monitor itself goes quiet. The infrastructure stays modest: Healthchecks.io stores about 14M objects in 119 GB ([HN](https://news.ycombinator.com/item?id=47806348)).

**Skills shown.** Handling a high volume of incoming events, time-series queries, anomaly detection, alert de-duplication, and the deep Celery and Redis knowledge Python interviewers like to probe.

### 4. Consent behaviour monitor: does "reject" actually reject?

**Demand.** Regulators now test how a cookie banner behaves, not just whether one exists. In September 2025 France's CNIL fined Google €325m and Shein €150m. At Shein, cookies were set before consent and refusing did not work ([The Record](https://therecord.media/shein-google-fines-advertising-cookies-france-cnil)). That same month, California's privacy agency and the attorneys general of California, Colorado and Connecticut announced a joint check on whether sites honour the Global Privacy Control (GPC) browser signal. The agency settled with Tractor Supply for **$1.35m**, partly for ignoring it ([WilmerHale](https://www.wilmerhale.com/en/insights/blogs/wilmerhale-privacy-and-cybersecurity-law/20251017-california-privacy-protection-agency-issues-largest-monetary-penalty-to-date)). Buyers already pay for consent tools and are unhappy. Cookiebot roughly doubled its base price per domain in August 2025 and did not keep existing customers on old prices ([Enzuzo](https://enzuzo.com/blog/cookiebot-pricing)).

**Competitors and gaps.** The research did not map competitors in depth, so treat crowding as unknown. The angle is an independent test of whether a banner actually works, rather than the banner vendor checking its own product. US state privacy laws exclude most small firms. Rhode Island's law applies from 35,000 consumers, and Indiana's and Kentucky's from 100,000, with lower thresholds only for firms that make money selling data ([TrustArc](https://trustarc.com/resource/new-in-2026-state-privacy-laws-in-indiana-kentucky-and-rhode-island/)). So target mid-size online shops and the agencies that build their sites.

**Why it fits you.** Playwright has Python bindings. The work is headless browsing, job queues and storing evidence.

**MVP.** The user enters a URL. A headless browser loads the page three ways: with no consent given, after clicking "reject", and with the GPC signal turned on. Each time it records which trackers and cookies fire, saving screenshots and network logs as dated evidence. Weekly re-checks alert the user when something breaks. Report technical findings only, and never say a site is "compliant".

**Skills shown.** Browser automation at scale, worker queues, evidence storage on S3, comparing results over time, and a limited AI job: finding the reject button on an unfamiliar banner. You would measure that against a test set and fall back to fixed rules when the AI fails.

### 5. Webhook delivery: a $0-to-$490 pricing cliff

**Demand.** "The Valley of Webhooks" (August 2026, 247 points) summed up the frustration: "think of a webhook delivery as best-effort, a bit like UDP" ([HN](https://news.ycombinator.com/item?id=49184216)). A GitHub webhook incident thread reached 427 points ([HN](https://news.ycombinator.com/item?id=48010301)). One founder wrote that "debugging lost webhooks was a recurring nightmare" ([HN](https://news.ycombinator.com/item?id=46090343)).

**Competitors and gaps.** Svix's Free and Pro plans both include 50,000 messages a month, yet Pro costs **$490/month**. The extra money buys throughput, an SLA and an unbranded portal ([Toolradar](https://toolradar.com/tools/svix/pricing)). Hookdeck handles incoming webhooks for $39/month plus usage ([Toolradar](https://toolradar.com/tools/hookdeck/pricing)), and Hookdeck Outpost is open source ([HN](https://news.ycombinator.com/item?id=43904511)). The open slot is a service for *sending* webhooks to your customers, with signing, retries, a customer portal and replay, at $19–49/month.

**Why it fits you.** It is pure backend work: FastAPI, a queue in Postgres or Redis, workers and HMAC signatures.

**MVP.** An API takes events from a SaaS app, signs them and delivers them to customer endpoints. It retries with growing delays, moves repeated failures to a dead-letter queue, and has a portal where customers can view and replay deliveries.

**Skills shown.** The classic backend interview topics: at-least-once delivery, idempotency, retries, ordering, rate limiting and signing. The weakness is that the space is crowded, and companies trust event delivery only to proven vendors. Real users will be hard to get, so publish throughput and latency benchmarks as your proof instead.

### 6. Per-customer AI cost guard: spending caps sit in enterprise tiers

**Demand.** AI agent costs grow faster than usage. Two threads made this case: "Expensively Quadratic: The LLM Agent Cost Curve" (131 points) and "Why current LLM costs are not sustainable" (196 comments) ([HN](https://news.ycombinator.com/item?id=47000034); [HN](https://news.ycombinator.com/item?id=48683588)). Vendor guides say a small share of users drives a large share of LLM spend, which makes cost tracking per customer the basis for billing them. That claim comes from vendors and has no independent data behind it ([MetaCTO](https://www.metacto.com/blogs/llm-cost-attribution-per-user-feature)).

**Competitors and gaps.** Portkey offers "granular budget and rate limits" only in its Enterprise tier ([Portkey](https://portkey.ai/pricing)). Observability tools show spend but do not connect it to your billing. Be warned: launches of stand-alone cost trackers drew only 4–12 points ([HN](https://news.ycombinator.com/item?id=44856183); [HN](https://news.ycombinator.com/item?id=47381668)). Pitch this as protecting your margins and billing customers fairly, not as "see your token spend". LiteLLM, a popular Python package for calling many LLM providers, had compromised releases on PyPI (938 points) ([HN](https://news.ycombinator.com/item?id=47501426)). Since then, buyers prefer small components they can audit.

**Why it fits you.** It is an async Python proxy plus Redis counters and an export to Stripe.

**MVP.** A proxy that accepts the same requests as the OpenAI API. It tags each call with a customer ID, works out its cost, blocks calls once a customer hits a hard monthly cap, alerts at 80% of the cap, and sends usage to Stripe metered billing.

**Skills shown.** This is the strongest AI signal on the list: running LLM calls in production (streaming, fallbacks, token accounting), low-latency design for code that sits in the request path, atomic Redis counters and billing webhooks. It is also the weakest on viability. There is no built-in channel, demand is unclear, and gateways can add the feature.

### 7. Accessibility evidence scanner: overlays failed, so evidence matters

**Demand.** The European Accessibility Act (EAA) has applied since 28 June 2025, measured against the EN 301 549 standard, which maps to WCAG 2.1 AA. Very small service firms (under 10 staff and €2m or less in turnover) are exempt. A firm that claims accessibility would be a "disproportionate burden" must document that claim ([Taylor Wessing](https://www.taylorwessing.com/en/interface/2025/accessibility/key-eu-accessibility-act-exemptions-and-the-challenges-they-pose)). Courts are enforcing it. In June 2026 a French court ordered Carrefour to make its site and app accessible within six months, even though Carrefour claimed 71% conformance ([PinMeTo](https://www.pinmeto.com/news/eu-accessibility-act-enforcement-french-courts-2026/)). Overlay widgets, which add an accessibility toolbar on top of a site, lost credibility after the FTC reached a $1m settlement with accessiBe over its "automatic compliance" claims ([Grand River Solutions](https://grandriversolutions.com/ftc-1-million-dollar-settlement-case/)).

**Competitors and gaps.** Self-serve tools cost $38–89/month, and most are overlays ([FrontDeskReview](https://frontdeskreview.com/best/web-accessibility/)). Siteimprove costs about $12k–30k a year ([BrowserStack](https://www.browserstack.com/guide/siteimprove-alternatives)). UserWay's scanning-only plans cost $990–10,990 a year ([GetApp](https://www.getapp.com/all-software/a/userway-accessibility-monitor/)). The gap is a mid-priced real scanner with a dated evidence log. Many scanners already exist, though, so this is crowded.

**Why it fits you.** It is Playwright with the axe-core checker injected into each page, crawl workers and generated reports.

**MVP.** Crawl a site, run automated checks mapped to EN 301 549, store dated results, draft an accessibility statement and a list of fixes, and re-scan every month.

**Skills shown.** Crawling, queues, report generation, and an LLM step that writes plain-language fix suggestions. Never claim a site is "compliant".

## Why the e-invoice preflight API is the pick

Three ideas tie at 38 points. The e-invoice API wins the tie-break on both rules. It has the highest hiring score of the three, and its demand evidence is the hardest: laws with dates and per-invoice fines, plus readiness surveys. The other two rely on Hacker News threads with 8–134 points. Four reasons matter most for you.

**First, the demand does not depend on anyone liking your product.** A business must send valid invoices by a fixed date or face fines. The deadlines fall right when you would launch: Germany in January 2027 and 2028, France in September 2027, Poland's penalties in January 2027.

**Second, the gap is concrete and easy to check.** The main Python libraries skip business-rule validation, so a Python-native validator that explains its errors fills a hole you can point to in one sentence.

**Third, it forces nearly everything the hiring rubric rewards.** It needs file pipelines, versioned rules, a test corpus and an idempotent API. It also gives you the best AI story on the list: an LLM extracts fields from a plain PDF invoice, and a strict rule-based validator decides whether the result is valid. That addresses a real German complaint about extracting mandatory fields ([mehrwertsteuerrechner.de](https://www.mehrwertsteuerrechner.de/e-rechnung-pflicht/)). It also lets you answer the 2026 interview question "where does AI help and where does it fail?" with your own measurements.

**Fourth, no hiring manager has seen ten of these.**

The risks are real. You score 1 of 3 on access to buyers. If you live outside the EU, finding people to interview will be the hardest step. You will need to learn the EN 16931 standard. Free validators exist, so the paid value must be the API, the conversion and the explanations. The rules change twice a year. Nobody knows how many businesses already use free validators, so the size of the paid market is unknown. Stay clear of tax advice by reporting technical findings only. If validation fails, switch to the **Postgres restore drill** (#2). You are its first customer, it needs no domain access, and its interview story is equally strong apart from the AI part.

## Validate in two weeks, then build in eight

Talk to people before you write code. Several founders admitted spending weeks on architecture before speaking to a single customer ([HN](https://news.ycombinator.com/item?id=47803524)). Validate in four steps:

1. **Find complaints (days 1–3).** Collect 20 or more specific complaints from forums, competitor reviews and the Peppol thread above. Note who is complaining: freelancers, developers or bookkeepers.
2. **Hold 5–10 Mom Test conversations (days 4–10).** Talk to people who send invoices to German businesses or build invoicing software for them. The Mom Test rules are simple: ask about their past, not your idea. Ask "walk me through the last invoice that was rejected", not "would you use this?" For each person, record their current workaround, how often the problem happens and what it costs them ([mtlynch](https://mtlynch.io/book-reports/the-mom-test/)).
3. **Put up a one-page site with a concrete ask.** For example: "upload an invoice for a free check" and "join a paid API pilot". Count commitments such as uploads with an email address, pilot sign-ups and introductions. Do not count visits.
4. **Decide in advance what counts as success.** For example, at least 3 commitments from 10 conversations, or you switch ideas. No source validates an exact number, so treat it as a rule of thumb.

For payments, use a merchant of record (a service that handles billing and sales tax for you) and simple pricing, as experienced founders advise ([HN](https://news.ycombinator.com/item?id=47803524)).

| Week | What you build | What you can show at the end |
|---|---|---|
| 1 | FastAPI, Postgres and Docker Compose skeleton; CI with pytest; the KoSIT validator (or the Rust en16931-cli) wrapped behind one Python function; 30 or more valid and broken sample invoices saved as test cases | Tests passing against real invoices |
| 2 | Async pipeline: upload → S3 → Celery or arq worker → results table; job-status endpoint; idempotency keys; file size and type limits | Upload an invoice, check back for the result |
| 3 | Plain-language error catalogue (rule ID → meaning → fix); extract embedded XML from ZUGFeRD PDFs with factur-x and compare it with the PDF; free public validator page (Django templates or HTMX) | A free tool strangers can use |
| 4 | Generator: JSON or CSV → XRechnung or ZUGFeRD with drafthorse or factur-x; every generated file is validated before it is returned | A tested "never returns an invalid invoice" guarantee |
| 5 | Accounts, separate data per customer, API keys, Redis rate limiting, usage metering, billing with webhook handling | A paid API with real keys |
| 6 | Limited AI step: plain PDF → LLM extracts fields → draft XML → validator checks → user confirms; a test set of 50 invoices with field-level accuracy; manual form when the model is unsure | An accuracy number you measured yourself |
| 7 | Structured logs, metrics, error tracking, backups, pinned rule versions (new KoSIT rules arrive every February and August); deploy to AWS | A live URL, a dashboard and a runbook |
| 8 | README with an architecture diagram and 3–5 architecture decision records (ADRs); launch on Show HN and in German developer and freelancer communities; onboard your interviewees by hand | First real users and a public write-up |

## Conclusion

A verification product is useless if it is wrong, and that makes it a good portfolio project. It forces habits that junior candidates rarely get to show: a corpus of test cases, measured accuracy, monitoring and careful handling of failures. It also gives you an honest way to use AI: the model drafts, and strict rules decide. That pattern answers the question hiring managers now ask about AI better than any chatbot project, and it applies to every idea on this list, not only the top pick.

Deadlines fade, but this demand lasts. In Belgium, about **89%** of businesses that must use Peppol had registered by July 2026, and attention moved from signing up to sending correct data ([Brussels Times](https://www.brusselstimes.com/belgium/2256506/companies-not-yet-fined-for-not-joining-peppol-e-invoice-network/)). A validator serves that second phase. It outlasts each national deadline and grows when EU-wide e-invoicing for cross-border sales starts in July 2030 ([Eurofiscalis](https://www.eurofiscalis.com/en/intra-eu-e-invoicing-2030/)). The e-invoice idea therefore does not expire after the 2027 rush; the need for validation grows. The two-week test still matters. If you cannot get ten conversations with EU invoice senders, access to buyers is your real limit. In that case the restore-drill idea, where you are the customer, is the better bet.
