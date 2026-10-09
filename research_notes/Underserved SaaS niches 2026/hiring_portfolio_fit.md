# Hiring Value and Solo Viability: Criteria for Scoring a Portfolio SaaS Project (Backend/Python, 2025–2026)

Research date: 2026-10-09. Data vintage is marked for each item. "Older" means data from before 2025.

## What skills and technologies do 2025–2026 backend and Python job postings and hiring managers ask for?

### Takeaway
The standard 2025 backend stack is Python with FastAPI or Django, PostgreSQL, Docker, Redis and AWS. FastAPI, Docker, Redis and Python all grew sharply in the 2025 surveys. Job postings that mention AI are the one part of the US tech market that is growing (about 45% above the pre-pandemic level while all tech postings are 34% below it), and about one in five software-development postings now mentions AI. I found no rigorous public data on how often postings ask for Kubernetes, CI/CD, testing, observability or multi-tenancy.

### Cited Findings
**Stack Overflow Developer Survey 2025** (about 49,000 respondents from 177 countries, released July 2025; percentages are all respondents / professional developers)
- Python is used by 57.9% / 54.8%, up 7 percentage points from 2024, and the survey says Python's growth is "accelerating". SQL is at 58.6% / 61.3%. — [SO Survey 2025 – Technology](https://survey.stackoverflow.co/2025/technology/)
- Docker is at 71.1% / 73.8%, up 17 points, the largest one-year rise of any technology. The survey notes this is partly because it merged some categories. Kubernetes is at 28.5% / 30.1% and Terraform at 17.8% / 18.7%. — [SO Survey 2025 – Technology](https://survey.stackoverflow.co/2025/technology/)
- Cloud: AWS 43.3% / 45.9%, Azure 26.3% / 27.2%, GCP 24.6% / 24.3%. — [SO Survey 2025 – Technology](https://survey.stackoverflow.co/2025/technology/)
- Databases: PostgreSQL 55.6% / 58.2%, MySQL 40.5% / 39.6%, SQLite 37.5%, Redis 28% / 30.7% (usage growth reported as "+8%"), MongoDB 24%. — [SO Survey 2025 – Technology](https://survey.stackoverflow.co/2025/technology/)
- PostgreSQL has been the most admired and most desired database since 2023 (46.5% desired, 65.5% admired). This comes from a search summary of the official page; I did not see the admired/desired section myself. — [SO Survey 2025](https://survey.stackoverflow.co/2025/); see also [data-bene.io commentary](https://www.data-bene.io/en/blog/most-desired-database-three-years-running-postgresqls-developer-appeal/)
- Web frameworks: FastAPI 14.8% / 15.1% (up 5 points), Flask 14.4% / 13.2%, Django 12.6% / 11.7%. — [SO Survey 2025 – Technology](https://survey.stackoverflow.co/2025/technology/)
- AI tooling: OpenAI GPT models are used by 81.4%, Claude Sonnet by 42.8%, Cursor by 17.9%, Claude Code by 9.7%, Ollama by 15.3% and "RAG" by 10.6%. — [SO Survey 2025 – Technology](https://survey.stackoverflow.co/2025/technology/)
- Positive sentiment toward AI tools fell from over 70% (2023–2024) to about 60% in 2025. — [Stack Overflow blog, Aug 1 2025](https://stackoverflow.blog/2025/08/01/diving-into-the-results-of-the-2025-developer-survey/)

**JetBrains / PSF "State of Python 2025"** (published Aug 2025, based on the Python Developers Survey 2024, fielded Oct–Nov 2024, with more than 30,000 responses)
- FastAPI use rose from 29% to 38%, ahead of Django at 35% and Flask at 34%. PostgreSQL rose from 43% to 49%. Use cases: data analysis 48%, web development 46%, machine learning 41%. — [JetBrains PyCharm blog: State of Python 2025](https://blog.jetbrains.com/pycharm/2025/08/the-state-of-python-2025/); [JetBrains: most popular Python frameworks 2025](https://blog.jetbrains.com/pycharm/2025/09/the-most-popular-python-frameworks-and-libraries-in-2025/)
- 50% of respondents have less than 2 years of professional coding experience, so the Python talent pool is crowded at the junior end. — [JetBrains State of Python 2025](https://blog.jetbrains.com/pycharm/2025/08/the-state-of-python-2025/)
- The article describes a move toward async frameworks and ASGI servers (uvicorn, Hypercorn). It gives no percentage for async use. — [JetBrains State of Python 2025](https://blog.jetbrains.com/pycharm/2025/08/the-state-of-python-2025/)
- State of Django 2025 (4,600+ Django developers): HTMX use grew from 5% in 2021 to 24%, and Alpine.js from 3% to 14%. Server-rendered approaches are gaining ground again. — [JetBrains: State of Django 2025](https://blog.jetbrains.com/pycharm/2025/10/the-state-of-django-2025/)
- The FastAPI ecosystem still trails Django for ready-made pieces such as CMS and role-based access control. — [JetBrains frameworks article](https://blog.jetbrains.com/pycharm/2025/09/the-most-popular-python-frameworks-and-libraries-in-2025/)

**Job postings (US, Indeed Hiring Lab, Jan 22 2026, by Cory Stahle)**
- At the end of 2025, total US tech postings were 34% below February 2020, while tech postings that mention AI were about 45% above February 2020. — [Indeed Hiring Lab, Jan 2026](https://hiringlab.indeed.com/2026/01/22/january-labor-market-update-jobs-mentioning-ai-are-growing-amid-broader-hiring-weakness/)
- 20% or more of software-development postings mention AI. Indeed counts terms such as ML, GenAI, LLM and ChatGPT. Indeed's AI Tracker reached 4.2% of all postings in December 2025. The author suggests that highlighting AI skills "may be key" for finding work in 2026. — [Indeed Hiring Lab, Jan 2026](https://hiringlab.indeed.com/2026/01/22/january-labor-market-update-jobs-mentioning-ai-are-growing-amid-broader-hiring-weakness/)
- Unverified secondary claim: software postings are about 27.5% below the pre-pandemic level, 71% of the net increase between May 2025 and May 2026 came from senior roles, and 37% came from postings with AI in the title. I could not confirm these against Indeed's own material. — [OfficeChai summary of Indeed data](https://officechai.com/ai/us-software-job-postings-are-up-15-since-launch-of-claude-code-while-overall-job-postings-are-down-7-indeed-data/)
- A job-listing aggregator (published May 2026, methodology not disclosed) reports that Python roles list a median of 8 other technologies and that only 3% list Python alone. It also reports that SQL plus pipeline skills (Airflow, Spark, dbt) give 12–18% higher match scores than web-framework-only profiles. Its AWS figure is inconsistent: the search snippet says 62% of Python roles, but the page says about 34%. Treat this source as directional only. — [SeekerScore, May 2026](https://www.seekerscore.com/insights/python-developer-skills-2026)
- A UK H1 2025 recruiter talent report lists FastAPI, data-pipeline development, ML frameworks and AWS/Azure integration as emerging in-demand Python skills. — [OHO Group Python H1 2025 Talent Report](https://oho-group.sites.sourceflow.co.uk/talent-report/python-h1-2025-talent-report/)

**India (Naukri JobSpeak, 2026 monthly index of Naukri.com postings)**
- AI/ML hiring in IT was up 40% year on year in February 2026 and 37% in March, and up 45% for the full FY26. — [Naukri JobSpeak Feb 2026](https://naukri.com/blog/naukri-jobspeak-it-hiring-shows-meaningful-recovery-and-ai-momentum-continues-white-collar-market-posts-12-yoy-growth-in-february-2026/); [Naukri JobSpeak Mar 2026](https://www.naukri.com/blog/naukri-jobspeak-march-26-records-a-9-rise-in-white-collar-hiring-as-fy26-closes-at-8-the-strongest-job-growth-in-three-years/)
- AI/ML roles were up 22% in May 2026, with roles paying ₹30 LPA or more up 27%. Hyderabad led AI hiring growth at +44%, and AI/ML demand for the 13–16 years experience band grew 32%. — [Naukri JobSpeak May 2026](https://www.naukri.com/blog/naukri-jobspeak-may-2026-white-collar-hiring-remains-stable-in-may-ai-ml-roles-and-insurance-sector-continue-to-lead/)
- AI/ML roles were up 25% in June 2026 while overall IT hiring slowed. — [Naukri JobSpeak Jun 2026](https://www.naukri.com/blog/naukri-jobspeak-white-collar-hiring-grows-6-in-june-2026-ai-ml-and-fresher-hiring-lead-the-charge/)

### Inferences
- **Stack-alignment criterion.** A project scores highest when built on Python with FastAPI (or Django), PostgreSQL, Redis and Docker, deployed on AWS. Each of these is at or near the top of its 2025 category and growing. Kubernetes (about 29%) and Terraform (about 18%) are minority skills, so they are a bonus rather than a requirement for a portfolio.
- **AI-integration criterion.** AI-mentioning postings are the growth area in the US, and AI/ML is the strongest segment in India. A project with a real, bounded LLM component (RAG, extraction, classification or agents with tool calls) is therefore likely to score higher on hiring value than an equivalent project without one.
- **Data-pipeline adjacency.** About half of Python developers do data work, and one aggregator ties pipeline skills to better match scores. A SaaS with ingestion and ETL work (scheduled jobs, queues, batch processing) probably covers both "backend" and "data/AI platform" postings.
- **India-specific.** AI/ML demand is skewed toward senior roles and fresher growth is mostly outside IT, so a junior or mid-level candidate targeting India probably benefits most from a project that shows production AI/ML integration, not just CRUD.

### Gaps
- I found no rigorous 2025–2026 dataset giving the share of backend postings that require Kubernetes, CI/CD, pytest/testing, observability (OpenTelemetry, Prometheus), multi-tenancy, Stripe/payments or OAuth. Lightcast, LinkedIn or Dice data would be needed. Treat these as hiring-manager expectations rather than measured posting frequencies.
- I did not retrieve the Dice Tech Jobs Report or LinkedIn's 2025–2026 "Jobs on the Rise"/skills reports. Hired.com reports appear to have stopped after Hired was acquired; this is unconfirmed.
- I did not find a JetBrains Python Developers Survey 2025 publication (fieldwork late 2025) in this search. The latest figures above are from 2024 fieldwork.
- Exact Stack Overflow admired/desired figures for Redis and FastAPI were not verified on the official page.

## What makes a side project impressive versus generic to hiring managers and senior engineers?

### Takeaway
The current guidance agrees on what counts: real users or measurable outcomes, real technical depth (scale, benchmarks, failure handling), and written evidence of engineering judgment such as a design write-up. Tutorial clones (to-do, weather, Netflix or Spotify clones, basic CRUD) and half-finished repos count against a candidate. Since AI makes code cheap, deciding what to build and being able to defend it in an interview now carries most of the weight. Projects matter most for new grads and career switchers, less for mid-level candidates, and seniors usually omit them.

### Cited Findings
- **By career level** (techinterview.org, Apr 26 2026, updated Jun 30 2026): new grads and career switchers should list 2–3 substantial projects, mid-level engineers 1–2 projects as one-liners, and senior/staff engineers usually none, apart from one truly notable project. — [techinterview.org](https://www.techinterview.org/post/3233474610/side-projects-open-source-engineering-resume/)
- **What counts as impressive** (same source): open source with measurable adoption, and personal projects with real technical depth such as "a database or storage layer with real benchmarks, an ML model serving real users, or a system handling non-trivial scale". Write-ups and design-tradeoff docs also count because they "let reviewers verify engineering judgment". Each project bullet should give an outcome: scale, users, or a notable technical decision. — [techinterview.org](https://www.techinterview.org/post/3233474610/side-projects-open-source-engineering-resume/)
- **What counts as generic or harmful** (same source): tutorial or course projects, todo/weather/recipe/basic CRUD apps, half-finished repos with thin READMEs or stale commits, trivial contributions such as typo fixes, and "projects you can't discuss in depth under interview pressure". — [techinterview.org](https://www.techinterview.org/post/3233474610/side-projects-open-source-engineering-resume/)
- The same source suggests a test: would a hiring manager learn something the work-history bullets don't already show? If there are no users, report technical scale instead (data volume, latency), or get a few real users (friends, a subreddit, a beta) and say so. This comes from the search summary of the article. — [techinterview.org](https://www.techinterview.org/post/3233474610/side-projects-open-source-engineering-resume/)
- Arslan Ahmad (May 7 2026) lists three projects that impress: (1) a tool that solves a real annoyance in your life, (2) a merged open-source PR, and (3) "a tiny AI-integrated feature in a real app" where the AI does one bounded job and the app is useful without it. Weather apps, to-do lists and Netflix/Spotify clones signal "tutorial follower", and recruiters "recognize clones within seconds". Because "anyone with a Copilot subscription can produce code", judgment about what to build is the differentiator. — [Arslan Ahmad, Substack](https://arslandg.substack.com/p/3-portfolio-projects-that-actually)
- A hiring-lead essay (June 2026) on early-career AI builders says managers want people who "can show finished work, explain decisions, and point out where AI helped or fell short". Useful artifacts include demos, repos, decision logs, prompt traces, user feedback and postmortems, and "a builder who knows when to stop, verify, simplify" is safer to hire than one who names tools. This comes from a search summary; I did not fetch the page. — [provn.co, Jun 2026](https://provn.co/blog/2026/06/hiring-manager-expectations-ai-builders)
- Dice career advice: another "Spotify clone or scheduling tool" will not set a candidate apart. This is an older piece; the original appears to be from June 2021. — [Dice](https://www.dice.com/career-advice/essential-steps-for-turning-side-projects-into-job-offers); [Dice Insights 2021 original](https://insights.dice.com/2021/06/14/essential-steps-for-turning-side-projects-into-job-offers/)
- An experienced developer on the freeCodeCamp forum says that for experienced developers the "proof" is mostly in the interview conversation. This is older and anecdotal. — [freeCodeCamp forum](https://forum.freecodecamp.org/t/how-do-experienced-developers-create-resume/555688)

### Inferences
**Proposed hiring-value rubric**, derived from the findings above and the stack data in section 1. Score each item 0–3.
1. **Not a clone.** The project solves a specific, real problem for a named user group, not a to-do, weather or streaming clone.
2. **Deployed and used.** It has a live URL with real users, paying users, or at least measurable usage. If there are no users, it shows benchmarked scale such as throughput, latency or data volume.
3. **Backend depth beyond CRUD.** It includes async I/O, background workers or queues, Redis caching or rate-limiting, idempotent webhooks, scheduled jobs, and handling of retries and failures. These are what make a system "handling non-trivial scale" believable.
4. **Production hygiene.** It has tests and CI, a Dockerized deploy, migrations, structured logs, metrics or traces, and secrets handling. No posting-frequency data was found for these; the case for them is that "abandoned repo" and "minimal README" are named as negatives.
5. **Bounded AI component.** An LLM does one clear job with evaluation and fallbacks, and the product still works without it.
6. **Visible judgment.** The README has an architecture diagram, ADRs or a design-tradeoffs section, and a postmortem or write-up.
7. **Defensible under questioning.** The candidate can explain every major decision live. AI-assisted interview cheating has made interviewers sceptical (see section 3).
8. **Stack alignment** with Python, FastAPI or Django, Postgres, Redis, Docker and AWS (section 1).

- SaaS-specific elements such as multi-tenancy, auth/RBAC and Stripe billing with webhooks are a natural way to meet criteria 3 and 4 in one project. That is my inference; I found no posting data.

### Gaps
- I could not retrieve first-hand Reddit threads from r/cscareerquestions, r/ExperiencedDevs, r/Python or r/learnprogramming, because search returned only secondary summaries. An HN Algolia search for 2025–2026 Ask HN threads specifically on "side projects and hiring" returned no strong matches. Community opinion here therefore rests on blogs and articles, several of which are SEO content.
- I found no controlled data showing that side projects change interview or offer rates. One anecdote (34% of 150 interviewed engineers had a side project) is from an unrepresentative sample. — [DEV Community](https://dev.to/dannyhabibs/having-impressive-side-projects-lets-big-tech-recruiters-know-you-are-self-motivated-2khj)

## How did the 2025–2026 junior and mid-level market change with AI coding tools, and what differentiates candidates now?

### Takeaway
Early-career software employment in the US has fallen sharply since late 2022. Developers aged 22–25 are down nearly 20% from their peak, while older cohorts grew. Big Tech new-grad hiring roughly halved as a share of hires. Hiring managers report that AI cheating has weakened both live-coding and take-home signals, so referrals, direct outreach, in-person or paid trial work, and demonstrable proof of work count for more. India shows strong AI/ML demand, but it is concentrated in senior roles.

### Cited Findings
- **Stanford Digital Economy Lab**, "Canaries in the Coal Mine?" (Brynjolfsson, Chandar, Chen; ADP payroll data; Nov 13 2025 version): workers aged 22–25 in AI-exposed occupations saw a 16% relative employment decline after controlling for firm-level shocks, while experienced workers were stable. The adjustment came through employment rather than pay, and was concentrated where AI automates rather than augments work. — [Stanford paper PDF, Nov 2025](https://digitaleconomy.stanford.edu/app/uploads/2025/11/CanariesintheCoalMine_Nov25.pdf)
- In the same study, employment of software developers aged 22–25 fell nearly 20% from the late-2022 peak, while workers aged 35–49 in exposed jobs grew by more than 8%. This comes from secondary coverage of the paper. — [SF Standard, Aug 27 2025](https://sfstandard.com/2025/08/27/ai-entry-level-jobs-decline/); [Stanford paper PDF](https://digitaleconomy.stanford.edu/app/uploads/2025/11/CanariesintheCoalMine_Nov25.pdf)
- A Stanford follow-up (Feb 9 2026) concludes that interest rates "are not a good explanation" for the disproportionate fall in entry-level hiring in AI-exposed occupations. The evidence is still correlational. — [Stanford DEL, Feb 2026](https://digitaleconomy.stanford.edu/news/canaries-interest-rates-and-timinga-more-on-recent-drivers-of-employment-changes-for-young-workers)
- **SignalFire State of Talent** (2025): new grads make up about 7% of Big Tech hires, down from 15% before the pandemic. Engineers were 55% of new hires at the 12 "Tech Majors" in 2025, up from 46% in 2019, and engineering hiring fell less (−11%) than overall hiring (−25% vs 2019). These figures come via secondary coverage. — [SF Standard, Aug 2025](https://sfstandard.com/2025/08/27/ai-entry-level-jobs-decline/); [Enterprise DNA summary](https://enterprisedna.co/resources/news/ai-engineering-jobs-resilient-signalfire-2026)
- **The Pragmatic Engineer** (Gergely Orosz, Apr 15 2025): managers find hiring "harder than ever" despite more applicants, because postings are flooded with poor matches. Live coding has lost signal because of teleprompter and overlay tools. In one case all four take-home submissions included an invisible planted instruction, and three of those candidates denied using AI. One scaleup fired a senior data engineer who used AI tools during interviews and is weighing in-person final loops at $1,500–2,000 per candidate. 4 of its last 5 hires came through referrals. Paid week-long trials were "largely unaffected", and the best signals were direct, specific outreach and "proof of humanity". — [Pragmatic Engineer, Apr 2025](https://newsletter.pragmaticengineer.com/p/tech-hiring-inflection-point)
- AI-generated résumés and cover letters make applicants sound alike, so polished applications carry less weight. Hiring has moved toward referrals, personal projects, live assessments and in-person interviews. This comes from a search summary; I did not fetch the page. — [provn.co, Jun 2026](https://provn.co/blog/2026/06/hiring-manager-expectations-ai-builders)
- 49% of developers plan to try AI coding agents in the coming year (JetBrains State of Developer Ecosystem 2025). — [JetBrains State of Python 2025](https://blog.jetbrains.com/pycharm/2025/08/the-state-of-python-2025/)
- **India**: fresher (0–3 years) hiring across all sectors grew 8–17% year on year in each month from January to June 2026. In May the growth was driven mainly by hospitality, retail and BPO/ITES, not core IT. IT fresher hiring rose 8% in February 2026. — [Naukri JobSpeak Jan 2026](https://naukri.com/blog/naukri-jobspeak-white-collar-hiring-opens-2026-with-3-yoy-growth-driven-by-non-it-sectors-and-fresher-hiring/); [Naukri JobSpeak Feb 2026](https://naukri.com/blog/naukri-jobspeak-it-hiring-shows-meaningful-recovery-and-ai-momentum-continues-white-collar-market-posts-12-yoy-growth-in-february-2026/); [Naukri JobSpeak May 2026](https://www.naukri.com/blog/naukri-jobspeak-may-2026-white-collar-hiring-remains-stable-in-may-ai-ml-roles-and-insurance-sector-continue-to-lead/)

### Inferences
- Code volume no longer differentiates a candidate. What does: (a) evidence that cannot easily be faked by AI, such as live users, a production incident history, and a public repo history with meaningful commits; (b) the ability to defend design decisions live; and (c) channels that bypass résumé screening, such as referrals, direct outreach and open-source PRs. A portfolio SaaS with real users gives the candidate concrete talking points for direct outreach.
- Entry-level hiring is shrinking while engineering hiring overall is steadier and tilted toward experience. A junior candidate's project should therefore show work normally associated with mid-level engineers: operations, reliability, and tradeoff reasoning.
- Showing honest, critical use of AI tools (where AI helped and where it failed, with evaluations) is itself a positive signal according to the 2026 hiring-lead commentary. This suggests documenting the AI-assisted workflow rather than hiding it.

### Gaps
- I did not read SignalFire's 2025 report directly; its figures come from secondary coverage.
- I found no hard data specifically on mid-level (3–6 years) backend hiring changes. The Stanford study separates cohorts by age, not by job level.
- I found no Reddit primary threads (see section 2).

## What do Indie Hackers and micro-SaaS data say about typical solo SaaS outcomes, fastest niches to first revenue, and failure modes?

### Takeaway
There is little rigorous outcome data for solo SaaS. The best structured source is MicroConf's State of Independent SaaS (2024 edition, about 700 founders). It shows that bootstrapped SaaS is mostly solo-founded, that companies selling to enterprise, mid-market and SMB customers grow much faster than consumer or education ones, and that paid ads are slow to pay back. Founder commentary from 2026 consistently says distribution, not building, is the bottleneck, that escape velocity takes 18–24 months or more, and that AI has filled most obvious niches with 10–20 competitors. The fastest path to first revenue reported by practitioners is a small product sold through a built-in marketplace channel, or a vertical B2B tool where the founder has domain access.

### Cited Findings
**MicroConf State of Independent SaaS 2024** (just under 700 usable responses from MicroConf, TinySeed and SFTRU audiences; discussed on Startups for the Rest of Us episode 721, July 9 2024; older than 2025)
- Roughly 70% of respondents were single founders and 15% or more had two founders. Rob Walling was not certain of the exact figures. Solo founders averaged about 17% month-over-month growth. — [SFTRU Ep. 721](https://www.startupsfortherestofus.com/episodes/episode-721-7-key-takeaways-from-the-2024-state-of-independent-saas-report)
- Average month-over-month growth by target market: enterprise about 26%, SMB about 12%, consumer about 5%, government about 1.75%. The fastest-growing markets were enterprise, mid-market and NGOs. The slowest were aspiring entrepreneurs, education, consumers and government. — [SFTRU Ep. 721](https://www.startupsfortherestofus.com/episodes/episode-721-7-key-takeaways-from-the-2024-state-of-independent-saas-report)
- By business model: free trials requiring a credit card had the highest month-over-month growth (about 14%) and about 5.5% monthly churn. Freemium had about 11% monthly churn. Free trials without a card had about 6.3% churn but the highest LTV (about $6.5K vs about $3–3.6K). 71% of companies require a card for trials. — [SFTRU Ep. 721](https://www.startupsfortherestofus.com/episodes/episode-721-7-key-takeaways-from-the-2024-state-of-independent-saas-report)
- Among founders running ads, Google Ads was most often cited as raising revenue (about 65%), then Meta (about 30%), with LinkedIn fourth. — [SFTRU Ep. 721](https://www.startupsfortherestofus.com/episodes/episode-721-7-key-takeaways-from-the-2024-state-of-independent-saas-report)
- Of founders who run ads, 57% either wait 7 months or more to see ROI or can't tell whether the ads work. This is MicroConf survey data as cited by Freemius; it is probably 2024 data. — [Freemius State of Micro-SaaS 2025](https://freemius.com/blog/state-of-micro-saas-2025/)
- 20% of bootstrapped SaaS exits happen at $1M–$3M ARR (2024 report). — [MicroConf pre-revenue page](https://microconf.com/founders/pre-rev)
- A full 2025 or 2026 edition of the report was not found; the latest public edition is 2024, and the results are gated behind a form. — [MicroConf State of Indie SaaS](https://microconf.com/state-of-indie-saas)

**Solo-founder trend (Carta Solo Founders Report, Dec 9 2025; US startups on Carta, a VC-oriented sample)**
- Solo-founder share of new startups rose from 23.7% (2019) to 36.3% (H1 2025). Solo founders were 30% of 2024 startups but received only 14.7% of priced-round cash. The median time from incorporation to first hire is 399 days for solo founders. Carta's 2026 Founder Ownership Report uses slightly different figures (31% in 2024, 36% in 2025). — [Carta Solo Founders Report 2025](https://carta.com/data/solo-founders-report)

**Founder commentary (HN "Ask HN: Building a solo business is impossible?", Apr 17 2026, 78 points, 93 comments)**
- The original poster says "build, and they will come" failed despite SEO and outreach. Commenters: "Distribution is the whole game"; "building the thing is only 10 percent of the battle"; doing "sales at the same time as shipping" is the trap for one person. — [HN 47803524](https://news.ycombinator.com/item?id=47803524)
- Success stories in the thread come from founders with domain access. One built 7 years of solo SaaS from an internal app and reached about 80 dealerships in 13 states, having been "the first best customer of your own product". Another shipped a B2B vertical platform alone in 12 months, with paying customers, using prior domain knowledge. A bootstrapped B2B founder at single-digit millions ARR says escape velocity typically takes 18–24 months. — [HN 47803524](https://news.ycombinator.com/item?id=47803524)
- Failures in the thread: a martial-arts SaaS and a chess extension got about zero adoption (2 installs), there were 2 years on a P2P marketplace, and founders spent weeks on architecture before talking to anyone. Commenters say "almost everything with clear use has been built", with 10–20 competitors per niche, and that "AI slop" makes it harder for good products to reach users. Advice offered: pick a beachhead market where customers refer each other; choose B2B markets that are "not attractive to VCs"; mine industry subreddits for pain posts; use a merchant of record and simple pricing. — [HN 47803524](https://news.ycombinator.com/item?id=47803524)

**Stair Step Approach (Rob Walling, originally around 2015, reprinted by MicroConf; older)**
- First-time founders mostly fail by building something too complex. The recommendation is a simple first product with one traffic channel, often an add-on to an existing ecosystem (WordPress plugin, Shopify app) because of "built in discovery through the plugin repository or app store". Recurring-revenue SaaS comes later because "there's a long ramp to any kind of substantial revenue". — [MicroConf: The Stair Step Approach](https://microconf.com/latest/the-stairstep-approach-to-bootstrapping)

**Weak or unverified figures (use with caution)**
- "The median indie SaaS generates only $145/month" and "70% of indie developers fail" come from a vendor blog with no traceable source. — [Fungies.io](https://fungies.io/indie-developer-market-2026-complete-analysis-data-trends-forecasts-8/)
- Indie Hackers' 2021 thread on "$60M in Stripe-verified ARR" shows the aggregate is real, but the claim that it follows the Pareto principle is a commenter's guess. This is older. — [Indie Hackers](https://www.indiehackers.com/post/indie-hackers-are-making-60-million-in-stripe-verified-arr-bac07f782d)

### Inferences
**Proposed solo-viability rubric.** Score each item 0–3.
1. **Business buyer.** The buyer is a business (SMB, mid-market or vertical professional), not a consumer, student, aspiring entrepreneur or government. MicroConf growth data supports this.
2. **Built-in distribution channel.** There is a marketplace or app store (Shopify, Chrome Web Store, Slack, HubSpot, Zapier, WordPress, GitHub Marketplace) or one reachable community. This follows the Stair Step approach and the HN "distribution is the whole game" comments.
3. **Founder access.** The founder has domain knowledge, network access, or is a user. Every HN success had this.
4. **Existing spend or workaround.** Buyers already pay for, or manually work around, the problem (Mom Test, section 5).
5. **Low competitive density.** There are fewer than about 10 direct competitors, or a clear wedge (a vertical, region or integration gap). The HN "10–20 competitors per niche" observation supports this.
6. **Small and simple.** The scope is shippable in about 4–8 weeks with simple pricing and a merchant of record (Stair Step; HN pricing advice).
7. **Patient channel.** The plan does not depend on paid ads, given that 57% of founders running ads see slow or unclear ROI.

- Realistic expectation: most solo micro-SaaS products do not replace a salary within the first year. Practitioners cite 18–24 months to escape velocity for B2B. A portfolio project that reaches even a few paying customers is a strong hiring signal (section 2), so the two goals reinforce each other even if the business never scales.
- Niches that probably reach first revenue fastest: ecosystem add-ons with marketplace discovery, and narrow vertical B2B tools where the founder already knows buyers. This is an inference from Walling and the HN thread, not measured data.
- Common failure modes in the evidence: building before talking to customers; consumer or "aspiring entrepreneur" markets; crowded horizontal categories, now more crowded because of AI; relying on SEO or ads with long payback; and treating architecture as progress.

### Gaps
- I found no rigorous public dataset on median time to first dollar, $1K MRR or $10K MRR for solo SaaS. The detailed MicroConf 2024 tables are gated.
- I found no verified 2025–2026 Indie Hackers or Stripe distribution of solo SaaS revenue.
- I found no data ranking niches by time to first revenue.

## How should a solo developer validate a SaaS idea quickly before building?

### Takeaway
Use The Mom Test for interviews. Talk about the other person's life and past behaviour rather than your idea, and end each conversation by asking for a commitment that costs them something: time, reputation, or money (LOI, pre-order, deposit). Treat "I would use that" as noise. Practitioners also suggest mining industry communities for pain posts and manually onboarding the first users.

### Cited Findings
- **Mom Test rule 1: talk about their life, not your idea.** Pitching early makes people evaluate your concept instead of describing what actually happens to them. — [mtlynch book report on The Mom Test](https://mtlynch.io/book-reports/the-mom-test/); [Indie Hackers summary](https://www.indiehackers.com/post/the-mom-test-summary-850d61ebcf)
- **Rule 2: ask about specifics in the past, not opinions about the future.** Instead of "Would you buy this?", ask how they handle the problem today, what they have tried, and what they have already paid for. People are overly optimistic about hypothetical purchases. — [mtlynch](https://mtlynch.io/book-reports/the-mom-test/); [DEV summary](https://dev.to/sandro_vol/the-mom-test-how-to-talk-to-customers-a-summary-17o2)
- **Rule 3: talk less, listen more.** If you are talking more than they are, that is a red flag. — [Indie Hackers 5-step summary](https://www.indiehackers.com/post/how-to-nail-customerconversations-and-validateyour-business-idea-5-simplesteps-from-the-mom-test-4b90231a94)
- **Commitment ladder.** Time: a next meeting, reviewing wireframes, trialling the product. Reputation: an intro to peers or the decision-maker, a testimonial. Money: an LOI, pre-order or deposit. A prospect who won't commit has still given you a clear answer. For feature requests, ask "Why do you want this?" and "How are you coping without it?" — [mtlynch](https://mtlynch.io/book-reports/the-mom-test/); [koji.so Mom Test guide](https://www.koji.so/docs/mom-test-user-interviews)
- **Practitioner tactics (HN, Apr 2026):** spend about two weeks reading industry subreddits for frustrated pain posts. Look for a strong reaction when you describe the problem before mentioning any solution. Drop ideas quickly if there is no reaction. Do in-person conversations and manual onboarding. Several commenters admitted building or architecting for weeks before speaking to a customer. — [HN 47803524](https://news.ycombinator.com/item?id=47803524)
- **Keep the first product small** so it can be validated through one channel (Stair Step, older). — [MicroConf Stair Step](https://microconf.com/latest/the-stairstep-approach-to-bootstrapping)

### Inferences
**Compact validation sequence for a time-boxed solo developer** (my synthesis of the sources above)
1. Pain mining (2–5 days): collect 20 or more specific complaints from forums, subreddits, reviews of competitors, and app-store reviews.
2. Mom Test interviews: 5–10 conversations about past behaviour. Record the current workaround, how often it happens, and money or time spent.
3. Landing page or waitlist with a concrete ask such as a demo call, beta slot or paid pilot. Measure commitments, not visits.
4. Pre-sale: an LOI, discounted annual pre-order, or paid concierge or manual version before full automation.
5. Kill or continue: set a threshold in advance, for example at least 3 commitments from at least 10 conversations. The threshold is illustrative; no source gives a validated number.

- A scoring criterion follows: an idea scores higher on viability if its buyers are reachable for interviews and have visible existing spend or workarounds.

### Gaps
- I did not retrieve primary sources with conversion benchmarks for landing-page smoke tests (for example, what sign-up or pre-order rate counts as validated). No benchmark is cited here.
- I did not read the Mom Test book directly; the points above come from consistent secondary summaries.
- I did not find 2025–2026 data on how often solo founders who pre-sell outperform those who don't.
