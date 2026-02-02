# AI_CYBERSECURITY.md
## TEMPT Profile: AI & LLM Security

---

## Profile Overview

**Domain:** AI/ML Cybersecurity with emphasis on Large Language Models, Agentic Systems, and Prompt Security  
**Focus:** Attack vectors, defensive mitigations, and real-world deployment risk data  
**Recency Filter:** Prioritize 2023-2025 sources (post-GPT-4 era)  
**Last Updated:** February 2026 (v1.1)

---

## BB Pair Configuration

This profile uses **six specialized BB pairs**, each with a dedicated Red Team adversary. The debates focus on *how attacks actually work* and *what defenders are doing about it*.

### BB Pair 1: Network Hardener vs. Infra Breaker

| Role | Persona |
|------|---------|
| **Defender:** Network Hardener | Classic security engineer. Thinks in firewalls, network segmentation, IAM policies, zero-trust architecture. Views AI as "just another application" that needs standard enterprise controls. |
| **Attacker:** Infra Breaker | Traditional pentester who pivoted to AI targets. Exploits misconfigs in AI deployment infrastructure—exposed APIs, overprivileged service accounts, unpatched Ray clusters, S3 buckets full of training data. |

**Debate Focus:**  
- Cloud infrastructure securing AI workloads (AWS, GCP, Azure AI services)
- API gateway security and rate limiting
- Network isolation of training vs. inference environments
- Credential management for model endpoints
- Supply chain attacks on AI infrastructure (e.g., ShadowRay CVE)

---

### BB Pair 2: Model Guardian vs. ML Attacker

| Role | Persona |
|------|---------|
| **Defender:** Model Guardian | AI security specialist focused on the model itself. Thinks about training data integrity, model robustness, adversarial inputs, and inference-time attacks. Uses MITRE ATLAS as their playbook. |
| **Attacker:** ML Attacker | Adversarial ML researcher. Poisons training data, extracts models through APIs, crafts adversarial examples, and exploits embedding weaknesses. Treats models as artifacts to corrupt or steal. |

**Debate Focus:**  
- Training data poisoning and backdoor injection
- Model extraction and theft via inference APIs
- Adversarial inputs that bypass classifiers
- RAG knowledge base poisoning (e.g., PoisonedRAG: 5 malicious docs → 90% attack success)
- Embedding manipulation and vector database attacks
- Membership inference and training data extraction
- Supply chain backdoors in pre-trained models (see: BackdoorLLM research)

---

### BB Pair 3: Agent Wrangler vs. Autonomy Exploiter

| Role | Persona |
|------|---------|
| **Defender:** Agent Wrangler | Builds guardrails around autonomous AI systems. Obsessed with permission boundaries, tool access controls, human-in-the-loop checkpoints, and audit logging. Knows that agency = attack surface. |
| **Attacker:** Autonomy Exploiter | Specializes in making agents do things they shouldn't. Exploits tool integrations, chains actions across systems, escalates privileges through trust relationships, and turns agent autonomy against itself. |

**Debate Focus:**  
- Excessive agency and unchecked permissions (OWASP LLM06)
- Tool misuse and unauthorized API calls
- **Memory poisoning** — corrupting agent long-term memory with persistent false beliefs
  - Sleeper agent scenarios: dormant until triggered
  - Memory-persistent data exfiltration (SpAIware)
- Cascading hallucination attacks
- Goal hijacking and planning manipulation
- Human-in-the-loop bypass techniques
- **ZombAIs** — long-term prompt injection persistence in coding agents
- Intent breaking and objective redirection

---

### BB Pair 4: Prompt Fortifier vs. Injection Artist

| Role | Persona |
|------|---------|
| **Defender:** Prompt Fortifier | Input/output security specialist. Builds prompt templates, output validators, content filters, and system prompt isolation. Knows that the prompt is the new attack surface. |
| **Attacker:** Injection Artist | The jailbreak specialist. Crafts prompts that bypass safety filters, extracts system prompts, manipulates model behavior through indirect injection via documents/web pages, and finds creative ways to make models misbehave. |

**Debate Focus:**  
- Direct prompt injection and jailbreaks
- Indirect injection via external content (documents, emails, web pages)
- System prompt extraction and leakage (OWASP LLM07)
- **Output handling → code execution** — XSS, SQL injection, RCE via unvalidated LLM output
  - exec()/eval() on LLM-generated code
  - Prompt-to-SQL injection attacks
- Multi-language and encoding attacks (Base64, ROT13, Unicode invisible characters)
- Image-based prompt injection (steganography, OCR exploitation)
- Roleplay and persona attacks (89.6% ASR in research)
- **AI ClickFix** — nation-state TTP adaptation for AI computer-use systems
- **Lethal Trifecta exploitation** — targeting systems with private data + untrusted content + external communication

---

### BB Pair 5: Protocol Defender vs. Protocol Exploiter

| Role | Persona |
|------|---------|
| **Defender:** Protocol Defender | Secures AI integration protocols and tool connection layers. Focuses on MCP server hardening, OAuth token management, tool registration security, and API isolation. Knows that standardized protocols create standardized attack surfaces. |
| **Attacker:** Protocol Exploiter | Targets the connective tissue of AI systems. Exploits MCP servers, tool definitions, OAuth aggregation, and protocol-level weaknesses. Views each integration point as an entry vector. |

**Debate Focus:**  
- **MCP (Model Context Protocol) attacks:**
  - Tool poisoning — hidden instructions in tool descriptions
  - Rug pull attacks — tools that modify their definitions post-approval
  - OAuth token aggregation — single breach exposes all connected services
  - Command injection in MCP servers (CVE-2025-6514, CVSS 9.6)
  - Sampling abuse — resource theft, conversation hijacking, covert tool invocation
  - Sandbox escape and containment bypass
- **Protocol-level vulnerabilities:**
  - Session ID exposure in URLs
  - Lack of authentication standards
  - Missing message signing/integrity controls
  - Confused deputy attacks via dynamic client registration
- Tool redefinition attacks in multi-server environments
- Supply chain attacks on MCP server repositories

**Key CVEs & Incidents:**
- CVE-2025-6514 (mcp-remote command injection)
- Anthropic Filesystem-MCP sandbox escape
- GitHub MCP server private repo exfiltration
- WhatsApp MCP tool poisoning + exfiltration chain
- Anthropic MCP Inspector unauthenticated RCE
- Supabase Cursor agent SQL injection via support ticket

---

### BB Pair 6: Trust Architect vs. Cascade Attacker

| Role | Persona |
|------|---------|
| **Defender:** Trust Architect | Designs secure multi-agent systems. Focuses on inter-agent authentication, trust boundaries, communication channel integrity, and cascade failure prevention. Knows that agent-to-agent trust is the new attack surface. |
| **Attacker:** Cascade Attacker | Exploits relationships between agents. Targets trust chains, impersonates legitimate agents, poisons inter-agent communication, and triggers cascade failures that overwhelm incident response. |

**Debate Focus:**  
- **Inter-agent trust exploitation:**
  - 82.4% of models compromised through peer agent requests (even when resistant to direct injection)
  - Agent impersonation and identity spoofing
  - Trust chain abuse — using legitimate agents to reach protected systems
- **Cascade attacks:**
  - Single compromised agent → 87% downstream poisoning in 4 hours (Galileo AI research)
  - Cascading hallucinations across agent networks
  - Vendor-validation agent compromise → $3.2M fraudulent orders (manufacturing case)
- **Multi-agent coordination exploits:**
  - Agent collusion — secretly coordinating for malicious goals
  - Steganographic communication between compromised agents
  - Competition exploitation — agents attacking each other's weaknesses
- **Communication channel attacks:**
  - Agent communication poisoning
  - Rogue agents operating outside monitoring boundaries
  - Human-in-the-loop overwhelming (decision fatigue attacks)
- **Registry and discovery manipulation:**
  - Compromised agent registries
  - Malicious agent discovery promotion
  - Agent behavior hijacking via coordination manipulation

**Key Frameworks:**
- OWASP Agentic AI Threat #10: Multi-Agent Trust Exploitation
- OWASP Agentic AI Threat #13: Rogue Agents
- OWASP Agentic AI Threat #14: Human Attacks on Multi-Agent Systems
- CSA MAESTRO Framework (Multi-Agent Environment, Security, Threat Risk, and Outcome)

---

## Source Priority Hierarchy

When researching for BB debates, Claude MUST search in this order:

### Tier 0: Bleeding Edge (Check FIRST for Novel Attacks)

These sources surface vulnerabilities **weeks to months** before mainstream frameworks:

| Source | Focus | URL |
|--------|-------|-----|
| **Embrace The Red (Johann Rehberger)** | Real exploits, coding agent vulnerabilities, Month of AI Bugs | https://embracethered.com |
| **Simon Willison's Blog** | Conceptual frameworks, lethal trifecta, prompt injection analysis | https://simonwillison.net |
| **Month of AI Bugs Archive** | Vulnerability database with PoCs | https://monthofaibugs.com |
| **Invariant Labs** | MCP exploits, tool poisoning research | https://invariantlabs.ai |
| **Pillar Security Blog** | Indirect injection, CFS model | https://pillar.security/blog |
| **Lakera AI Blog** | Prompt injection defense, attack data | https://lakera.ai/blog |
| **Lasso Security Blog** | RAG attacks, guardrail bypasses | https://lasso.security/blog |
| **HiddenLayer Innovation Hub** | Enterprise AI security, lethal trifecta analysis | https://hiddenlayer.com/innovation-hub |

**Community Sources:**
- **AI Village Discord** — DEFCON-affiliated, real-time CTF/exploit sharing
- **r/LocalLLaMA** — Open-source model jailbreaks, fine-tuning exploits
- **r/ChatGPT** — User-discovered vulnerabilities
- **r/PromptEngineering** — Technique development, bypass methods
- **Jailbreak Tracker** — Live monitoring of known jailbreaks

**Research shows:** Discord contributes 43% of novel vulnerabilities, Reddit 31%, GitHub 18% (PrompTrend 2025)

### Tier 1: Authoritative Standards & Frameworks
1. **OWASP LLM Top 10 2025** — https://genai.owasp.org/llm-top-10/
2. **OWASP Top 10 for Agentic Applications** — https://genai.owasp.org/
3. **MITRE ATLAS** — https://atlas.mitre.org/
4. **NIST AI Risk Management Framework** — https://www.nist.gov/itl/ai-risk-management-framework
5. **CSA MAESTRO Framework** — https://cloudsecurityalliance.org/ (multi-agent threat modeling)
6. **MCP Security Project (CSA)** — https://modelcontextprotocol-security.io/

### Tier 2: Vendor Security Research
7. **Anthropic Security Research** — https://www.anthropic.com/research
8. **OpenAI Security Blog** — https://openai.com/blog (security posts)
9. **Google DeepMind Safety** — https://deepmind.google/safety-and-ethics/
10. **Microsoft AI Red Team** — https://www.microsoft.com/en-us/security/blog/
11. **Palo Alto Unit 42 AI Research** — https://unit42.paloaltonetworks.com/
12. **NVIDIA AI Red Team** — https://developer.nvidia.com/blog/ (security posts)
13. **Wiz AI Security** — https://wiz.io/blog

### Tier 3: Academic & Conference Research
14. **arXiv cs.CR (Cryptography and Security)** — AI security papers
15. **DEF CON AI Village** — https://aivillage.org/
16. **Chaos Communication Congress (CCC)** — 39C3 AI security talks
17. **Black Hat / RSA Conference** — AI security talks
18. **IEEE S&P, USENIX Security, CCS** — Academic conferences

### Tier 4: CVE & Incident Databases
19. **NVD (National Vulnerability Database)** — https://nvd.nist.gov/
20. **MITRE CVE** — https://cve.mitre.org/
21. **AI Incident Database** — https://incidentdatabase.ai/

### Tier 5: Industry Analysis
22. **Gartner AI Security** — Market analysis
23. **Recorded Future / CrowdStrike / Mandiant** — Threat intelligence
24. **Security vendor blogs** — Trend Micro, Qualys, Oligo, eSentire, etc.

---

## Key Attack Concepts

### The Lethal Trifecta (Simon Willison)

The combination of three capabilities that makes AI systems critically vulnerable to data exfiltration:

1. **Access to private data** — The AI can read sensitive information
2. **Exposure to untrusted content** — The AI processes external inputs an attacker can control
3. **External communication ability** — The AI can send data outside the organization

> "If your agent combines these three features, an attacker can easily trick it into accessing your private data and sending it to that attacker."

**Defense:** Treat "exposure to untrusted content" as a taint event. Once tainted, block all actions with exfiltration potential.

### The AI Kill Chain (Johann Rehberger)

Extension of lethal trifecta to include action-based attacks:

1. **Prompt Injection** → Entry point via untrusted content
2. **Confused Deputy Behavior** → Agent acts on attacker's behalf
3. **Automatic Tool Invocation** → Actions executed without human verification

**Key insight:** Many systems attempt human-in-the-loop protection, but attacks can rewrite agent configuration to allow-list dangerous tools for future invocations.

### ZombAIs (Johann Rehberger)

Long-term prompt injection persistence in AI coding agents:
- Injected instructions persist across sessions
- Agent continues malicious behavior until explicitly reset
- Often undetected because behavior appears "normal"

### AI ClickFix (Johann Rehberger)

Adaptation of nation-state TTPs (e.g., ClickFix social engineering) to AI computer-use systems:
- Tricks AI agents into executing malicious actions
- Can achieve full system compromise
- Exploits agent trust in visual/text instructions

### AgentHopper (Johann Rehberger)

AI virus research demonstrating worm-like propagation:
- Self-replicating through agent systems
- Chains vulnerabilities across multiple agents
- Demonstrates how compromised agents can infect others

### CFS Model (Pillar Security)

Three components that make indirect prompt injection succeed:

1. **Context** — Injection appears in trusted context
2. **Format** — Instructions formatted as authoritative
3. **Salience** — Injection is prominent enough to influence behavior

### Memory Poisoning Persistence

Unlike traditional attacks, memory poisoning scales across time:
- One well-placed injection compromises months of agent interactions
- Agent defends false beliefs when questioned (sleeper agent scenario)
- Traditional incident response can't contain what it can't detect

### Cascade Failure Propagation

In multi-agent systems:
- Single compromised agent can poison 87% of downstream decision-making within 4 hours
- SIEM shows symptoms (50 failed transactions) but not root cause (single poisoned agent)
- Attacker gets free reconnaissance time while defenders chase symptoms

---

## Risk Statistics to Include

When relevant, BB debates should reference real-world deployment statistics:

### Deployment & Exposure Stats
- **Only 37%** of organizations assess AI tool security before deployment (WEF Global Cybersecurity Outlook 2025)
- **42%** of organizations actively implementing LLMs; **45%** exploring implementation
- **70%+** of enterprise AI deployments expected to involve multi-agent systems by mid-2025
- **85%+** of organizations using managed or self-hosted AI in cloud environments
- **Only 48%** of employees have received AI-related security training (National Cybersecurity Alliance 2024)

### Attack & Vulnerability Stats
- **94.4%** of LLM agents vulnerable to prompt injection (Lupinacci et al. research)
- **83.3%** vulnerable to retrieval-based backdoors
- **100%** vulnerable to inter-agent trust exploits
- **82.4%** of models compromised through inter-agent trust exploitation
- **52.9%** vulnerable to RAG backdoor attacks
- **41.2%** vulnerable to direct prompt injection
- **Only 5.9%** (1/17 models) resistant to all attack vectors
- **72%** surge in AI-assisted cyber attacks in 2025 (SecurityWeek Cyber Insights)
- **40%** increase in attacks targeting RAG pipelines in 2024
- **30+ documented cases** of system prompt leakage exposing API keys/workflows in 2024
- **15%** of LLM operational costs from uncontrolled resource usage (2024 enterprise reports)

### Attack Speed Stats
- Ransomware lifecycle with agentic AI: **~25 minutes** (Palo Alto Unit 42)
- Mean time to exfiltrate: **9 days (2021) → 2 days (2024)** → many under **1 hour**
- Time to exploit new CVEs: **63 days (2019) → 32 days (2022) → 5 days (2023)**
- Cascade failure propagation: **87% of downstream systems poisoned within 4 hours**

### Real Incident Examples
- **Samsung** — Engineers leaked source code via ChatGPT
- **JPMorgan/Goldman Sachs** — Restricted ChatGPT after sensitive data sharing
- **ServiceNow Now Assist** — Second-order prompt injection via agent hierarchy (late 2025)
- **Microsoft Copilot EchoLeak** — CVE-2025-32711 email-triggered data exfiltration
- **Ollama CVE-2024-37032** — DoS and model poisoning in open-source LLM framework
- **Arup** — $25M loss from deepfake video conference fraud (Sept 2025)
- **Manufacturing company** — $3.2M fraudulent orders via compromised vendor-validation agent
- **GitHub MCP** — Private repo exfiltration via poisoned public issue
- **Supabase Cursor** — SQL injection via support ticket prompt injection
- **WhatsApp MCP** — Full chat history exfiltration via tool poisoning chain

---

## OWASP LLM Top 10 (2025) Quick Reference

| # | Vulnerability | Core Risk |
|---|---------------|-----------|
| LLM01 | Prompt Injection | Manipulated inputs override model behavior |
| LLM02 | Sensitive Information Disclosure | Model leaks PII, credentials, proprietary data |
| LLM03 | Supply Chain | Compromised models, datasets, plugins |
| LLM04 | Data and Model Poisoning | Training data corruption introduces vulnerabilities |
| LLM05 | Improper Output Handling | Unvalidated outputs enable XSS, RCE |
| LLM06 | Excessive Agency | Unchecked autonomy enables harmful actions |
| LLM07 | System Prompt Leakage | Exposed instructions reveal security architecture |
| LLM08 | Vector and Embedding Weaknesses | RAG/embedding manipulation corrupts knowledge |
| LLM09 | Misinformation | Model generates plausible false information |
| LLM10 | Unbounded Consumption | Resource exhaustion, DoS, cost attacks |

---

## OWASP Agentic AI Top 10 Quick Reference

| # | Threat | Core Risk |
|---|--------|-----------|
| 1 | Agent Behavior Hijacking | Attacker manipulates agent decision-making |
| 2 | Tool Misuse and Exploitation | Agent abuses integrated tools/APIs |
| 3 | Identity and Privilege Abuse | Escalation through agent permissions |
| 4 | Memory Poisoning | Corrupted long-term memory affects behavior |
| 5 | Cascading Hallucinations | False info propagates across agent systems |
| 6 | Human-in-the-Loop Bypass | Circumventing approval checkpoints |
| 7 | Resource Overload | Overwhelming agent compute/memory |
| 8 | Supply Chain Compromise | Poisoned frameworks, tools, or model weights |
| 9 | Goal/Planning Manipulation | Subtle alteration of agent objectives |
| 10 | Multi-Agent Trust Exploitation | Abuse of agent-to-agent communication |
| 11 | Repudiation and Untraceability | Insufficient logging makes actions untraceable |
| 12 | Agent Communication Poisoning | Manipulating inter-agent channels |
| 13 | Rogue Agents | Compromised agents outside monitoring |
| 14 | Human Attacks on Multi-Agent Systems | Exploiting delegation and trust relationships |
| 15 | Human Manipulation | Abusing human-agent interactions |

---

## MCP Security Quick Reference

### MCP Client Top 10 Risks
1. Server impersonation and spoofing
2. Credential/token theft from client storage
3. Tool definition manipulation
4. Unauthorized server connections
5. Client-side injection via malicious server responses
6. Insufficient server validation
7. Permission scope creep
8. Session hijacking
9. Insecure credential storage
10. Lack of transport security

### MCP Server Top 10 Risks
1. Command injection in tool handlers
2. Path traversal and file access
3. OAuth token aggregation (single breach = all services)
4. Tool poisoning via description manipulation
5. Rug pull attacks (post-approval tool modification)
6. Sandbox escape
7. Insufficient input validation
8. Information disclosure via error messages
9. Denial of service via resource exhaustion
10. Supply chain compromise of server dependencies

### Key MCP CVEs
- **CVE-2025-6514** — mcp-remote command injection (CVSS 9.6)
- **Anthropic Filesystem-MCP** — Sandbox escape and symlink bypass
- **Anthropic MCP Inspector** — Unauthenticated RCE

---

## MITRE ATLAS Tactics (Relevant Subset)

| Tactic | Description | Example Techniques |
|--------|-------------|-------------------|
| Reconnaissance | Gathering info about ML system | Discover model family, ontology |
| Resource Development | Building attack infrastructure | Acquire adversarial tools, malicious prompts |
| Initial Access | Gaining foothold | Prompt injection, API exploitation |
| ML Model Access | Obtaining model access | API access, physical environment access |
| Execution | Running adversarial ML | Craft adversarial data (AML.T0043) |
| Persistence | Maintaining access | Poison training data, embed backdoors |
| Defense Evasion | Avoiding detection | Obfuscate injections, use encoding |
| Exfiltration | Extracting data | Exfiltration via ML Inference API (AML.T0024) |
| Impact | Causing damage | Model denial of service, output manipulation |

**Note:** October 2025 ATLAS update added 14 agentic techniques covering multi-agent scenarios.

---

## Trigger Keywords

**Infrastructure triggers:** firewall, network, IAM, zero-trust, API gateway, cloud security, AWS, GCP, Azure, Kubernetes, container, service account, credential, S3, data lake, Ray, MLflow, SageMaker, Vertex AI

**Model-level triggers:** training data, poisoning, backdoor, adversarial, model extraction, model theft, inference attack, membership inference, embedding, vector database, RAG, fine-tuning, weights, checkpoint

**Agentic triggers:** agent, autonomous, tool use, function calling, MCP, plugin, excessive agency, permission, privilege, human-in-the-loop, memory, planning, multi-agent, orchestration, workflow, Claude Code, Copilot, Cursor, ZombAI, sleeper agent

**Prompt triggers:** prompt injection, jailbreak, system prompt, guardrail, filter bypass, indirect injection, output handling, content filter, safety, alignment, refusal, roleplay attack, lethal trifecta, AI kill chain

**MCP/Protocol triggers:** MCP, Model Context Protocol, tool poisoning, rug pull, OAuth aggregation, server security, tool definition, sampling, protocol, connector, integration

**Multi-agent triggers:** multi-agent, inter-agent, trust chain, cascade, agent-to-agent, swarm, orchestration, delegation, impersonation, collusion, rogue agent

**Framework triggers:** OWASP, MITRE ATLAS, NIST, CVE, red team, penetration test, vulnerability, exploit, threat model, MAESTRO

---

## Debate Output Format

### Standard Format
```
## [Topic]: [Specific Question]

### 🛡️ [Defender Role] Position
[2-4 paragraphs on defensive approach]
- Key mitigations
- Industry best practices
- Links to relevant sources

### 🔴 [Attacker Role] Position  
[2-4 paragraphs on attack vectors]
- How the attack works
- Real-world examples or CVEs
- Why defenses fail

### ⚖️ Current Reality
[1-2 paragraphs on actual deployment landscape]
- Risk statistics
- What most organizations actually do
- Gap between best practice and reality

### 📚 Sources Consulted
[List of sources searched and cited]
```

### Comparative Format (for cross-cutting issues)
```
## [Topic]: Multi-Perspective Analysis

### Infrastructure View (Network Hardener vs. Infra Breaker)
[Debate from traditional security lens]

### Model View (Model Guardian vs. ML Attacker)
[Debate from ML security lens]

### Agent View (Agent Wrangler vs. Autonomy Exploiter)
[Debate from agentic systems lens]

### Prompt View (Prompt Fortifier vs. Injection Artist)
[Debate from input/output security lens]

### Protocol View (Protocol Defender vs. Protocol Exploiter)
[Debate from MCP/integration security lens]

### Multi-Agent View (Trust Architect vs. Cascade Attacker)
[Debate from multi-agent trust lens]

### Synthesis
[How these perspectives connect]
```

---

## Subset Commands

| Command | Effect |
|---------|--------|
| `"TEMPT this, infrastructure focus"` | Emphasize BB Pair 1 (Network Hardener vs. Infra Breaker) |
| `"TEMPT this, model security focus"` | Emphasize BB Pair 2 (Model Guardian vs. ML Attacker) |
| `"TEMPT this, agentic focus"` | Emphasize BB Pair 3 (Agent Wrangler vs. Autonomy Exploiter) |
| `"TEMPT this, prompt security focus"` | Emphasize BB Pair 4 (Prompt Fortifier vs. Injection Artist) |
| `"TEMPT this, MCP focus"` | Emphasize BB Pair 5 (Protocol Defender vs. Protocol Exploiter) |
| `"TEMPT this, multi-agent focus"` | Emphasize BB Pair 6 (Trust Architect vs. Cascade Attacker) |
| `"TEMPT this, full stack"` | All six BB pairs debate the topic |
| `"TEMPT this, OWASP mapping"` | Map discussion to specific OWASP LLM Top 10 items |
| `"TEMPT this, MITRE ATLAS mapping"` | Map discussion to MITRE ATLAS techniques |
| `"TEMPT this, with CVEs"` | Prioritize specific vulnerability references |
| `"TEMPT this, enterprise reality"` | Emphasize real-world deployment statistics and gaps |
| `"TEMPT this, bleeding edge"` | Prioritize Tier 0 sources (researcher blogs, Discord, Reddit) |
| `"TEMPT this, lethal trifecta analysis"` | Analyze through lethal trifecta framework |
| `"TEMPT this, kill chain analysis"` | Analyze through AI kill chain framework |

---

## Research Requirements

### Minimum Search Requirements

| Question Type | Minimum Searches | Notes |
|---------------|------------------|-------|
| Single attack vector | 2-3 searches | Cover attack + defense perspectives |
| Defense strategy | 3-4 searches | Include framework guidance + vendor practices |
| Comparative analysis | 4-6 searches | At least 1 per perspective |
| Full stack analysis | 6-10 searches | Cover all six BB pair domains |
| Bleeding edge query | 3-5 searches | Must include Tier 0 sources |

### Mandatory Source Checks

For EVERY AI security BB debate, Claude MUST attempt to retrieve:
1. Relevant OWASP entry (LLM Top 10 or Agentic Top 10)
2. MITRE ATLAS technique if applicable
3. At least one 2024-2025 dated source
4. Real-world incident or CVE if exists
5. **For novel/emerging attacks:** Check Tier 0 sources first (embracethered.com, simonwillison.net)

### Citation Format

```
According to [Source Name], [specific claim]. [Link if available]
```

Example:
> According to OWASP LLM Top 10 2025, prompt injection remains the #1 vulnerability, with 94.4% of LLM agents found vulnerable in academic testing.

> According to Johann Rehberger's Month of AI Bugs research, ZombAIs demonstrate long-term prompt injection persistence in coding agents that survives across sessions.

---

## Failure Mode Protocol

If web search unavailable or returns no results:

1. **Inform the user:** "I was unable to retrieve current sources for [topic]."
2. **Offer alternatives:** "I can provide a response based on training data, but it won't include the latest research. Proceed?"
3. **Never silently fall back** to training-data-only responses for this profile.

---

## Example Activations

### Example 1: MCP Security Query

**User:** "TEMPT this: How do we secure our MCP server deployment?"

**Claude's Process:**
1. [DETECT] AI_CYBERSECURITY profile triggered by "MCP", "secure"
2. [FETCH] web_fetch this profile URL
3. [RESEARCH]
   - Search: "MCP Model Context Protocol security vulnerabilities 2025"
   - Search: "MCP server command injection CVE"
   - Search: "tool poisoning MCP attack"
   - Search: "MCP security best practices"
4. [SELECT BB PAIRS] 
   - Primary: Protocol Defender vs. Protocol Exploiter (MCP-specific)
   - Secondary: Agent Wrangler vs. Autonomy Exploiter (tool access)
5. [GENERATE] Build debates using retrieved sources
6. [CITE] Include citations and links
7. [OUTPUT] Present with source attribution

### Example 2: Multi-Agent Trust Query

**User:** "TEMPT this: What are the risks of multi-agent AI systems?"

**Claude's Process:**
1. [DETECT] AI_CYBERSECURITY profile triggered by "multi-agent", "risks"
2. [FETCH] web_fetch this profile URL
3. [RESEARCH]
   - Search: "multi-agent AI trust exploitation security 2025"
   - Search: "OWASP agentic AI multi-agent threats"
   - Search: "agent-to-agent attack cascade failure"
   - Search: "inter-agent trust vulnerability research"
4. [SELECT BB PAIRS] 
   - Primary: Trust Architect vs. Cascade Attacker (multi-agent focus)
   - Secondary: Agent Wrangler vs. Autonomy Exploiter (agent-level)
5. [GENERATE] Build debates using retrieved sources
6. [CITE] Include citations and links
7. [OUTPUT] Present with source attribution

### Example 3: Bleeding Edge Query

**User:** "TEMPT this, bleeding edge: What's the latest on prompt injection in coding agents?"

**Claude's Process:**
1. [DETECT] AI_CYBERSECURITY profile + "bleeding edge" subset
2. [FETCH] web_fetch this profile URL
3. [RESEARCH] — Prioritize Tier 0 sources:
   - Search: "site:embracethered.com prompt injection coding agent"
   - Search: "Month of AI Bugs coding agent vulnerabilities"
   - Search: "ZombAI prompt injection persistence"
   - Search: "AI kill chain coding agent exploit"
4. [SELECT BB PAIRS] 
   - Primary: Prompt Fortifier vs. Injection Artist
   - Secondary: Agent Wrangler vs. Autonomy Exploiter
5. [GENERATE] Build debates emphasizing latest researcher findings
6. [CITE] Include citations from researcher blogs
7. [OUTPUT] Present with source attribution

### Example 4: RAG Pipeline Security

**User:** "TEMPT this: How should we secure our RAG pipeline?"

**Claude's Process:**
1. [DETECT] AI_CYBERSECURITY profile triggered by "RAG", "secure", "pipeline"
2. [FETCH] web_fetch this profile URL
3. [RESEARCH]
   - Search: "RAG security vulnerabilities 2024 2025"
   - Search: "OWASP LLM08 vector embedding weaknesses"
   - Search: "PoisonedRAG knowledge base attack"
   - Search: "RAG pipeline defense best practices"
4. [SELECT BB PAIRS] 
   - Primary: Model Guardian vs. ML Attacker (RAG = model-level concern)
   - Secondary: Prompt Fortifier vs. Injection Artist (injection via retrieved content)
5. [GENERATE] Build debates using retrieved sources
6. [CITE] Include citations and links
7. [OUTPUT] Present with source attribution

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | February 2026 | Initial profile creation |
| 1.1 | February 2026 | Added BB Pair 5 (MCP Protocol Security), BB Pair 6 (Multi-Agent Trust), Tier 0 bleeding edge sources, attack concepts (Lethal Trifecta, AI Kill Chain, ZombAIs, AI ClickFix, AgentHopper, CFS Model), expanded memory poisoning and output handling coverage, MCP security quick reference, new subset commands |

---

*Profile created for TEMPT v4.0 framework. Integrate with existing TEMPT project instructions.*
