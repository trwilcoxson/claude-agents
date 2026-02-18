# Claude Code Agents

Custom agents for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) that provide specialized, reusable capabilities for security assessment, code review, and quality analysis.

## Security Assessment Suite

A pipeline of specialized agents for comprehensive security assessments, orchestrated by the [threat-model skill](https://github.com/trwilcoxson/claude-skills). See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for the full design document.

The parent conversation reads the skill's orchestration guide and spawns all agents as flat peers — no nesting. Solo mode runs the threat model + report generation. Team mode adds privacy, compliance, code review, and validation agents in parallel.

### `security-architect` — Threat Modeling Specialist

Performs architectural security assessments using the [threat-model skill](https://github.com/trwilcoxson/claude-skills). Executes the 8-phase threat model analysis and writes structured phase outputs.

**Capabilities:**
- 8-phase structured threat modeling (STRIDE-LM, PASTA, OWASP Risk Rating)
- Cloud security (AWS, GCP, Azure), container, serverless, and API security expertise
- Mermaid data flow diagrams with 4-layer structural + risk overlay approach

**Dependencies:** [threat-model skill](https://github.com/trwilcoxson/claude-skills)

### `report-analyst` — QA & Multi-Format Report Generator

Quality assurance reviewer and report consolidator. Validates deliverable accuracy, consistency, and completeness, then generates integrated reports in four formats.

**Capabilities:**
- Cross-document validation (finding counts, severity ratings, framework IDs, terminology)
- Consolidated report generation from 8 threat model phases + optional team outputs
- Four output formats: HTML (interactive, Mermaid diagrams with zoom/fullscreen), Word (.docx), PDF, and Executive PPTX
- Mermaid diagram rendering to PNG for print formats
- Deterministic output structure via report template
- Post-generation validation checklist

**Dependencies:** [docx, pdf, pptx, frontend-design skills](https://github.com/anthropics/claude-code)

### `code-review-agent` — Threat-Model-Aware Code Security Review

Performs deep code-level vulnerability analysis prioritized by the security-architect's threat model findings. Team-integrated with STRIDE-LM-directed review focus.

**Capabilities:**
- CVSS v3.1 scoring with vector strings
- Threat-model-aware prioritization (focuses on components flagged by architecture review)
- Code evidence for every finding
- CWE and MITRE ATT&CK mapping

### `privacy-agent` — Privacy Impact Assessment

Privacy professional for GDPR, CCPA/CPRA, HIPAA, and global privacy regulation analysis.

**Capabilities:**
- Data flow mapping and personal data inventory
- LINDDUN threat analysis
- Privacy impact assessments (DPIA/PIA)
- Regulatory compliance evaluation
- Privacy-by-design recommendations

### `grc-agent` — Governance, Risk & Compliance

Compliance gap analysis across major frameworks.

**Capabilities:**
- SOC 2, ISO 27001, NIST CSF/800-53, PCI-DSS, HIPAA, FedRAMP, CMMC coverage
- Cross-framework control mapping
- Gap analysis with remediation roadmaps
- Control matrix generation (.xlsx)
- Audit readiness assessment

### `security-reviewer` — Standalone Code Security Review

Reviews code for security vulnerabilities, misconfigurations, and insecure design patterns. Standalone (not team-integrated) — use for quick security checks.

**Capabilities:**
- Authentication, authorization, input validation, cryptography review
- API security and infrastructure config analysis
- OWASP Top 10 coverage
- Secure design pattern validation

## Code Quality

### `code-quality-reviewer` — Expert Code Quality Reviewer

Performs thorough, actionable code quality reviews across 9 dimensions: readability, documentation, maintainability, architecture, error handling, modern practices, testability, security, and performance.

**Features:**
- Systematic review methodology with prioritized findings (Critical / Important / Suggestions)
- For Python projects, automatically invokes the `/python-quality` skill for automated analysis
- Language/framework agnostic
- Actionable feedback with concrete code examples

**When it activates:**
- After implementing new features or refactoring code
- When explicitly asked to review code
- Before merging pull requests

## Installation

Copy any agent's `.md` file to your Claude Code agents directory:

```bash
# Global (available in all projects)
cp agents/security-architect/security-architect.md ~/.claude/agents/security-architect.md

# Project-specific
cp agents/security-architect/security-architect.md .claude/agents/security-architect.md
```

For the full security assessment suite, install all security agents:

```bash
for agent in security-architect report-analyst code-review-agent grc-agent privacy-agent validation-specialist security-reviewer; do
  cp agents/$agent/$agent.md ~/.claude/agents/$agent.md
done
```

**Note:** The security-architect agent requires the [threat-model skill](https://github.com/trwilcoxson/claude-skills). The report-analyst requires the docx, pdf, pptx, and frontend-design skills. The validation-specialist has no built-in agent type — it is spawned as `general-purpose` by the parent conversation.

## Structure

```
agents/
  security-architect/
    security-architect.md       # Threat modeling specialist (8-phase analysis)
    skills/threat-model/        # Methodology, orchestration, and 11 reference files
  report-analyst/
    report-analyst.md           # QA & multi-format report generation
  code-review-agent/
    code-review-agent.md        # Threat-model-aware code security review
  grc-agent/
    grc-agent.md                # Governance, risk & compliance
  privacy-agent/
    privacy-agent.md            # Privacy impact assessment
  validation-specialist/
    validation-specialist.md    # Cross-agent validation (spawned as general-purpose)
  security-reviewer/
    security-reviewer.md        # Standalone code security review
  code-quality-reviewer/
    code-quality-reviewer.md    # Code quality review
docs/
  ARCHITECTURE.md               # Full system architecture design document
```

## License

MIT
