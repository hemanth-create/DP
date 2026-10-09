# AI-era problems and tooling gaps (2025–2026): where a solo Python developer could build a SaaS

Research date: 2026-10-09. HN points and comment counts were pulled from the HN Algolia API on 2026-10-09, so they are a snapshot. GitHub stars came from the shields.io badge JSON on 2026-10-09; the GitHub API itself was blocked in this environment. Pricing comes from vendor pricing pages fetched on 2026-10-09 unless a different source is named. Show HN point counts are low for most infra tools. That reflects how HN works as much as demand, so read them as relative signals only.

## Q1. What do teams struggle with when running LLM features and AI agents in production?

### Takeaway
The production pains with the most discussion in 2025–2026 are: (a) agent safety and permissions (agents destroying data, prompt injection, MCP supply-chain attacks); (b) cost that grows non-linearly with agent context; (c) unreliable inference providers behind gateways like OpenRouter (silent empty responses, quality varying by host, IP-based 429s); (d) the infrastructure burden of self-hosting observability; and (e) MCP auth, scopes and analytics. Prompt management and PII redaction look like real needs, but stand-alone launches in those two areas draw almost no engagement.

### Cited Findings

**Agent safety, permissions and auditing (strongest engagement signal)**
- "An AI agent deleted our production database. The agent's confession is below": 860 pts, 1,032 comments (2026-04-26). Commenters stressed operator responsibility: "your agents are your responsibility", and noted that backups were stored on the same volume and that the agent found secrets "wherever they happen to be". — [HN](https://news.ycombinator.com/item?id=47911524)
- "The 'S' in MCP Stands for Security": 730 pts, 183 comments (2025-04-06). — [HN](https://news.ycombinator.com/item?id=43600192)
- A malicious Postmark MCP npm package that downloaded users' emails: 308 pts (2025-09-27). — [HN](https://news.ycombinator.com/item?id=45395957); [Koi Security](https://www.koi.security/blog/postmark-mcp-npm-malicious-backdoor-email-theft)
- "Google Antigravity exfiltrates data via indirect prompt injection": 768 pts (2025-11-25). Other prompt-injection incidents: GitLab Duo, 214 pts (2025-05-23), and a GitHub Copilot RCE (CVE-2025-53773), 128 pts (2025-10-12). — [HN Antigravity](https://news.ycombinator.com/item?id=46048996); [HN GitLab Duo](https://news.ycombinator.com/item?id=44070626); [HN Copilot](https://news.ycombinator.com/item?id=45559603)
- Show HN "Agent Vault – open-source credential proxy and vault for agents" (Infisical): 156 pts (2026-04-22), 2.3k GitHub stars. — [HN](https://news.ycombinator.com/item?id=47865822); [GitHub](https://github.com/Infisical/agent-vault)
- Show HN "MCP-Shield – detect security issues in MCP servers": 134 pts (2025-04-15). — [HN](https://news.ycombinator.com/item?id=43689178)
- Show HN "An MCP Gateway to block the lethal trifecta" (Open Edison): 51 pts (2025-09-12). It classifies tools on three axes (private data, untrusted content, external comms) and blocks a session when all three line up. Commenters were skeptical: "Wouldn't the LLM running in the gateway also be susceptible to the same jailbreaks?", and "So is any combination of MCP servers basically going to require human in the loop approval for everything?" — [HN](https://news.ycombinator.com/item?id=45223102)
- "12-factor Agents: Patterns of reliable LLM applications": 475 pts (2025-04-15). "What makes 5% of AI agents work in production?": 126 pts, 121 comments (2025-10-02). — [HN 12-factor](https://news.ycombinator.com/item?id=43699271); [HN 5%](https://news.ycombinator.com/item?id=45456381)

**Cost (agent cost curves, per-customer attribution, budgets)**
- "Expensively Quadratic: The LLM Agent Cost Curve": 131 pts (2026-02-13). "Why current LLM costs are not sustainable": 116 pts, 196 comments (2026-06-26). — [HN quadratic](https://news.ycombinator.com/item?id=47000034); [HN unsustainable](https://news.ycombinator.com/item?id=48683588)
- Show HN "Context Gateway – compress agent context before it hits the LLM": 97 pts, 64 comments (2026-03-13). — [HN](https://news.ycombinator.com/item?id=47367526)
- Stand-alone cost-tool Show HNs got little traction: Llmswap (caching), 12 pts (2025-08-10); AgentReady (token-cutting proxy), 8 pts (2026-02-23); PreflightLLMCost, 5 pts (2025-06-28); Costly (OSS cost audit SDK), 4 pts (2026-03-14); Slash-tokens (pre-call cost), 4 pts (2026-08-25). — [HN Llmswap](https://news.ycombinator.com/item?id=44856183); [HN AgentReady](https://news.ycombinator.com/item?id=47122083); [HN PreflightLLMCost](https://news.ycombinator.com/item?id=44403725); [HN Costly](https://news.ycombinator.com/item?id=47381668); [HN Slash-tokens](https://news.ycombinator.com/item?id=49441725)
- Vendor guides describe per-customer cost attribution as a recognized need: "a small fraction of users typically drives a large fraction of LLM spend", and per-tenant attribution is "the basis for chargeback and invoicing". The tool categories they list are gateways (Portkey, Bifrost, TrueFoundry, LiteLLM, Cloudflare AI Gateway), observability platforms (Helicone, Langfuse, Braintrust, Phoenix, Datadog), FinOps tools (CloudZero, Amnic) and usage-metering primitives (OpenMeter). These guides are written by vendors in the space. — [MetaCTO](https://www.metacto.com/blogs/llm-cost-attribution-per-user-feature); [Amnic](https://amnic.com/blogs/llm-cost-allocation-tools); [FutureAGI](https://futureagi.com/blog/best-llm-cost-tracking-tools-2026/)

**Gateways, fallbacks and provider reliability**
- "So you want to use OpenRouter?" (Mo Moustafa, 2026-09-07): 766 pts, 207 comments (HN, 2026-09-09). The author's iMessage assistant has handled 18M+ messages, about a third through OpenRouter. Problems reported:
  - Quality varies by host for the same weights. DeepSeek V4 Flash scored 81.3% on TAU-Bench Airline from the first-party provider and 58.4% from DigitalOcean, and one host scored 46%.
  - Some hosts "didn't see" images but still returned 200 OK.
  - The `reasoning.effort` setting is accepted but ignored by some hosts.
  - Malformed tool calls arrive as raw text.
  - Some 200 responses come back with no content and no usage data. One provider carried ~20% of traffic but produced 92% of the empty completions in July.
  - History rules differ by provider (400 errors).
  - Some providers rate-limit by IP: 429s from the production servers, but the same key worked from a laptop.
  - Pinning providers with fallbacks disabled caused a full outage.
  — [Blog](https://mmoustafa.com/blog/so-you-want-to-use-openrouter/); [HN](https://news.ycombinator.com/item?id=49621546)
- LiteLLM supply-chain compromise: "Litellm 1.82.7 and 1.82.8 on PyPI are compromised", 938 pts, 500 comments (2026-03-24). A follow-up incident write-up drew 441 pts (2026-03-26). Lean alternatives then got traction: "GoModel – open-source AI gateway in Go", 217 pts (2026-04-21, 1.2k stars), and "Litelm: LiteLLM Without the Bloat", 177 pts (2026-09-11). — [HN compromise](https://news.ycombinator.com/item?id=47501426); [HN response](https://news.ycombinator.com/item?id=47531967); [HN GoModel](https://news.ycombinator.com/item?id=47849097); [HN Litelm](https://news.ycombinator.com/item?id=49662767)
- Many new self-hosted gateway Show HNs, all with low points: Foreman (cost-aware routing), 15 pts (2026-07-08); LLM-Gateway Zero-Trust, 7 pts; Mantis, 5 pts; Llmbridge (C++), 5 pts; and "I stopped using an LLM gateway and put rate-limits/fallback in-process", 4 pts (2026-09-06). — [HN Foreman](https://news.ycombinator.com/item?id=48835063); [HN in-process](https://news.ycombinator.com/item?id=49585787)

**Observability and tracing (pain is infrastructure weight and per-trace cost)**
- Show HN "Torrix, self hosted LLM Observability (no Postgres, no Redis)": 74 pts (2026-05-13). The author's stated friction: "Most self hosted LLM observability tools require Postgres, Redis and non trivial infrastructure… that set up cost discourages adoption." Torrix is a single Docker container on SQLite, aimed at "hundreds to low thousands of LLM calls per day". Features include cost forecasting and hard budget caps, PII masking, routing rules, golden-run evals and a prompt library. The community edition is free for 1 user with 7-day retention; a Pro tier adds teams and RBAC. — [HN](https://news.ycombinator.com/item?id=48120912)
- Show HN "Oodle.ai – $10 per million agent traces": 31 pts (2026-07-14). The founders said Langfuse was "6x more expensive" for their own use, and that they store unsampled traces as parquet-like files in S3 queried through Lambda. One commenter replied: "Dang that's expensive. We pay $0.75/M through a vendor." — [HN](https://news.ycombinator.com/item?id=48907615)
- A self-hosted Langfuse deployment has six moving parts: web, async worker, Postgres, ClickHouse, Redis/Valkey and S3. One estimate puts this at "a few hundred dollars a month" plus part of an engineer's time. The same source paraphrases an r/LangChain thread that started when LangSmith ended its free tier: "We self-host Langfuse and are pretty happy". This is a competitor blog quoting Reddit second-hand. — [Morph comparison](https://www.morphllm.com/comparisons/langfuse-alternatives)
- "LLM Observability in the Wild – Why OpenTelemetry Should Be the Standard" (SigNoz): 144 pts (2025-09-27). — [HN](https://news.ycombinator.com/item?id=45398467)
- Launch HN Lucidic (YC W25), "Debug, test, and evaluate AI agents in production": 116 pts (2025-07-30). Show HN "RLM-based local debugger for AI agent traces": 27 pts (2026-06-23). — [HN Lucidic](https://news.ycombinator.com/item?id=44735843); [HN RLM debugger](https://news.ycombinator.com/item?id=48649137)

**Evals and regression testing**
- Eval-related Show HNs with traction: "FrontierHarness Eval – 9 harness, same model, cost per pass varies 17x", 82 pts, 56 comments (2026-09-02); "Agent-skills-eval", 79 pts (2026-05-07); Launch HN Cekura (YC F24), testing and monitoring for voice and chat agents, 89 pts (2026-03-03); Promptloop (terminal prompt evals), 13 pts (2026-05-29). — [HN FrontierHarness](https://news.ycombinator.com/item?id=49538490); [HN skills-eval](https://news.ycombinator.com/item?id=48046023); [HN Cekura](https://news.ycombinator.com/item?id=47232903); [HN Promptloop](https://news.ycombinator.com/item?id=48325073)

**MCP server building, hosting and auth**
- Launch HN Manufact (YC S25), "MCP Cloud" (formerly mcp-use): 111 pts, 70 comments (2026-07-02). Comments included "we have so many problems with MCP related to auth, scopes etc... how do you guys help solve that?" and, from a would-be customer, "what does credits mean on your pricing page?… I would need to be able to budget this before I deploy." Skeptics wrote "MCP is a deadend. CLI use is the future" and "stopped using mcp and mostly using skills now." — [HN](https://news.ycombinator.com/item?id=48762862)
- Show HN Armature (YC P26), "Product analytics (and evals) for agent sessions on your MCP": 42 pts (2026-08-03). A commenter wrote: "As a builder of an MCP only product, I can attest to the pain. Nondeterministic nature of LLMs mean things break in highly unexpected ways with little visibility." — [HN](https://news.ycombinator.com/item?id=49157807)
- The MCP spec updates of 2025-06-18 and 2025-11-25 require OAuth 2.1 plus Dynamic Client Registration, Protected Resource Metadata, Resource Indicators and Client ID Metadata Documents. Google, GitHub and Microsoft Entra ID do not support DCR. Source is WorkOS, a vendor that sells MCP auth. — [WorkOS](https://workos.com/blog/best-mcp-server-authentication-providers)
- Hosting launches: "GuMCP – open-source MCP servers, hosted for free", 79 pts (2025-03-31); "MCP-Cloud – one-click hosting (50 templates)", 15 pts (2025-06-05); "Multi Tenant MCP Platform", 3 pts (2026-02-11); Launch HN Strata (YC P25), "One MCP server for AI to handle thousands of tools", 133 pts (2025-09-23); Launch HN Dedalus Labs (YC S25), "Vercel for Agents", 77 pts (2025-08-28). — [HN GuMCP](https://news.ycombinator.com/item?id=43535889); [HN MCP-Cloud](https://news.ycombinator.com/item?id=44195399); [HN Strata](https://news.ycombinator.com/item?id=45347914); [HN Dedalus](https://news.ycombinator.com/item?id=45054040)

**PII redaction before LLM calls**
- Every 2025–2026 Show HN in this area had very low engagement: SafeKey, PII redaction for text/image/audio/video, 4 pts (2025-12-03); Prompt-scrub, 4 pts (2026-07-31); "Open-source GDPR router for LLMs detects PII, forces EU-only inference", 4 pts (2026-04-07); Veil (redaction proxy), 2 pts; Blindfold, 1 pt; LLM-Shield-Proxy, 4 pts (2026-08-19). — [HN SafeKey](https://news.ycombinator.com/item?id=46137601); [HN Prompt-scrub](https://news.ycombinator.com/item?id=49124405); [HN GDPR router](https://news.ycombinator.com/item?id=47681656); [HN LLM-Shield](https://news.ycombinator.com/item?id=49360413)

**Prompt management**
- Stand-alone prompt-management Show HNs drew 2–3 pts each: open-sourced prompt manager, 3 pts (2025-08-02); PromptCol, 2 pts (2025-04-20); a lightweight prompt manager, 2 pts (2025-09-18). — [HN](https://news.ycombinator.com/item?id=44770969); [HN](https://news.ycombinator.com/item?id=43746053)

**Document ingestion for RAG**
- Launch HN Chonkie (YC X25), "Open-Source Library for Advanced Chunking": 151 pts (2025-06-09), 4.8k stars. Launch HN Context.dev (YC S26), "API to get structured data from any website": 119 pts (2026-07-09). Smaller ingestion tools got 2–9 pts: MarkdownConverters, 9 pts; Ragctl (OCR, chunking, Qdrant), 4 pts; side-by-side PDF parser comparison, 2 pts. — [HN Chonkie](https://news.ycombinator.com/item?id=44225930); [HN Context.dev](https://news.ycombinator.com/item?id=48847562); [HN Ragctl](https://news.ycombinator.com/item?id=46371520)
- One analysis of a 2M-page corpus put parsing spend anywhere from $2,100 to $90,000 depending on parser and options. This is a third-party claim reported in search results and not verified at the primary source. — [tokencost.app](https://tokencost.app/blog/document-parsing-api-cost-per-page)

### Inferences
- The best-evidenced developer pain in 2025–2026 is runtime control of agents: what an agent may touch, with which credentials, at what cost, and with an audit trail. The top threads (860, 768, 730 pts) are about agents or tools doing damage, not about missing dashboards.
- Observability demand is real, but the complaint has moved to two places: heavy self-host infrastructure (Torrix's pitch) and per-trace cost (Oodle at $10/M vs a commenter paying $0.75/M). That is price compression, not an open gap.
- The OpenRouter post documents a gap nobody seems to own: continuous, provider-level quality and reliability monitoring of the same model across hosts (empty-200 rates, tool-call validity, ignored params, IP-based throttling). The fix is backend-heavy (scheduled probes, async workers, time-series storage), which suits a Python developer. I did not research direct competitors for it; see Gaps.
- The supply-chain incident around LiteLLM (a large Python dependency) plus the "Litelm without the bloat" traction suggest buyers want small, auditable gateways or in-process libraries rather than large proxies.

### Gaps
- I could not reach Reddit threads (r/LocalLLaMA, r/LangChain, r/SaaS, r/SEO) directly. The only Reddit evidence is second-hand quotes in vendor blogs.
- I did not find Product Hunt upvote data for 2025–2026 launches in these categories. HN was the only engagement source I could query systematically.
- I found no survey data on how many teams track LLM cost per customer, or on what share of AI-feature gross margin is lost to outlier users. The vendor claim that "a small fraction of users drives a large fraction of spend" has no independent statistic behind it.
- I did not check for existing provider-quality monitors for OpenRouter-style hosts (for example, third-party benchmark or status sites), so whether that gap is really open is unverified.
- I did not find Show HN or Launch HN posts specifically for "AI output auditing" as a product category.

## Q2. How crowded is each sub-market? (Incumbents, pricing, stars and funding; saturation flags)

### Takeaway
LLM observability, tracing, evals, gateways, document parsing and GEO tracking are crowded. Each has well-funded companies, very large OSS projects (often 10k–190k stars), generous free tiers, and an acquisition wave in 2025–2026 (Langfuse to ClickHouse, Helicone to Mintlify, Promptfoo to OpenAI, Humanloop to Anthropic as an acqui-hire, OpenRouter to Stripe, Semrush to Adobe). The less-crowded edges are narrower:
- per-tenant cost and margin enforcement tied to billing, for small B2B SaaS;
- provider-quality monitoring;
- MCP auth shims and analytics for server builders;
- agent tool-call policy and audit;
- AI-crawler management for sites not on Cloudflare.

### Cited Findings

**Observability, tracing and evals (SATURATED)**
- **Langfuse** pricing (fetched 2026-10-09):
  - Hobby: $0, 50k units/mo, 30-day retention, 2 seats.
  - Core: $29/mo, 100k units, 90 days.
  - Pro: $199/mo, 3-year retention.
  - Enterprise: $2,499/mo.
  - Overage is $8 per 100k units, graduated down to $6. A "unit" is any trace, observation or score.
  - Self-hosting is free.
  — [Langfuse pricing](https://langfuse.com/pricing)
- Langfuse has 36k GitHub stars (2026-10-09) — [GitHub](https://github.com/langfuse/langfuse). "ClickHouse acquires Langfuse": 220 pts (2026-01-17) — [HN](https://news.ycombinator.com/item?id=46656552); [Langfuse blog](https://langfuse.com/blog/joining-clickhouse). A competitor blog says the deal came alongside ClickHouse's $400M Series D and that the core stays MIT-licensed — [Morph](https://www.morphllm.com/comparisons/langfuse-alternatives).
- **LangSmith** pricing (fetched 2026-10-09): Developer $0, 5k base traces, 1 seat. Plus $39/seat/mo, 10k traces, pay-as-you-go beyond that. Base traces are kept 14 days; extended traces 180 days at extra cost. — [LangChain pricing](https://www.langchain.com/pricing)
- **Helicone** pricing (fetched 2026-10-09): Hobby free, 10k requests, 7-day retention. Pro $79/mo. Team $799/mo. Usage-based beyond 10k requests and 1 GB. The page banner reads "Helicone Joins Mintlify". — [Helicone pricing](https://www.helicone.ai/pricing). Secondary sources date the Mintlify deal to around 2026-03-03, report Helicone moving to maintenance mode, and cite 16,000 active organizations and 14.2T tokens processed. These are aggregator claims I could not confirm at a primary source. — [vantaige.io](https://vantaige.io/ai-tool/helicone). Helicone has 6.2k stars — [GitHub](https://github.com/Helicone/helicone).
- **Braintrust** pricing (fetched 2026-10-09): Starter $0 (1 GB processed data, 10k scores, 14-day retention). Pro $249/mo (5 GB, 50k scores, 30 days, then +$3/GB and $1.50 per 1k scores). Unlimited users. — [Braintrust pricing](https://www.braintrust.dev/pricing). Braintrust raised an $80M Series B at an $800M post-money valuation, led by Iconiq (Feb 2026). — [Axios Pro](https://www.axios.com/pro/enterprise-software-deals/2026/02/17/ai-observability-braintrust-80-million-800-million)
- OSS star counts (2026-10-09): Comet Opik 22k; Arize Phoenix 12k; Traceloop OpenLLMetry 7.5k; AgentOps 5.9k; Promptfoo 26k; DeepEval 19k. — [Opik](https://github.com/comet-ml/opik); [Phoenix](https://github.com/Arize-ai/phoenix); [OpenLLMetry](https://github.com/traceloop/openllmetry); [AgentOps](https://github.com/AgentOps-AI/agentops); [Promptfoo](https://github.com/promptfoo/promptfoo); [DeepEval](https://github.com/confident-ai/deepeval)
- **Consolidation in evals:**
  - OpenAI agreed to acquire Promptfoo on 2026-03-09 (terms undisclosed; it stays open source). — [Futurum](https://futurumgroup.com/?p=87434); [Bloomberg Gov](https://news.bgov.com/private-equity/openai-buying-ai-security-startup-promptfoo-to-safeguard-agents)
  - Anthropic hired Humanloop's founders and team in Aug 2025. The Humanloop platform was sunset around 2025-09-08 (sources disagree on the exact date). — [Seedtable](https://seedtable.com/exits/humanloop)
- New entrants are competing on price: Oodle at $10 per million traces (2026-07-14); a commenter reported paying $0.75/M through another vendor. — [HN](https://news.ycombinator.com/item?id=48907615)

**Gateways, routing and cost controls (SATURATED at the core; budgets are gated to higher tiers)**
- **Portkey** pricing (fetched 2026-10-09):
  - Open source gateway: free.
  - Developer: free, 10k logs/mo, 3-day log retention, 3 prompt templates.
  - Production: $49/mo, 100k logs, +$9 per 100k up to 3M, 30-day logs.
  - Enterprise: custom, 10M+ logs, "granular budget and rate limits". A PII anonymizer appears in the comparison table, but its tier is unclear because the page layout is jumbled.
  — [Portkey pricing](https://portkey.ai/pricing). Portkey gateway has 13k stars — [GitHub](https://github.com/Portkey-AI/gateway).
- **LiteLLM** has 60k stars — [GitHub](https://github.com/BerriAI/litellm). It suffered a PyPI compromise on 2026-03-24 — [HN](https://news.ycombinator.com/item?id=47501426).
- **OpenRouter** raised a $113M Series B (HN 460 pts, 2026-05-30). Stripe reportedly agreed to acquire it for $7B+ (TechCrunch 2026-08-16; HN 487 pts), and OpenRouter announced it is "joining Stripe" (HN 964 pts, 2026-08-19). — [HN Series B](https://news.ycombinator.com/item?id=48338660); [TechCrunch via HN](https://news.ycombinator.com/item?id=49323381); [OpenRouter blog via HN](https://news.ycombinator.com/item?id=49364559)
- Other OSS gateways: GoModel 1.2k stars (2026-10-09) — [GitHub](https://github.com/ENTERPILOT/GOModel).
- FinOps and metering tools named for per-customer LLM cost allocation: CloudZero, Amnic, OpenMeter. — [Amnic](https://amnic.com/blogs/llm-cost-allocation-tools); [FutureAGI](https://futureagi.com/blog/best-llm-cost-tracking-tools-2026/)

**Guardrails and PII (OSS-heavy; enterprise vendors)**
- Microsoft Presidio 11k stars; NVIDIA NeMo-Guardrails 7.3k; ProtectAI llm-guard 3.2k (2026-10-09). — [Presidio](https://github.com/microsoft/presidio); [NeMo-Guardrails](https://github.com/NVIDIA/NeMo-Guardrails); [llm-guard](https://github.com/protectai/llm-guard)

**MCP hosting, gateways and auth (CROWDING FAST; VC-backed)**
- Funded MCP companies: Manufact (YC S25) MCP Cloud; Strata (YC P25); Dedalus Labs (YC S25); Armature (YC P26). mcp-use SDK has 11k stars. — [HN Manufact](https://news.ycombinator.com/item?id=48762862); [HN Strata](https://news.ycombinator.com/item?id=45347914); [HN Dedalus](https://news.ycombinator.com/item?id=45054040); [HN Armature](https://news.ycombinator.com/item?id=49157807); [GitHub mcp-use](https://github.com/mcp-use/mcp-use)
- More than 7 MCP gateway Show HNs between 2025-07 and 2026-10: Director, 14 pts; MCP Gateway (N×M), 10 pts; Universal MCP gateway, 6 pts; Zero-Trust MCP Gateway, 4 pts; Portus (Rust), 4 pts; Storm MCP, 3 pts. — [HN Director](https://news.ycombinator.com/item?id=44533022); [HN MCP Gateway](https://news.ycombinator.com/item?id=46136222)
- Pricing for Smithery ($10/mo Basic, $25/mo Pro) and Composio (four tiers, free OSS core) comes only from third-party aggregators. — [Toolradar Smithery](https://toolradar.com/tools/smithery/pricing); [Merge on Composio](https://www.merge.dev/blog/composio-pricing). Auth vendors (WorkOS, Auth0) sell MCP auth. — [WorkOS](https://workos.com/blog/best-mcp-server-authentication-providers); [Auth0](https://auth0.com/ai/docs/mcp/intro/overview)

**Document ingestion and parsing (SATURATED by OSS and cheap APIs)**
- OSS star counts (2026-10-09): Microsoft MarkItDown 189k; Docling 69k; Marker 40k; Unstructured 16k; Chonkie 4.8k. — [MarkItDown](https://github.com/microsoft/markitdown); [Docling](https://github.com/docling-project/docling); [Marker](https://github.com/datalab-to/marker); [Unstructured](https://github.com/Unstructured-IO/unstructured); [Chonkie](https://github.com/chonkie-inc/chonkie)
- API pricing, from third-party write-ups (verify before relying on them):
  - LlamaParse: credit-based at $1.25 per 1,000 credits, 1–45 credits per page (about $0.00125–$0.056/page), with 10k free credits/mo.
  - Reducto: Extract at $0.02/page all-in from 2026-09-01.
  - Unstructured: 15k pages/mo free, then $0.03/page, billing capped at $3,000/mo.
  — [Reducto blog](https://reducto.ai/blog/reducto-simple-transparent-document-processing-pricing); [tokencost.app](https://tokencost.app/blog/document-parsing-api-cost-per-page); [apiscout](https://apiscout.dev/guides/llamaparse-vs-reducto-best-document-ai-api-2026)

### Inferences
- **Saturation flags.** Avoid head-on: general LLM observability/tracing, evals platforms, general-purpose LLM gateways, PDF-to-Markdown parsing, and prompt management. Each has a 10k+-star free OSS option and at least one funded incumbent, and per-unit prices are falling (Langfuse at $6–8 per 100k units; traces quoted at $0.75–$10 per million).
- The 2025–2026 acquisition wave (ClickHouse/Langfuse, Mintlify/Helicone, OpenAI/Promptfoo, Anthropic/Humanloop, Stripe/OpenRouter) cuts both ways:
  - Consolidation makes it hard for a solo developer to compete on breadth.
  - It may also leave orphaned users. Helicone is reportedly in maintenance mode, and some teams are re-evaluating after the Langfuse acquisition. A migration or lightweight-replacement tool could serve them, but the evidence for that demand is anecdotal.
- Budgets and rate limits per key or customer exist, but they sit in gateway enterprise tiers (Portkey). They are also not tied to the customer's own billing system. That leaves room for a cheap, focused "AI margin guard" for small B2B SaaS: ingest usage from SDK, OTel or gateway logs; attribute cost per tenant and feature; enforce hard caps; alert; export to Stripe/usage billing. The main risk is gateways and observability tools bundling this feature.
- MCP infrastructure is crowding with YC-backed teams, and HN commenters question MCP itself in favor of CLI tools and skills. A niche MCP auth shim (OAuth 2.1 + DCR in front of IdPs that lack DCR) is technically substantive, but it competes with WorkOS, Auth0 and Stytch-class vendors.

### Gaps
- I could not get Arize AX paid pricing or OpenRouter's fee percentage from primary sources in this pass.
- The Helicone/Mintlify deal terms and maintenance-mode status are secondary-source only.
- I did not verify primary pricing for Smithery, Composio or the PII redaction vendors (for example Private AI, Protecto, Skyflow).
- I found no reliable data on revenue or ARR for the OSS observability companies beyond funding figures.

## Q3. What new non-developer problems did AI create?

### Takeaway
Four business-side problems came out of AI adoption in 2025–2026:
- **AI crawler and agent load on websites.** Very high HN engagement; Cloudflare dominates the response.
- **Loss of search traffic and the need to track brand presence in AI answers (GEO).** A large, heavily funded and crowded market.
- **AI slop and spam in communities and inboxes.** Very high engagement, but few products.
- **AI-generated or fraudulent job applications.** A recurring complaint, but mostly backed by vendor-sourced statistics.

I found no good 2025–2026 evidence on content provenance (C2PA).

### Cited Findings

**AI crawlers and agent traffic on websites**
- High-engagement HN threads:
  - "Nepenthes is a tarpit to catch AI web crawlers": 714 pts (2025-01-16).
  - "Amazon's AI crawler is making my Git server unstable": 607 pts (2025-01-18).
  - "Devs say AI crawlers dominate traffic, forcing blocks on entire countries" (Ars Technica): 360 pts (2025-03-25).
  - "AI crawlers, fetchers are blowing up websites; Meta, OpenAI are worst offenders" (The Register): 231 pts (2025-08-21).
  - "How I protect my Forgejo instance from AI web crawlers": 189 pts (2025-12-21).
  - "Ask HN: AI bots everywhere – does anyone have a good whitelist for robots.txt?": 61 pts (2025-01-29).
  — [HN Nepenthes](https://news.ycombinator.com/item?id=42725147); [HN Amazon](https://news.ycombinator.com/item?id=42750420); [HN Ars](https://news.ycombinator.com/item?id=43476337); [HN Register](https://news.ycombinator.com/item?id=44971487); [HN Forgejo](https://news.ycombinator.com/item?id=46345205); [Ask HN](https://news.ycombinator.com/item?id=42861047)
- Anubis (anti-AI-scraper proof-of-work proxy) has 23k stars (2026-10-09). — [GitHub](https://github.com/TecharoHQ/anubis)
- **Cloudflare:**
  - Pay Per Crawl lets sites allow, block or charge each crawler. Crawlers get HTTP 402 and must authenticate with Web Bot Auth. One source still lists the product as private beta.
  - Starting 2026-09-15, Cloudflare blocks "mixed-use" crawlers by default on ad-carrying pages, for new domains and free customers.
  - Crawl-to-referral ratios conflict across sources. July 2025 figures were reported as about 14:1 for Google, 1,700:1 for OpenAI and 73,000:1 for Anthropic; later 2026 figures differ.
  — [Let's Data Science](https://letsdatascience.com/news/cloudflare-blocks-mixed-use-crawlers-on-monetized-pages-5a9acadb); [eWeek](https://www.eweek.com/de/news/cloudflare-expands-ai-crawler-control/); [Digital Applied](https://www.digitalapplied.com/blog/ai-crawl-economics-pay-per-crawl-referral-data-2026)
- Research from Rutgers and Wharton (revised April 2026) found that publishers who blocked LLM crawlers lost about 7% of weekly traffic within six weeks. I saw this in search-result summaries only and did not verify the paper. — [Digital Applied](https://www.digitalapplied.com/blog/ai-crawl-economics-pay-per-crawl-referral-data-2026)
- **Dark Visitors** (AI agent and crawler analytics) pricing: Free, 100K events; Individual $29/mo, 1M events; Startup $299/mo, 10M events; Enterprise custom. Sources conflict on the free tier. — [Dark Visitors pricing](https://darkvisitors.com/pricing); [Manual do Usuário](https://manualdousuario.net/en/dark-visitors-plano-gratuito/)
- Show HN crawler and bot-tracking tools got 1–7 pts each: CountermarkAI, 7 pts; AI Search Index, 2 pts; Track AI Bots Crawling, 2 pts; AI crawler honeypot, 3 pts; "Directory of 28 AI crawlers", 2 pts; a Caddy plugin charging AI crawlers USDC, 1 pt; a WordPress AI crawler access-control plugin, 1 pt; self-hosted analytics with AI crawler tracking, 1 pt. — [HN CountermarkAI](https://news.ycombinator.com/item?id=44275375); [HN Caddy USDC](https://news.ycombinator.com/item?id=47179432); [HN WP plugin](https://news.ycombinator.com/item?id=46694542)
- Machine-readable site standards: Show HN "CommerceTXT – an open standard for AI shopping context (like llms.txt)", 20 pts, 58 comments (2025-12-16). Several llms.txt generators and validators got 4–7 pts each. — [HN CommerceTXT](https://news.ycombinator.com/item?id=46289481); [HN llms.txt validator](https://news.ycombinator.com/item?id=44492455)

**Search traffic loss and AI search visibility (GEO/AEO)**
- "Wikipedia says traffic is falling due to AI search summaries and social video": 445 pts, 447 comments (2025-10-21). "Chatbots are replacing Google's search, devastating traffic for some publishers" (WSJ): 205 pts (2025-06-10). — [HN Wikipedia](https://news.ycombinator.com/item?id=45651485); [HN WSJ](https://news.ycombinator.com/item?id=44241407)
- **Market size and funding:**
  - About 100+ tools, $200M+ in VC, 20+ dedicated platforms; industry-average price about $337/mo.
  - Profound: $155M total, $1B valuation after a $96M Series C (2026-02-24).
  - Bluefish: $68M ($20M Series A Aug 2025; $43M Series B Apr 2026).
  - Scrunch: about $19M. Evertune: $20M+.
  - Daydream: $21M ($15M Series A, Apr 2026).
  - Adobe completed its ~$1.9B acquisition of Semrush on 2026-04-28. Semrush's AI Visibility Toolkit costs about $99/domain/mo.
  - Ahrefs Brand Radar: from $129/mo; all-platform bundle about $699/mo.
  - Otterly.AI: from about $29/mo. Rankshift: €69/€159.
  - The source's author runs a GEO vendor (GrackerAI); figures are partly estimates.
  — [guptadeepak.com GEO market 2026](https://guptadeepak.com/geo-compass/guides/geo-tooling-market-2026/)
- Peec AI closed a $21M Series A (May 2026). It reported $4M+ ARR within ten months of launch and 1,300+ brands and agencies as customers. — [everything-pr](https://everything-pr.com/berlins-peec-ai-rockets-to-4m-arr-in-ten-months-raises-21m-series-a-to-open-new-york-office/amp); [CXO Digital Pulse](https://www.cxodigitalpulse.com/?p=40702)
- Neither Profound's nor Peec's pricing page shows tier prices. Profound shows a free trial of 50 prompts over 7 days on 3 engines, and Enterprise covering up to 9 engines. Peec lists Starter/Pro/Advanced/Enterprise with coverage = prompts × models × frequency. — [Profound pricing](https://www.tryprofound.com/pricing); [Peec pricing](https://peec.ai/pricing)
- GEO Show HN launches with almost no engagement:
  - Geneo, 2 pts (2025-06-20).
  - ReachLLM, 2 pts (2025-08-25).
  - "Track Your Brand in ChatGPT", 2 pts (2025-11-06).
  - "You need this for tracking AI search visibility", 2 pts (2026-01-08).
  - Mentionable, 2 pts (2026-02-02).
  - VisibleInAI, 2 pts (2026-02-17).
  - PilotCite, 6 pts (2026-07-19).
  - Bloomiro, 5 pts (2026-07-07).
  - Free AI-visibility scan, 5 pts (2026-08-30).
  - "Estimating what users ask ChatGPT about your company", 2 pts (2026-06-24).
  — [HN Geneo](https://news.ycombinator.com/item?id=44325360); [HN ReachLLM](https://news.ycombinator.com/item?id=45019946); [HN Mentionable](https://news.ycombinator.com/item?id=46853772); [HN VisibleInAI](https://news.ycombinator.com/item?id=47054773); [HN PilotCite](https://news.ycombinator.com/item?id=48965687); [HN query estimation](https://news.ycombinator.com/item?id=48658057)
- A gap the same market analysis notes: it does not say whether any vendor ties AI visibility to traffic or revenue. It calls Google AI Mode "the weakest spot for many monitors". — [guptadeepak.com](https://guptadeepak.com/geo-compass/guides/geo-tooling-market-2026/)

**AI slop and spam (communities, inboxes, search)**
- "AI slop is killing online communities": 834 pts, 734 comments (2026-05-07). "SlopStop: community-driven AI slop detection in Kagi Search": 589 pts (2025-11-13). "Rob Pike got spammed with an AI slop 'act of kindness'": 312 pts (2025-12-26). "Tell HN: I'm tired of AI-generated answers": 120 pts (2026-05-21). — [HN slop communities](https://news.ycombinator.com/item?id=48053203); [HN Kagi SlopStop](https://news.ycombinator.com/item?id=45919067); [HN Rob Pike](https://news.ycombinator.com/item?id=46394867); [HN tired](https://news.ycombinator.com/item?id=48230104)

**AI-generated or fraudulent job applications**
- A 2025 survey of 874 HR professionals, cited by a vendor blog, found 72% of recruiters had seen AI-generated applications: AI portfolios in 51% of cases and fabricated references in 42%. A Gartner forecast that "1 in 4 applicant profiles will be fraudulent by 2028" is widely repeated, but I could not verify it at the source. Suggested detection signals include data-center IPs, newly created emails and untraceable phone numbers. Keyword-based screeners are described as easy for AI-written resumes to beat. — [eWeek](https://www.eweek.com/news/ai-job-applicants-hiring/); [MintHCM](https://minthcm.org/?p=3382); [Metaview on deepfake interviews](https://www.metaview.ai/resources/blog/deepfake-interviews)

### Inferences
- **AI crawler management is a strong, long-running pain** (hundreds of HN points across 2025). Cloudflare now sets the default for most sites, and Anubis covers self-hosters for free. The remaining gaps:
  - sites not behind Cloudflare (Vercel, Netlify, self-hosted Nginx) that want per-bot analytics from server logs;
  - verification of a bot's claimed identity (IP ranges, Web Bot Auth);
  - crawl-to-referral reporting per bot, connecting crawl cost to AI referral traffic.

  That is log-pipeline work suited to a Python backend. Competition: Dark Visitors at $29–$299/mo, and free Cloudflare features.
- **GEO tracking is the clearest saturation flag on the non-developer side**: 100+ tools, $200M+ VC, a $1B leader, Adobe/Semrush and Ahrefs bundling it, and around ten copycat Show HNs at 2–6 pts each. Peec's $4M ARR proves willingness to pay, but a solo developer would be the 101st entrant. Narrower angles that look less covered:
  - attributing AI referrals to revenue (joining GA4/server logs with AI-answer citations);
  - vertical or local GEO for one industry.
- **AI slop and spam moderation** shows high frustration but weak evidence of anyone paying, and detection accuracy is a known hard problem. That makes it risky as an MVP.
- **Hiring fraud** looks like a real budget line (recruiting teams already pay for ATS and verification), but the numbers come mostly from vendors. A lightweight risk-signal API or ATS plugin (IP and email reputation, duplicate and template detection across applications) is backend-substantive. I did not map competitor products in this pass.

### Gaps
- No usable 2025–2026 data on content provenance or C2PA adoption, or on demand for verification tools. HN searches for "C2PA" returned only unrelated popular stories.
- No r/SEO or r/SaaS primary threads retrieved.
- No independent benchmark of AI-text or AI-application detection accuracy was found.
- The Cloudflare crawl-to-referral ratios conflict across sources, so treat exact per-company values as unreliable.

## Q4. Which of these did people say they'd pay for, or launch with traction, in 2025–2026?

### Takeaway
Explicit paying traction is clearest in GEO (Peec: $4M+ ARR, 1,300+ customers), observability/evals (Braintrust at an $800M valuation; Helicone reportedly at 16k orgs; Langfuse acquired), gateways (OpenRouter, reportedly $7B+ to Stripe) and MCP infrastructure (several YC Launch HNs at 77–133 pts). The highest-traction Show HN launches by indie or small teams in 2025–2026 were security, guardrail and agent-control tools (Agent Vault 156, MCP-Shield 134, Context Gateway 97) and lightweight self-hosted alternatives (GoModel 217, Litelm 177, Torrix 74). Generic GEO, PII, prompt-management and cost-calculator launches drew 1–12 pts.

### Cited Findings

**Paying traction at funded companies**
- Peec AI: $4M+ ARR within ten months, 1,300+ brands and agencies, $21M Series A (May 2026). — [everything-pr](https://everything-pr.com/berlins-peec-ai-rockets-to-4m-arr-in-ten-months-raises-21m-series-a-to-open-new-york-office/amp)
- Profound: "used by more than 700 enterprises". This is a figure from a competitor's comparison page. — [Waikay compare](https://waikay.io/compare/)
- Braintrust: $80M Series B at $800M valuation (Feb 2026). — [Axios Pro](https://www.axios.com/pro/enterprise-software-deals/2026/02/17/ai-observability-braintrust-80-million-800-million)
- Helicone: reportedly 16,000 active organizations at acquisition (secondary source). — [vantaige.io](https://vantaige.io/ai-tool/helicone)
- OpenRouter: $113M Series B, then a reported $7B+ Stripe acquisition (2026). — [HN Series B](https://news.ycombinator.com/item?id=48338660); [HN Stripe](https://news.ycombinator.com/item?id=49364559)

**Highest-traction indie and small-team launches**
- GoModel (Go AI gateway): 217 pts (2026-04-21). — [HN](https://news.ycombinator.com/item?id=47849097)
- Litelm: 177 pts (2026-09-11). — [HN](https://news.ycombinator.com/item?id=49662767)
- Agent Vault: 156 pts (2026-04-22). — [HN](https://news.ycombinator.com/item?id=47865822)
- MCP-Shield: 134 pts (2025-04-15). — [HN](https://news.ycombinator.com/item?id=43689178)
- Context Gateway: 97 pts (2026-03-13). — [HN](https://news.ycombinator.com/item?id=47367526)
- GuMCP: 79 pts (2025-03-31). — [HN](https://news.ycombinator.com/item?id=43535889)
- Torrix: 74 pts (2026-05-13). — [HN](https://news.ycombinator.com/item?id=48120912)
- Open Edison MCP gateway: 51 pts (2025-09-12). — [HN](https://news.ycombinator.com/item?id=45223102)

**YC Launch HNs in adjacent spaces**
- Chonkie, 151 pts (2025-06-09). — [HN](https://news.ycombinator.com/item?id=44225930)
- Strata, 133 pts (2025-09-23). — [HN](https://news.ycombinator.com/item?id=45347914)
- Context.dev, 119 pts (2026-07-09). — [HN](https://news.ycombinator.com/item?id=48847562)
- Lucidic, 116 pts (2025-07-30). — [HN](https://news.ycombinator.com/item?id=44735843)
- Manufact, 111 pts (2026-07-02). — [HN](https://news.ycombinator.com/item?id=48762862)
- Cekura, 89 pts (2026-03-03). — [HN](https://news.ycombinator.com/item?id=47232903)

**Explicit willingness-to-pay statements**
- Manufact thread, from a would-be customer: "I'm a target customer… One thing that's stopping me, what does credits mean on your pricing page? And what is the pay as you go price after you hit your limit? I would need to be able to budget this before I deploy." — [HN](https://news.ycombinator.com/item?id=48762862)
- Oodle thread: "We pay $0.75/M through a vendor" (for agent traces). — [HN](https://news.ycombinator.com/item?id=48907615)
- Torrix sells a Pro tier (teams, RBAC, 30-day retention, audit logs) on top of a free single-user edition. The launch post gives no price. — [HN](https://news.ycombinator.com/item?id=48120912)

**Low-traction categories (all 2025–2026 Show HNs at 1–12 pts)**
- LLM cost calculators and savers: Llmswap 12, AgentReady 8, Costly 4, Slash-tokens 4.
- PII redaction proxies: 1–4 each.
- Prompt managers: 2–3.
- GEO trackers: 2–6.
- AI bot trackers: 1–7.
- llms.txt tools: 4–7.

Sources are the HN links cited in Q1–Q3.

### Inferences
These ideas are inferred and ranked for a solo Python developer: backend substance first, then evidence of pain, then crowding. Each needs validation.

1. **Agent tool-call policy, credential brokering and audit log.** A proxy or SDK between an agent and its tools/MCP servers that enforces allow/deny rules per tool and argument, requires approval for destructive actions, uses scoped short-lived credentials, and keeps an append-only audit trail plus replay.
   - Pain evidence: 860, 768 and 730-pt incident threads; Agent Vault (156 pts) and MCP-Shield (134 pts).
   - Backend: policy engine, async approval queue, multi-tenant audit store.
   - Crowding: emerging, with Infisical (Agent Vault), Open Edison, auth vendors and YC MCP startups. Commenters doubt LLM-based classifiers, so a deterministic policy engine is more defensible.
2. **Per-tenant LLM cost and margin guard for small B2B SaaS.** Ingest usage from an OpenAI-compatible proxy, an SDK or OTel; attribute cost per customer, feature and model; enforce hard caps and soft alerts; forecast; push usage to Stripe.
   - Evidence: vendor guides call it a need; budgets sit in Portkey's Enterprise tier; Torrix users asked for "cost forecasting and hard budget caps".
   - Backend: event ingestion, aggregation workers, multi-tenant API.
   - Crowding: medium. Gateways, observability tools and FinOps vendors could bundle this.
   - Stand-alone cost-tool Show HNs got little traction, so position it on margin and billing, not on "see your token spend".
3. **Provider reliability and quality monitor for multi-provider and OpenRouter users.** Scheduled canary probes per model×provider (empty-200 rate, tool-call validity, ignored params, latency, quality drift on a small eval set), an alerting API, and auto-generated provider allow/deny lists for routing.
   - Evidence: the 766-pt OpenRouter post.
   - Backend: schedulers, workers, time-series storage.
   - Crowding: not researched (see Gaps).
4. **AI crawler/agent log analytics and policy for sites not on Cloudflare.** Server-log or edge ingestion, bot identity verification, per-bot crawl cost vs AI referral traffic, robots.txt/llms.txt management, optional 402 responses.
   - Evidence: 2025 HN threads at 189–714 pts; Anubis at 23k stars.
   - Competition: Cloudflare (dominant), Dark Visitors ($29–$299/mo).
   - Crowding: medium; Cloudflare default-blocking narrows the market.
5. **MCP server analytics, testing and an auth shim.** OAuth 2.1/DCR facade for IdPs without DCR, plus per-tool usage analytics for MCP builders.
   - Evidence: Manufact and Armature threads.
   - Crowding: high and VC-backed (Manufact, Armature, WorkOS, Auth0, Smithery, Composio). MCP's longevity is also questioned in comments.
6. **Lightweight self-hosted LLM observability.**
   - Evidence: the Torrix and Oodle pitches.
   - Crowding: saturated. Langfuse (36k stars, free self-host), Phoenix and Opik, with per-trace prices falling to $0.75–$10/M. Only viable as a very narrow niche.

Flagged as saturated or poor fit for a solo MVP:
- GEO/AI-visibility tracking (100+ tools, $200M+ VC, Adobe/Semrush and Ahrefs bundling it).
- General evals platforms (Braintrust, plus Promptfoo and Humanloop absorbed by OpenAI and Anthropic).
- General LLM gateways (LiteLLM 60k stars, Portkey, OpenRouter/Stripe).
- PDF/document parsing (MarkItDown 189k stars, Docling 69k, Marker 40k; APIs at $0.001–$0.03/page).
- Stand-alone prompt management.
- Generic PII-redaction proxies (Presidio 11k stars; many zero-traction launches).

### Gaps
- No Product Hunt upvote data was collected. HN was the only engagement source I could query systematically.
- There are few direct "I would pay $X for Y" quotes in the sources I could reach. Reddit and Indie Hackers threads with explicit willingness to pay were not accessible in this pass.
- No revenue or traction data for small indie tools such as Torrix or Dark Visitors.
- No competitor scan for ideas 3 (provider-quality monitor) and the hiring-fraud signal API, so whether those gaps are really open is unconfirmed.
