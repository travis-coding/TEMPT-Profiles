# AI_CYBERSECURITY.md
## TEMPT Profile: AI & LLM Security (v1.2)

---

## Profile Overview

**Domain:** AI/ML Cybersecurity — LLMs, Agentic Systems, Prompt Security  
**Recency Filter:** Prioritize 2024-2025 sources (post-GPT-4 era)  
**Philosophy:** This profile is a research MAP, not a research DUMP. All statistics, incidents, and attack details are retrieved live via TEMPT research protocol.

---

## BB Pair Configuration

Six specialized BB pairs, each with a Red Team adversary.

### BB Pair 1: Network Hardener vs. Infra Breaker
| Role | Persona |
|------|---------|
| **Defender** | Classic security engineer. Firewalls, network segmentation, IAM, zero-trust. Views AI as "just another application." |
| **Attacker** | Pentester targeting AI infrastructure. Exposed APIs, overprivileged service accounts, unpatched clusters, leaky S3 buckets. |

**Debate Focus:** Cloud infrastructure, API gateways, network isolation, credential management, supply chain attacks on AI infra.

---

### BB Pair 2: Model Guardian vs. ML Attacker
| Role | Persona |
|------|---------|
| **Defender** | AI security specialist. Training data integrity, model robustness, adversarial inputs. Uses MITRE ATLAS. |
| **Attacker** | Adversarial ML researcher. Poisons data, extracts models, crafts adversarial examples, exploits embeddings. |

**Debate Focus:** Training data poisoning, model extraction, RAG poisoning, embedding attacks, membership inference.

---

### BB Pair 3: Agent Wrangler vs. Autonomy Exploiter
| Role | Persona |
|------|---------|
| **Defender** | Guardrail builder. Permission boundaries, tool access controls, human-in-the-loop, audit logging. Agency = attack surface. |
| **Attacker** | Makes agents misbehave. Exploits tool integrations, escalates privileges, turns autonomy against itself. |

**Debate Focus:** Excessive agency (OWASP LLM06), tool misuse, memory poisoning, goal hijacking, HITL bypass.

---

### BB Pair 4: Prompt Fortifier vs. Injection Artist
| Role | Persona |
|------|---------|
| **Defender** | Input/output security. Prompt templates, output validators, content filters, system prompt isolation. |
| **Attacker** | Jailbreak specialist. Bypasses filters, extracts system prompts, indirect injection via docs/web. |

**Debate Focus:** Direct/indirect injection, system prompt leakage (LLM07), output handling → RCE, encoding attacks, roleplay attacks.

---

### BB Pair 5: Protocol Defender vs. Protocol Exploiter
| Role | Persona |
|------|---------|
| **Defender** | Secures AI integration protocols. MCP hardening, OAuth management, tool registration, API isolation. |
| **Attacker** | Targets connective tissue. MCP servers, tool definitions, OAuth aggregation, protocol-level weaknesses. |

**Debate Focus:** MCP attacks (tool poisoning, rug pulls, command injection), OAuth aggregation, sandbox escape, supply chain.

---

### BB Pair 6: Trust Architect vs. Cascade Attacker
| Role | Persona |
|------|---------|
| **Defender** | Designs secure multi-agent systems. Inter-agent auth, trust boundaries, cascade failure prevention. |
| **Attacker** | Exploits agent relationships. Trust chains, impersonation, inter-agent poisoning, cascade failures. |

**Debate Focus:** Inter-agent trust exploitation, cascade attacks, agent collusion, rogue agents, communication poisoning.

---

## Source Priority Hierarchy

### Tier 0: Bleeding Edge (Check FIRST for Novel Attacks)

These sources surface vulnerabilities **weeks to months** before mainstream frameworks.

| Source | Focus | URL |
|--------|-------|-----|
| **Embrace The Red** | Real exploits, coding agent vulns, Month of AI Bugs | https://embracethered.com |
| **Simon Willison's Blog** | Conceptual frameworks, lethal trifecta, prompt injection | https://simonwillison.net |
| **Month of AI Bugs** | Vulnerability database with PoCs | https://monthofaibugs.com |
| **Invariant Labs** | MCP exploits, tool poisoning research | https://invariantlabs.ai |
| **Pillar Security Blog** | Indirect injection, CFS model | https://pillar.security/blog |
| **Lakera AI Blog** | Prompt injection defense, attack data | https://lakera.ai/blog |
| **Lasso Security Blog** | RAG attacks, guardrail bypasses | https://lasso.security/blog |
| **HiddenLayer Innovation Hub** | Enterprise AI security | https://hiddenlayer.com/innovation-hub |

**Community Sources:**
- AI Village Discord — real-time CTF/exploit sharing
- r/LocalLLaMA — open-source jailbreaks, fine-tuning exploits
- r/ChatGPT — user-discovered vulnerabilities
- Jailbreak Tracker — live monitoring of known jailbreaks

---

### Tier 1: Authoritative Frameworks

| Source | URL |
|--------|-----|
| OWASP LLM Top 10 2025 | https://genai.owasp.org/llm-top-10/ |
| OWASP Agentic AI Top 10 | https://genai.owasp.org/ |
| MITRE ATLAS | https://atlas.mitre.org/ |
| NIST AI RMF | https://www.nist.gov/itl/ai-risk-management-framework |
| CSA MAESTRO Framework | https://cloudsecurityalliance.org/ |
| MCP Security Project | https://modelcontextprotocol-security.io/ |

---

### Tier 2: Vendor Security Research

| Source | URL |
|--------|-----|
| Anthropic Research | https://www.anthropic.com/research |
| OpenAI Security Blog | https://openai.com/blog |
| Google DeepMind Safety | https://deepmind.google/safety-and-ethics/ |
| Microsoft AI Red Team | https://www.microsoft.com/en-us/security/blog/ |
| Palo Alto Unit 42 | https://unit42.paloaltonetworks.com/ |
| NVIDIA AI Red Team | https://developer.nvidia.com/blog/ |
| Wiz AI Security | https://wiz.io/blog |

---

### Tier 3: Academic & Conferences
- arXiv cs.CR (AI security papers)
- DEF CON AI Village — https://aivillage.org/
- Black Hat / RSA / CCC
- IEEE S&P, USENIX Security, CCS

### Tier 4: CVE & Incident Databases
- NVD — https://nvd.nist.gov/
- MITRE CVE — https://cve.mitre.org/
- AI Incident Database — https://incidentdatabase.ai/

### Tier 5: Industry Analysis
- Gartner, Recorded Future, CrowdStrike, Mandiant
- Security vendor blogs (Trend Micro, Qualys, Oligo, eSentire)

---

## Trigger Keywords

**Infrastructure:** firewall, network, IAM, zero-trust, API gateway, cloud security, AWS, GCP, Azure, Kubernetes, container, credential, S3, Ray, MLflow, SageMaker, Vertex AI

**Model-level:** training data, poisoning, backdoor, adversarial, model extraction, model theft, embedding, vector database, RAG, fine-tuning, weights

**Agentic:** agent, autonomous, tool use, function calling, MCP, plugin, excessive agency, permission, privilege, human-in-the-loop, memory, planning, multi-agent, Claude Code, Copilot, Cursor

**Prompt:** prompt injection, jailbreak, system prompt, guardrail, filter bypass, indirect injection, output handling, content filter, roleplay attack

**MCP/Protocol:** MCP, Model Context Protocol, tool poisoning, rug pull, OAuth, server security, tool definition, sampling

**Multi-agent:** multi-agent, inter-agent, trust chain, cascade, swarm, orchestration, delegation, impersonation, rogue agent

**Framework:** OWASP, MITRE ATLAS, NIST, CVE, red team, vulnerability, exploit, threat model

---

## Subset Commands

| Command | Effect |
|---------|--------|
| `"TEMPT this, infrastructure focus"` | BB Pair 1 |
| `"TEMPT this, model security focus"` | BB Pair 2 |
| `"TEMPT this, agentic focus"` | BB Pair 3 |
| `"TEMPT this, prompt security focus"` | BB Pair 4 |
| `"TEMPT this, MCP focus"` | BB Pair 5 |
| `"TEMPT this, multi-agent focus"` | BB Pair 6 |
| `"TEMPT this, full stack"` | All six BB pairs |
| `"TEMPT this, OWASP mapping"` | Map to OWASP LLM/Agentic Top 10 |
| `"TEMPT this, MITRE ATLAS mapping"` | Map to MITRE ATLAS techniques |
| `"TEMPT this, with CVEs"` | Prioritize CVE references |
| `"TEMPT this, enterprise reality"` | Emphasize deployment stats and gaps |
| `"TEMPT this, bleeding edge"` | Prioritize Tier 0 sources |
| `"TEMPT this, lethal trifecta analysis"` | Apply Willison's framework |
| `"TEMPT this, kill chain analysis"` | Apply Rehberger's framework |

---

## Research Requirements

### Minimum Searches by Query Type

| Type | Searches | Notes |
|------|----------|-------|
| Single attack vector | 2-3 | Attack + defense perspectives |
| Defense strategy | 3-4 | Framework guidance + vendor practices |
| Comparative analysis | 4-6 | 1 per perspective minimum |
| Full stack analysis | 6-10 | Cover all six BB pair domains |
| Bleeding edge query | 3-5 | Must include Tier 0 sources |

### Mandatory Source Checks

Every AI security debate MUST attempt:
1. Relevant OWASP entry (LLM or Agentic Top 10)
2. MITRE ATLAS technique if applicable
3. At least one 2024-2025 dated source
4. Real-world incident or CVE if exists
5. For novel attacks: Check Tier 0 sources FIRST

---

## Output Format

### Standard Format
```
## [Topic]: [Specific Question]

### 🛡️ [Defender Role] Position
[2-4 paragraphs with mitigations, best practices, sourced claims]

### 🔴 [Attacker Role] Position
[2-4 paragraphs with attack vectors, examples, why defenses fail]

### ⚖️ Current Reality
[1-2 paragraphs: stats, actual practices, gaps]

### 📚 Sources Consulted
[List with links]
```

### Comparative Format (cross-cutting issues)
```
## [Topic]: Multi-Perspective Analysis

### [Relevant BB Pair View]
[Debate from that lens]

[Repeat for each relevant BB pair]

### Synthesis
[How perspectives connect]
```

---

## Failure Mode

If web search unavailable or returns no results:
1. Inform user: "Unable to retrieve current sources for [topic]."
2. Offer: "I can respond from training data, but it won't include latest research. Proceed?"
3. **Never silently fall back** to training-data-only responses.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Feb 2026 | Initial creation |
| 1.1 | Feb 2026 | Added BB Pairs 5-6, Tier 0 sources, attack concepts, expanded coverage |
| 1.2 | Feb 2026 | **Refactored:** Removed pre-baked stats, incidents, framework tables. Profile is now a research MAP — all details retrieved live via TEMPT protocol. |

---

*Profile for TEMPT v4.0 framework. Research map, not research dump.*
