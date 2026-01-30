# TEMPT Profile Template

Use this template to create new domain-specific profiles for TEMPT v4.0.

---

## Instructions

1. Copy this template
2. Replace all `[bracketed]` placeholders
3. Define trigger keywords carefully (see guidance below)
4. Save as `profiles/[PROFILE_NAME].md`
5. Test with sample queries

---

## Profile: [PROFILE NAME]

### Metadata

| Field | Value |
|-------|-------|
| **Name** | [Profile Name] |
| **Version** | 1.0 |
| **Created** | [MM-DD-YYYY] |
| **Freshness Class** | [real-time / hours / days / weeks / months / any] |
| **Primary Use Case** | [1-2 sentence description] |

---

### Trigger Keywords

#### Tier 1 — Unambiguous (Auto-load silently)

High-confidence keywords unique to this domain.

```
[keyword1], [keyword2], [keyword3]
```

#### Tier 2 — Likely (Auto-load with confirmation)

Medium-confidence keywords common in this domain.

```
[keyword1], [keyword2], [keyword3]
```

#### Tier 3 — Ambiguous (Ask if sole match)

Low-confidence keywords shared across domains.

```
[keyword1], [keyword2], [keyword3]
```

---

### Freshness Requirements

| Data Type | Freshness Threshold | Auto-Inject |
|-----------|---------------------|-------------|
| [Data type 1] | [threshold] | [temporal qualifier] |
| [Data type 2] | [threshold] | [qualifier] |

**Default freshness:** [threshold]

---

### Source Priority

1. **[Source category 1]** — [Why preferred]
2. **[Source category 2]** — [Why]
3. **[Source category 3]** — [Why]

**Avoid:** [Sources to skip]

---

### Additional BB Pairs

| Dimension | Builder | Breaker | Trigger |
|-----------|---------|---------|---------|
| [Dimension 1] | [Role] | [Role] | [keywords] |
| [Dimension 2] | [Role] | [Role] | [keywords] |

---

### Anchoring Instructions

- [Search query modification 1]
- [Search query modification 2]

### Domain-Specific Flags

| Flag | Condition |
|------|-----------|
| [Flag] | [When to show] |

---

### Conflict Behavior

| Conflict | Resolution |
|----------|------------|
| Freshness | [Behavior] |
| Sources | [Behavior] |
| BB Pairs | Additive |

---

### Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | [MM-DD-YYYY] | Initial profile |

---

## Keyword Selection Guidance

### Good Tier 1 Keywords
- Proper nouns unique to domain
- Technical terms with clear meaning
- Abbreviations specific to field

### Good Tier 2 Keywords
- Common domain terms
- Verbs typical to domain
- General domain nouns

### Good Tier 3 Keywords
- Words with multiple domain meanings
- Generic terms (price, cost, value)

### Keywords to Avoid
- Stop words (the, is, are)
- Extremely common verbs
- Words triggering on every query
