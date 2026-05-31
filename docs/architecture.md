# Plugin Architecture

## Structure

```
structured-conversations/
├── .claude-plugin/
│   └── plugin.json              # Plugin identity and metadata
├── skills/                      # 95 skill directories
│   └── <skill-name>/
│       ├── SKILL.md             # Trigger description + instructions for Claude
│       └── references/          # Deep domain docs (loaded on demand)
│           └── *.md
├── docs/
│   └── architecture.md          # This file
├── README.md                    # Install, usage, skill index
├── CHANGELOG.md                 # Version history
├── SECURITY.md                  # Security posture
└── CONTRIBUTING.md              # Contribution guidelines
```

## Design Principles

### Skills-Only Architecture
All functionality is delivered through skills. There are no commands, hooks, agents, MCP servers, or executable scripts. This keeps the plugin simple, portable, and auditable.

### Progressive Disclosure
Each skill has two layers:
1. **SKILL.md** (always loaded when triggered): lean instructions under 3000 words
2. **references/** (loaded on demand): detailed domain docs, schemas, guides, rubrics

Claude reads the SKILL.md first. If deeper knowledge is needed, it reads from references/.

### Standardized Skill Structure
Every SKILL.md follows the same section pattern:
1. **Frontmatter** — name, description with trigger phrases
2. **Purpose** — what the skill does (1-2 paragraphs)
3. **Find Inputs Before Asking** — check for existing material before prompting user
4. **Core Workflow** — the skill-specific process steps
5. **Write Outputs** — what to produce and where to save it
6. **Quality Bar** — standards the output must meet
7. **User Experience Contract** — how to interact with the user

### Domain Organization
Skills span seven domains:
- **Foundation** — conversation facilitation, syntax selection, mapping technique selection
- **Mapping & Discovery** — empathy maps, impact maps, journey maps, value stream maps, story maps
- **Vision & Messaging** — elevator pitches, press releases, working-backwards artifacts
- **Specification** — example maps, feature maps, Gherkin scenarios, acceptance criteria, epics
- **Delivery** — user stories, story splitting, subtask planning, release slicing
- **Quality** — defect capture, reproduction, severity classification
- **Strategy** — roadmaps, OKRs, hypothesis trees, experiments

### Artifact Chaining
Skills are designed to feed into each other. For example:
- Empathy map → Impact map → User stories → Gherkin scenarios
- Observation → Hypothesis → Experiment → Decision

Each skill checks for existing outputs from upstream skills before asking the user for raw inputs.
