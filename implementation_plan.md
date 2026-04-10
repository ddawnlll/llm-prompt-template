# Phase [N] — [Short Title] ([Status: Planned | In Progress | Complete])

**Status:** [Planned | In Progress | Complete]
**Owner:** [Team / track name]
**Last updated:** [YYYY-MM-DD]
**Delivery status:** [Not started | Partial implementation | Complete]

---

## 1. Purpose

[1–3 sentences describing why this phase exists and what problem it solves at a high level.]

[Optional: state what this phase is NOT — useful when scope is easily confused with adjacent work.]

---

## 2. What Carried Over / What Must Stay Stable

> Use this section to list prior work that must not regress, or existing contracts that must remain intact.

The following are already implemented / must remain stable:

- [x] [Completed item 1]
- [x] [Completed item 2]
- [x] [Completed item 3]

[Short note: "This phase builds on top of these. Do not regress them."]

---

## 3. What Was Wrong / Why a New Approach Is Needed

> Use this section only when a prior plan is being revised or replaced. Explain what the old approach was and why it is being withdrawn.

- [Old recommendation or approach]
- [Reason it is being withdrawn or changed]
- [What the correct approach is instead]

> If this is a brand new plan with no prior revision history, this section can be titled "Background & Motivation" and used to explain root cause analysis instead.

---

## 4. Current Failure State / Known Blockers

> List the concrete observable failures or blockers that this phase must resolve. Be specific — use field names, flags, metrics, error labels, etc.

The current state has the following known issues:

- `[field_or_flag]` = `[value]` — [explanation]
- `[field_or_flag]` = `[value]` — [explanation]
- [Qualitative blocker description]
- [Qualitative blocker description]

---

## 5. Workstream A — [Name]

**Status:** [New | In Progress | Blocked | Complete]

### Problem / Goal

[Describe the specific problem this workstream addresses, or the goal it achieves.]

### Root Cause (if applicable)

[Explain the underlying technical or process cause.]

### Implementation Tasks

- [ ] [Task 1]
- [ ] [Task 2]
- [ ] [Task 3]
- [ ] [Task 4]

### Configuration / Code Reference (if applicable)

```[language]
# Paste relevant config block, code snippet, or data structure here
```

### Acceptance Criteria

- [ ] [Measurable outcome 1]
- [ ] [Measurable outcome 2]
- [ ] [Measurable outcome 3]

---

## 6. Workstream B — [Name]

**Status:** [New | In Progress | Blocked | Complete]

### Problem / Goal

[Describe the specific problem this workstream addresses, or the goal it achieves.]

### Implementation Tasks

- [ ] [Task 1]
- [ ] [Task 2]
- [ ] [Task 3]

### Configuration / Code Reference (if applicable)

```[language]
# Paste relevant config block, code snippet, or data structure here
```

### Acceptance Criteria

- [ ] [Measurable outcome 1]
- [ ] [Measurable outcome 2]

---

## 7. Workstream C — [Name]

**Status:** [New | In Progress | Blocked | Complete]

### Problem / Goal

[Describe the specific problem or goal.]

### Sub-sections (if the workstream has multiple config areas)

#### 7.1 [Sub-area title]

```[language]
{
  "[key]": "[value]",
  "[key]": [value]
}
```

**Rationale:**
- `[key]`: [why this value was chosen]
- `[key]`: [why this value was chosen]

#### 7.2 [Sub-area title]

```[language]
{
  "[key]": "[value]"
}
```

### Acceptance Criteria

- [ ] [Measurable outcome 1]
- [ ] [Measurable outcome 2]

---

## 8. Workstream D — Test Coverage

**Status:** [New | In Progress | Complete]
**Required before:** [milestone, e.g. "next promotion attempt" or "next training run"]

### 8.1 [Test category — e.g. "Invariant tests"]

- [ ] [Invariant or regression test description]
- [ ] [Invariant or regression test description]
- [ ] [Invariant or regression test description]

### 8.2 [Test category — e.g. "Regression coverage"]

- [ ] [Test description]
- [ ] [Test description]

### 8.3 [Test category — e.g. "Output validation"]

- [ ] [Test description]
- [ ] [Test description]

---

## 9. Workstream E — Pre-Run / Pre-Deploy Audit Checklist

**Status:** [New | In Progress | Complete]
**Must complete before:** [training run | deployment | release]

### 9.1 [Audit area — e.g. "Runtime config audit"]

- [ ] [Manual check description]
- [ ] [Conditional: if X, do Y; if Z, do W]

### 9.2 [Audit area]

- [ ] [Manual check description]

### 9.3 [Audit area]

- [ ] [Manual check description]

---

## 10. Combined Implementation Order

> List the workstreams in the exact sequence they must be executed. Explain any dependencies.

1. Complete Workstream A — [name]
2. Implement Workstream B — [name]
3. Apply Workstream C — [name]
4. Run Workstream E — [pre-run audit]
5. Implement Workstream D — [test coverage]
6. Execute [first combined run / deployment]
7. Evaluate results against acceptance criteria

### Acceptance Criteria for First Combined Run

- [Metric or flag] = [expected value]
- [Metric or flag] > [threshold]
- [Qualitative condition]
- [Qualitative condition]

---

## 11. Definition of Done

> Phase N is complete when **all** of the following are true simultaneously. No partial credit.

### 11.1 [Layer — e.g. "Gate layer" or "Bootstrap layer"]

- [x] [Already done — locked item]
- [x] [Already done — locked item]
- [ ] [Outstanding item]
- [ ] [Outstanding item]

### 11.2 [Layer — e.g. "Model layer" or "Runtime / interface / V6"]

- [ ] [Outstanding item]
- [ ] [Outstanding item]
- [ ] [Outstanding item]

### 11.3 [Layer — e.g. "Candidate health" or "Platform coverage"]

- [ ] [Outstanding item]
- [ ] [Outstanding item]

### 11.4 [Layer — e.g. "Test layer" or "Testing"]

- [ ] [Outstanding item]
- [ ] [Outstanding item]

---

## 12. What Phase [N+1] Inherits

> Describe the starting point Phase N+1 will have. What capabilities or guarantees does completing this phase unlock?

### 12.1 [Capability expansion themes or inherited state]

- [Theme or guaranteed capability 1]
- [Theme or guaranteed capability 2]
- [Theme or guaranteed capability 3]

### 12.2 Phase Boundary

- Phase [N+1] is [capability expansion | infrastructure work | product work | etc.].
- Phase [N] is the prerequisite.
- Do not start Phase [N+1] work until Phase [N] definition of done is fully satisfied.

---

## 13. Compact Mental Model

> A brief, opinionated summary for quick orientation. Useful when onboarding someone new or returning after a gap.

### 13.1 Phase Relationships

- Phase [N-2]: [what it did — one line]
- Phase [N-1]: [what it did — one line]
- Phase [N]: [what it does — one line]
- Phase [N+1]: [what it will do — one line]

### 13.2 Key Takeaway

[1–3 sentences capturing the core insight or decision that defines this phase. Why were these choices made? What would happen if this phase were skipped or done wrong?]

---

<!--
SKELETON USAGE NOTES
=====================

REQUIRED SECTIONS (always include):
  1. Purpose
  2. What Carried Over / What Must Stay Stable
  4. Current Failure State / Known Blockers
  5–N. Workstreams (at least one; add or remove as needed)
  Combined Implementation Order
  Definition of Done

OPTIONAL SECTIONS (include when applicable):
  3. What Was Wrong — only for revised plans
  Pre-Run Audit checklist — for plans involving training runs or deployments
  Test Coverage workstream — for plans requiring new test infrastructure
  Compact Mental Model — highly recommended for plans with 5+ workstreams
  What Phase N+1 Inherits — recommended when a sequence of phases is in flight

WORKSTREAM STRUCTURE RULES:
  - Every workstream has: Status, Goal/Problem, Implementation Tasks, Acceptance Criteria
  - Config blocks and code references are optional but encouraged
  - Acceptance criteria must be checkboxes — never prose

DEFINITION OF DONE RULES:
  - Must be checkboxes only
  - Separate into layers (gate, model, test, platform, etc.)
  - Distinguish already-done items [x] from outstanding items [ ]
  - No partial credit — all boxes must be checked

STATUS VALUES:
  Plan status:        Planned | In Progress | Complete
  Workstream status:  New | In Progress | Blocked | Complete

NAMING CONVENTION:
  Workstreams: A, B, C, D, E, F, G (alphabetical, not by priority)
  Typically: A=core fix, B=model/infra, C=config, D=tests, E=pre-run audit
  Add F, G for platform or coverage workstreams
-->
