# TEMPT Profile: Agentic Programming

## Metadata

| Field | Value |
|-------|-------|
| **Name** | Agentic Programming |
| **Version** | 1.0 |
| **Created** | 01-30-2026 |
| **Freshness Class** | months |
| **Primary Use Case** | Software development, architecture decisions, API design, code review, technical specifications |

---

## Trigger Keywords

### Tier 1 — Unambiguous (Auto-load silently)

```
code, function, class, method, variable, parameter, argument,
API, endpoint, REST, GraphQL, webhook, SDK, library, framework,
git, commit, branch, merge, pull request, PR, repository, repo,
deploy, deployment, CI/CD, pipeline, build, release, rollback,
bug, error, exception, debug, stack trace, log, crash,
database, SQL, NoSQL, query, schema, migration, ORM,
frontend, backend, fullstack, microservice, monolith,
React, Vue, Angular, Node, Python, JavaScript, TypeScript,
Docker, Kubernetes, AWS, Azure, GCP, cloud, serverless,
authentication, authorization, OAuth, JWT, token, session,
test, unit test, integration test, TDD, coverage, mock,
refactor, technical debt, code review, linting, formatting,
spec, specification, requirements, user story, acceptance criteria
```

### Tier 2 — Likely (Auto-load with confirmation)

```
development, developer, engineering, software, application, app,
server, client, request, response, payload, header,
interface, implementation, abstraction, pattern, architecture,
async, await, promise, callback, event, handler, listener,
state, store, reducer, context, hook, component, module,
route, controller, model, view, service, middleware,
cache, session, cookie, storage, memory, disk,
security, vulnerability, injection, XSS, CSRF, sanitize,
performance, optimization, latency, throughput, bottleneck,
scale, scaling, load balancer, horizontal, vertical
```

### Tier 3 — Ambiguous (Ask if sole match)

```
design, build, create, make, fix, update, change,
system, service, process, flow, logic, structure
```

---

## Freshness Requirements

| Data Type | Freshness Threshold | Auto-Inject |
|-----------|---------------------|-------------|
| Security vulnerabilities (CVE) | <30 days | "latest" or "[year]" |
| Framework major versions | <6 months | "[framework] [year]" |
| API documentation | <6 months | "current" or "latest docs" |
| Best practices / patterns | <12 months | no injection |
| Language features | <12 months | "[language] [version]" |
| Foundational concepts | any | no injection |

**Default freshness:** <6 months

**Stale handling:** Generally acceptable for established patterns; flag for security topics

---

## Source Priority

1. **Official Documentation** — Authoritative source
   - Language docs (python.org, developer.mozilla.org)
   - Framework docs (reactjs.org, docs.djangoproject.com)
   - Cloud provider docs (AWS, Azure, GCP)

2. **Official Repositories** — Implementation truth
   - GitHub/GitLab repos for libraries
   - README, CHANGELOG, release notes
   - Issue trackers for known bugs

3. **Security Databases** — For vulnerability checks
   - CVE database (cve.mitre.org)
   - GitHub Security Advisories
   - Snyk, npm audit databases

4. **Technical Blogs (Authoritative)** — Deep explanations
   - Official engineering blogs (Netflix, Uber, Stripe)
   - Core maintainer blogs

5. **Community Resources** — Supplementary
   - Stack Overflow (high-vote answers)
   - Dev.to, Medium (verify author credentials)

**Avoid:** Outdated tutorials, AI-generated code dumps, sources without versions

---

## Additional BB Pairs

| Dimension | Builder | Breaker | Trigger |
|-----------|---------|---------|---------|
| Architecture | Solution Architect | Technical Debt Analyst | architecture, design |
| Security | Security Architect | Penetration Tester | auth, security, token |
| Scalability | Scale Engineer | Bottleneck Hunter | scale, performance |
| Maintainability | Clean Code Advocate | Legacy Code Survivor | refactor, debt |
| Testing | Test Strategist | Edge Case Finder | test, coverage |
| DevOps | Deployment Strategist | Outage Historian | deploy, CI/CD |

### Pair Descriptions

**Architecture: Solution Architect / Technical Debt Analyst**
- Builder: Clean design, separation of concerns, flexibility
- Breaker: Over-engineering, premature abstraction, complexity

**Security: Security Architect / Penetration Tester**
- Builder: Defense in depth, secure by default
- Breaker: Attack vectors, bypass scenarios, exploits

**Scalability: Scale Engineer / Bottleneck Hunter**
- Builder: Horizontal scaling, caching, async
- Breaker: Hidden bottlenecks, scaling cliffs

**Maintainability: Clean Code Advocate / Legacy Code Survivor**
- Builder: Readability, documentation, consistency
- Breaker: Real-world maintenance burden, deadline pressure

**Testing: Test Strategist / Edge Case Finder**
- Builder: Coverage goals, test pyramid, confidence
- Breaker: Untestable paths, flaky tests, false confidence

**DevOps: Deployment Strategist / Outage Historian**
- Builder: Automation, rollback, monitoring
- Breaker: Deployment failures, cascading outages

---

## Anchoring Instructions

### Search Query Modifications

- **Include version numbers** (e.g., "React 18 hooks")
- **Specify language/framework** explicitly
- **Add "official docs"** to prioritize documentation
- **Include "CVE"** for security searches
- **Add year** for dated content

### Verification Requirements

- Verify code examples compile/run
- Check version compatibility
- Cross-reference security with CVE database
- Note language/framework specificity

### Domain-Specific Flags

| Flag | Condition |
|------|-----------|
| ⚠️ VERSION SPECIFIC | Advice depends on specific version |
| ⚠️ SECURITY SENSITIVE | Involves auth, crypto, user data |
| ⚠️ BREAKING CHANGE | Major version may break |
| ⚠️ DEPRECATED | API/pattern is deprecated |

---

## Conflict Behavior

| Conflict | Resolution |
|----------|------------|
| Freshness | Yield to Stock/Macro for their domains |
| Sources | Documentation trumps blogs |
| BB Pairs | Additive |

---

## TEMPT-Specific Note

**This profile respects TEMPT's spec-only constraint.**
- TEMPT produces specifications, not code
- Architecture decisions debated, not implemented
- Output remains spec files for downstream tools

---

## Example Activations

**Example 1: Architecture**
```
Query: "Should we use microservices or monolith?"
Detection: Tier 1 — microservices, monolith
BB Pairs: Architecture, Scalability, Maintainability
```

**Example 2: Security**
```
Query: "Is our JWT implementation secure?"
Detection: Tier 1 — JWT, secure
BB Pairs: Security
Flag: ⚠️ SECURITY SENSITIVE
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 01-30-2026 | Initial profile |
