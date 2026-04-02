# Roadmap

## v5.0 (Current)

The current release focuses on research grounding, structured reasoning, and community foundation:

- **Research grounding**: Full evidence documentation with citations, scope notes, and honest limitations (`docs/RESEARCH.md`)
- **Risks matrix**: Documented risks of grey rocking with mitigation strategies (`docs/SAFETY.md`)
- **Chain-of-Thought prompting**: 8-step structured reasoning chain for consistent response generation
- **EAR statements**: Eddy's Empathy-Attention-Respect method for Level 4 urgent matters
- **Hybrid communication modes**: Grey Rock Strict, Grey Rock Cooperative, and Normal modes per-contact
- **Simulation scenarios**: Interactive examples for litigation, vendor disputes, and board conflicts (`examples/scenarios.md`)
- **Contribution framework**: Guidelines for research, code, and documentation contributions (`CONTRIBUTING.md`)

## v6.0 (Planned)

Core implementation and testing infrastructure:

- **Core implementation code**: Python/JS agent wrapper implementing the protocol as executable code
- **Unit tests for BIFF compliance scoring**: Automated validation that generated responses meet BIFF criteria (brevity, informativeness, neutrality, firmness)
- **Hallucination resistance testing**: Test suite verifying the agent does not fabricate records, confirm unverified claims, or generate false details
- **Analytics dashboard**: Message volume tracking, escalation trend visualization, extinction burst detection, and per-contact engagement metrics
- **Draft review tracking**: `drafts` table (id, contact_id, incoming_message_id, draft_content, status, reviewer_actions, sent_at) for complete audit trail of the invisible side-channel review process

## v7.0 (Future)

Advanced capabilities and compliance:

- **RAG + confidence scoring**: Retrieval-augmented generation with automatic escalation to principal review when confidence falls below 90% certainty
- **A/B testing framework**: Systematic comparison of response variants to measure effectiveness across different contact types and conflict patterns
- **GDPR/CCPA privacy alignment documentation**: Formal documentation of data handling practices, retention policies, and user rights for regulatory compliance
- **Simulation/training interactive mode**: Interactive training environment where users can practice grey rock responses against simulated high-conflict scenarios
- **Anonymized research contribution pipeline**: Infrastructure for users to optionally contribute anonymized interaction patterns to improve the protocol's evidence base

## How to Influence the Roadmap

- **File an issue**: Describe the feature, its use case, and any supporting evidence
- **Propose via CONTRIBUTING.md**: Follow the contribution guidelines to submit proposals
- **Research contributions**: New evidence or citations may shift priorities -- well-sourced research suggestions are particularly valuable

---

*Roadmap priorities are subject to change based on community feedback and research developments.*
