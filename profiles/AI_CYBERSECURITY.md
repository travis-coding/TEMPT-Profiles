# AI_CYBERSECURITY.md
## TEMPT Profile: AI & LLM Security

---

## Profile Overview

**Domain:** AI/ML Cybersecurity with emphasis on Large Language Models, Agentic Systems, and Prompt Security  
**Focus:** Attack vectors, defensive mitigations, and real-world deployment risk data  
**Recency Filter:** Prioritize 2023-2025 sources (post-GPT-4 era)  
**Last Updated:** February 2026

---

## BB Pair Configuration

This profile uses **four specialized BB pairs**, each with a dedicated Red Team adversary. The debates focus on *how attacks actually work* and *what defenders are doing about it*.

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

---

### BB Pair 3: Agent Wrangler vs. Autonomy Exploiter

| Role | Persona |
|------|---------|
| **Defender:** Agent Wrangler | Builds guardrails around autonomous AI systems. Obsessed with permission boundaries, tool access controls, human-in-the-loop checkpoints, and audit logging. Knows that agency = attack surface. |
| **Attacker:** Autonomy Exploiter | Specializes in making agents do things they shouldn't. Exploits tool integrations, chains actions across systems, escalates privileges through trust relationships, and turns agent autonomy against itself. |

**Debate Focus:**  
- Excessive agency and unchecked permissions (OWASP LLM06)
- Tool misuse and unauthorized API calls
- Multi-agent trust chain exploitation
- Memory poisoning in persistent agents
- Cascading hallucination attacks
- Goal hijacking and planning manipulation
- Human-in-the-loop bypass techniques

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
- Output manipulation and improper output handling
- Multi-language and encoding attacks (Base64, ROT13)
- Image-based prompt injection (steganography, OCR exploitation)
- Roleplay and persona attacks

---

## Source Priority Hierarchy

When researching for BB debates, Claude MUST search in this order:

### Tier 1: Authoritative Standards & Frameworks
1. **OWASP LLM Top 10 2025** — https://genai.owasp.org/llm-top-10/
2. **OWASP Top 10 for Agentic Applications** — https://genai.owasp.org/
3. **MITRE ATLAS** — https://atlas.mitre.org/
4. **NIST AI Risk Management Framework** — https://www.nist.gov/itl/ai-risk-management-framework

### Tier 2: Vendor Security Research
5. **Anthropic Security Research** — https://www.anthropic.com/research
6. **OpenAI Security Blog** — https://openai.com/blog (security posts)
7. **Google DeepMind Safety** — https://deepmind.google/safety-and-ethics/
8. **Microsoft AI Red Team** — https://www.microsoft.com/en-us/security/blog/
9. **Palo Alto Unit 42 AI Research** — https://unit42.paloaltonetworks.com/

### Tier 3: Academic & Conference Research
10. **arXiv cs.CR (Cryptography and Security)** — AI security papers
11. **DEF CON AI Village** — https://aivillage.org/
12. **Black Hat / RSA Conference** — AI security talks
13. **IEEE S&P, USENIX Security, CCS** — Academic conferences

### Tier 4: CVE & Incident Databases
14. **NVD (National Vulnerability Database)** — https://nvd.nist.gov/
15. **MITRE CVE** — https://cve.mitre.org/
16. **AI Incident Database** — https://incidentdatabase.ai/

### Tier 5: Industry Analysis
17. **Gartner AI Security** — Market analysis
18. **Recorded Future / CrowdStrike / Mandiant** — Threat intelligence
19. **Security vendor blogs** — Trend Micro, Qualys, Oligo, Lasso, etc.

---

## Risk Statistics to Include

When relevant, BB debates should reference real-world deployment statistics:

### Deployment & Exposure Stats
- **Only 37%** of organizations assess AI tool security before deployment (WEF Global Cybersecurity Outlook 2025)
- **42%** of organizations actively implementing LLMs; **45%** exploring implementation (AI Global GenAI Security Readiness Report)
- **85%+** of organizations using managed or self-hosted AI in cloud environments
- **Only 48%** of employees have received AI-related security training (National Cybersecurity Alliance 2024)

### Attack & Vulnerability Stats
- **94.4%** of LLM agents vulnerable to prompt injection (Lupinacci et al. research)
- **83.3%** vulnerable to retrieval-based backdoors
- **100%** vulnerable to inter-agent trust exploits
- **72%** surge in AI-assisted cyber attacks in 2025 (SecurityWeek Cyber Insights)
- **40%** increase in attacks targeting RAG pipelines in 2024
- **30+ documented cases** of system prompt leakage exposing API keys/workflows in 2024
- **15%** of LLM operational costs from uncontrolled resource usage (2024 enterprise reports)

### Attack Speed Stats
- Ransomware lifecycle with agentic AI: **~25 minutes** (Palo Alto Unit 42)
- Mean time to exfiltrate: **9 days (2021) → 2 days (2024)** → many under **1 hour**
- Time to exploit new CVEs: **63 days (2019) → 32 days (2022) → 5 days (2023)**

### Real Incident Examples
- **Samsung** — Engineers leaked source code via ChatGPT
- **JPMorgan/Goldman Sachs** — Restricted ChatGPT after sensitive data sharing
- **ServiceNow Now Assist** — Second-order prompt injection via agent hierarchy (late 2025)
- **Microsoft Copilot EchoLeak** — CVE-2025-32711 email-triggered data exfiltration
- **Ollama CVE-2024-37032** — DoS and model poisoning in open-source LLM framework
- **Arup** — $25M loss from deepfake video conference fraud (Sept 2025)

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

---

## Trigger Keywords

**Infrastructure triggers:** firewall, network, IAM, zero-trust, API gateway, cloud security, AWS, GCP, Azure, Kubernetes, container, service account, credential, S3, data lake, Ray, MLflow, SageMaker, Vertex AI

**Model-level triggers:** training data, poisoning, backdoor, adversarial, model extraction, model theft, inference attack, membership inference, embedding, vector database, RAG, fine-tuning, weights, checkpoint

**Agentic triggers:** agent, autonomous, tool use, function calling, MCP, plugin, excessive agency, permission, privilege, human-in-the-loop, memory, planning, multi-agent, orchestration, workflow, Claude Code, Copilot, Cursor

**Prompt triggers:** prompt injection, jailbreak, system prompt, guardrail, filter bypass, indirect injection, output handling, content filter, safety, alignment, refusal, roleplay attack

**Framework triggers:** OWASP, MITRE ATLAS, NIST, CVE, red team, penetration test, vulnerability, exploit, threat model

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
| `"TEMPT this, full stack"` | All four BB pairs debate the topic |
| `"TEMPT this, OWASP mapping"` | Map discussion to specific OWASP LLM Top 10 items |
| `"TEMPT this, MITRE ATLAS mapping"` | Map discussion to MITRE ATLAS techniques |
| `"TEMPT this, with CVEs"` | Prioritize specific vulnerability references |
| `"TEMPT this, enterprise reality"` | Emphasize real-world deployment statistics and gaps |

---

## Research Requirements

### Minimum Search Requirements

| Question Type | Minimum Searches | Notes |
|---------------|------------------|-------|
| Single attack vector | 2-3 searches | Cover attack + defense perspectives |
| Defense strategy | 3-4 searches | Include framework guidance + vendor practices |
| Comparative analysis | 4-6 searches | At least 1 per perspective |
| Full stack analysis | 6-10 searches | Cover all four BB pair domains |

### Mandatory Source Checks

For EVERY AI security BB debate, Claude MUST attempt to retrieve:
1. Relevant OWASP entry (LLM Top 10 or Agentic Top 10)
2. MITRE ATLAS technique if applicable
3. At least one 2024-2025 dated source
4. Real-world incident or CVE if exists

### Citation Format

```
According to [Source Name], [specific claim]. [Link if available]
```

Example:
> According to OWASP LLM Top 10 2025, prompt injection remains the #1 vulnerability, with 94.4% of LLM agents found vulnerable in academic testing.

---

## Failure Mode Protocol

If web search unavailable or returns no results:

1. **Inform the user:** "I was unable to retrieve current sources for [topic]."
2. **Offer alternatives:** "I can provide a response based on training data, but it won't include the latest research. Proceed?"
3. **Never silently fall back** to training-data-only responses for this profile.

---

## Example Activation

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

---

*Profile created for TEMPT v4.0 framework. Integrate with existing TEMPT project instructions.*
