# Threat Register – AI Security Review Copilot

| ID | Threat | Reference | Likelihood | Impact | Control | Status |
|----|--------|-----------|------------|--------|---------|--------|
| T-001 | Hidden instructions in an uploaded architecture document hijack the reviewer | OWASP LLM01 Prompt Injection | High | High | Treat all documents as untrusted data; no tool can act on document text | Open |
| T-002 | Confidential client architecture leaks via output, logs or the model provider | OWASP LLM02 Sensitive Information Disclosure | Medium | High | Data classification; redacted logging; provider retention terms | Open |
| T-003 | Model invents threats or evidence not present in the inputs | OWASP LLM09 Misinformation | High | Medium | No source, no finding; citation check before output | Open |
| T-004 | Agent takes action beyond drafting a review | OWASP LLM06 Excessive Agency | Low | High | Read-only tools; human sign-off on every review | Open |
| T-005 | Private keys or API keys committed to a public repo | Supply chain / secrets | Medium | High | Keys outside repo; `.gitignore` for `.env`; GitHub secret scanning | Mitigated |