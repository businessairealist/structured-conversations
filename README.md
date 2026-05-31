# Structured Conversations Plugin

Transform rough goals, notes, evidence, and prior work into guided conversations, maps, vision drafts, specifications, delivery plans, quality reports, and strategy plans.

## Install

1. Open Claude Desktop
2. Open the plugin file `structured-conversations.plugin`
3. Review the plugin contents and click **Accept**

The plugin's 95 skills will appear in your skill list immediately.

## Structure

```
structured-conversations/
├── .claude-plugin/plugin.json     # Plugin manifest (v3.0.3)
├── skills/                        # 95 skills with references
├── docs/architecture.md           # Architecture documentation
├── README.md
├── CHANGELOG.md
├── SECURITY.md
└── CONTRIBUTING.md
```

## Skills by Domain

### Foundation (5 skills)

| Skill | Purpose |
|-------|---------|
| structured-conversation-facilitator | Turn vague topics into structured conversation plans |
| mapping-technique-selector | Choose the right mapping technique for a problem |
| syntax-pattern-selector | Select the right syntax pattern for requirements |
| verb-noun-rewriter | Rewrite vague language into precise verb-noun actions |
| shared-contracts | Guidance on artifact conventions, naming, lifecycle, and quality gates |

### Mapping & Discovery (25 skills)

| Skill | Purpose |
|-------|---------|
| empathy-map-builder | Build empathy maps from customer evidence |
| empathy-map-facilitator | Facilitate empathy mapping workshops |
| empathy-map-template-generator | Generate blank empathy map templates |
| empathy-insight-extractor | Extract insights from empathy maps |
| empathy-to-action-translator | Convert empathy insights into actions |
| impact-map-builder | Build impact maps connecting goals to deliverables |
| impact-map-facilitator | Facilitate impact mapping workshops |
| impact-to-story-translator | Convert impact map nodes to user stories |
| customer-journey-map-builder | Build customer journey maps |
| customer-journey-map-facilitator | Facilitate journey mapping workshops |
| journey-friction-analyzer | Analyze friction points in journey maps |
| journey-map-template-generator | Generate blank journey map templates |
| journey-to-priority-translator | Prioritize from journey insights |
| user-story-map-builder | Build user story maps |
| user-story-map-facilitator | Facilitate story mapping workshops |
| story-map-template-generator | Generate blank story map templates |
| value-stream-map-builder | Build value stream maps |
| value-stream-map-facilitator | Facilitate value stream mapping |
| value-stream-optimization-prioritizer | Prioritize value stream improvements |
| opportunity-solution-tree-builder | Build opportunity-solution trees |
| flow-efficiency-calculator | Calculate flow efficiency metrics |
| process-waste-classifier | Classify process waste types |
| gist-planner | GIST planning (Goals, Ideas, Steps, Tasks) |
| edge-case-question-miner | Mine edge cases from maps and evidence |
| visual-rendering-guide | Visual rendering guidance for all artifact types |

### Vision & Messaging (12 skills)

| Skill | Purpose |
|-------|---------|
| product-elevator-pitch-writer | Write product elevator pitches |
| product-elevator-pitch-facilitator | Facilitate pitch workshops |
| elevator-pitch-template-generator | Generate blank pitch templates |
| elevator-pitch-to-epic-translator | Convert pitches to epics |
| future-press-release-writer | Write working-backwards press releases |
| future-press-release-facilitator | Facilitate press release workshops |
| future-press-release-template-generator | Generate press release templates |
| press-release-structure-selector | Choose press release structure |
| persona-pitch-adapter | Adapt pitches for different audiences |
| pitch-comparison-matrix-builder | Compare pitch alternatives |
| working-backwards-section-scaffolder | Scaffold working-backwards sections |
| customer-needs-outcome-aligner | Align customer needs to outcomes |

### Specification (16 skills)

| Skill | Purpose |
|-------|---------|
| example-map-builder | Build example maps from stories |
| example-map-facilitator | Facilitate example mapping workshops |
| example-map-template-generator | Generate blank example map templates |
| feature-map-builder | Build feature maps |
| feature-map-facilitator | Facilitate feature mapping workshops |
| feature-map-template-generator | Generate feature map templates |
| feature-rule-example-scaffolder | Scaffold feature rules and examples |
| rule-example-question-scaffolder | Build rules/examples/questions tables |
| gherkin-scenario-writer | Write Gherkin scenarios from stories |
| living-documentation-builder | Build living documentation from specs |
| acceptance-criteria-scaffolder | Scaffold acceptance criteria |
| epic-hypothesis-statement-scaffolder | Scaffold epic hypothesis statements |
| epic-hypothesis-template-generator | Generate epic hypothesis templates |
| epic-outcome-indicator-framer | Frame outcome indicators for epics |
| outcome-driven-epic-writer | Write outcome-driven epics |
| data-driven-decision-framer | Frame data-driven decisions |

### Delivery (20 skills)

| Skill | Purpose |
|-------|---------|
| user-story-drafter | Draft user stories in the right syntax |
| user-story-format-selector | Choose story format |
| user-story-format-template-generator | Generate story format templates |
| user-story-splitter | Split stories into smaller pieces |
| story-splitting-method-selector | Choose splitting method |
| story-split-decision-tree-guide | Decision tree for splitting |
| spidr-slice-generator | SPIDR story slicing |
| hamburger-slice-scaffolder | Hamburger method slicing |
| story-hierarchy-organizer | Organize story hierarchies |
| story-subtask-planner | Break stories into subtasks |
| subtasking-workshop-facilitator | Facilitate subtasking workshops |
| subtasking-template-generator | Generate subtasking templates |
| sequence-diagram-subtask-scaffolder | Subtasks from sequence diagrams |
| code-review-to-subtask-translator | Convert code review findings to subtasks |
| story-syntax-comparison-matrix-builder | Compare story syntax options |
| invest-readiness-checker | Check stories against INVEST criteria |
| spike-writer | Write technical spikes |
| release-slice-planner | Plan release slices from maps |
| solution-experiment-designer | Design solution experiments |
| observation-to-hypothesis-translator | Convert observations to hypotheses |

### Quality (7 skills)

| Skill | Purpose |
|-------|---------|
| defect-context-capture-scaffolder | Scaffold defect context capture |
| defect-reproduction-scaffolder | Scaffold reproduction steps |
| defect-report-writer | Write defect reports |
| defect-report-template-generator | Generate defect report templates |
| severity-priority-classifier | Classify severity and priority |

### Strategy (10 skills)

| Skill | Purpose |
|-------|---------|
| goal-oriented-roadmap-builder | Build goal-oriented roadmaps |
| goal-oriented-roadmap-template-generator | Generate roadmap templates |
| now-next-later-roadmap-scaffolder | Build Now/Next/Later roadmaps |
| outcome-initiative-horizon-planner | Horizon planning |
| objective-keyresult-initiative-scaffolder | OKR scaffolding |
| okr-level-cascade-builder | OKR cascades across levels |
| okr-mapping-template-generator | Generate OKR mapping templates |
| okri-builder | OKRi (OKR + Initiatives) builder |
| initiative-to-keyresult-aligner | Align initiatives to key results |
| hypothesis-experiment-designer | Design hypothesis experiments |
| hypothesis-tree-template-generator | Generate hypothesis tree templates |
| experiment-signal-passfail-designer | Design experiment pass/fail signals |

## Usage

Skills trigger automatically when you describe what you want to do:

- "Build an empathy map from these customer interview notes"
- "Help me write a user story for the checkout flow"
- "I need a roadmap for Q3 — start from our OKRs"
- "Turn this vague idea into a structured conversation"
- "Write Gherkin scenarios for the login feature"
- "What mapping technique should I use for this problem?"
- "Split this story — it's too big for one sprint"

## Version

See [CHANGELOG.md](CHANGELOG.md) for version history.
