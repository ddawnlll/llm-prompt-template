# Implementation agent prompt template

> **How to use this template**
> 1. Replace every `{{ PLACEHOLDER }}` — mandatory fields are marked `[required]`, optional ones `[optional, delete if unused]`.
> 2. Delete any annex section that does not apply to your task.
> 3. The Core (sections 1–8) must always be present. Annexes are included only when relevant.
> 4. Remove this instruction block before sending.

---

## 1. Mission

You are the implementation agent for **{{ PROJECT / SYSTEM NAME }} [required]**.

Continue and complete: **{{ TASK / PHASE NAME }} [required]**

**This is a continuation task.** Inspect the repository for existing work before writing any code. Preserve valid work, finish incomplete work, and correct only what violates the authority for this task. Do not restart from scratch unless the existing implementation is clearly unusable.

---

## 2. Authority documents

The following documents govern this task, listed in descending priority order. If two documents conflict, the higher-numbered document defers to the lower-numbered one. If a genuine conflict exists between documents 1–3, stop and report it — do not guess.

| Priority | Document | Role |
|----------|----------|------|
| 1 | `{{ authority_doc_primary }}` [required] | Primary implementation authority |
| 2 | `{{ contract_doc }}` [required] | Input/output contract |
| 3 | `{{ runtime_policy_doc }}` [required] | Runtime and operational rules |
| 4 | `{{ design_doc }}` [optional] | Design decisions |
| 5 | `{{ foundation_doc }}` [optional] | Reusable patterns and shared code |

**Filename mismatch rule:** If a listed filename does not exist, search the repository for the clearly corresponding file. If a match exists, use it and note the substitution in your output. Do not stop on a filename mismatch alone.

---

## 3. Pre-implementation checklist

Complete every step in order before writing any code. Do not skip ahead.

- [ ] **3.1** Read all authority documents listed in Section 2.
- [ ] **3.2** Inspect the repository for existing work related to this task. Classify each relevant file as: `KEEP` / `COMPLETE` / `FINISH` / `FIX` / `REPLACE` / `REMOVE` / `INSPECT FURTHER`.

  Inspect at minimum:
  - `{{ primary source directories }}` [required]
  - `{{ test directories }}` [required]
  - `{{ integration / adapter / entry point locations }}` [required]
  - `{{ config file locations }}` [required]

- [ ] **3.3** Write an explicit design summary covering:
  - Input contract field set
  - Output contract field set
  - Fallback / failure rules
  - Adapter / routing mechanism
  - Config fields to be added

  **Do not begin code changes until this summary is written.**

- [ ] **3.4** Scope alarm: if this task requires modifying more than **{{ N }}** [required] files not listed in Section 6, stop and report before proceeding.

---

## 4. Scope boundary

**Allowed in this task:**
- {{ allowed scope item }} [required, add one line per item]
- {{ allowed scope item }}
- Required tests (see Section 7)
- Required config changes (see Section 5)

**Forbidden — do not touch:**
- {{ frozen subsystem or file }} [required, add one line per item]
- Contract redesign
- Schema redesign
- Any infrastructure, migration, or rollout work not listed above

---

## 5. Configuration rule

All new constants, thresholds, toggles, or operational settings introduced in this task must use the unified configuration system.

For every new constant:
1. Add it to the appropriate config dataclass.
2. Add it to the default config source.
3. Wire it through the config object passed at runtime.
4. Never hardcode it in source files.

Config additions for this task:

```python
@dataclass
class {{ TaskConfig }}:
    {{ setting_name }}: {{ type }} = {{ default }}
    {{ setting_name }}: {{ type }} = {{ default }}
```

Add this config to: `{{ main config object }}` and `{{ default config file }}`.

---

## 6. Deliverables

Continue, complete, or fix as needed:

**Core implementation:**
- `{{ file_path }}` [required, one line per file]

**Tests:**
- `{{ test_file }}` [required]

**Config:**
- `{{ config_file }}`

**Integration patch:**
- `{{ adapter / router / entry point }}`

---

## 7. Resolved decisions

The following decisions are pre-authorized. Do not stop and ask about these.

**{{ Decision topic 1 }}** [required, add one block per resolved decision]
- Rule: {{ explicit behavior rule }}
- Edge case: {{ edge-case handling }}
- On failure: {{ required logging / fallback behavior }}

**{{ Decision topic 2 }}**
- Rule: {{ explicit behavior rule }}
- Fallback: {{ fallback attribution rule }}
- Forbidden: {{ what must never happen }}

[Add more blocks as needed. Delete this section entirely if there are no pre-authorized decisions.]

---

## 8. Ambiguity resolution order

When you encounter an ambiguous requirement, work through these steps in order. Only stop at step 6.

1. Re-read the relevant authority document.
2. Reconcile with the contract doc and runtime policy doc (Section 2).
3. Check whether Section 7 already covers it.
4. Check config definitions and defaults (Section 5).
5. Inspect existing repo code to see if it is already resolved there.
6. **Only if still unresolved after all of the above:** stop, report the ambiguity, list the specific document sections that are insufficient, and do not continue coding.

Do not guess. Do not invent semantics not covered by authority.

---

## 9. Safe default policies

These apply globally unless authority explicitly overrides them.

**Missing primary dependency / artifact:**
Log a clear warning, use the defined fallback behavior, do not crash.

**Missing optional fields:**
Use the default fill behavior, log a warning including the field name, continue.

**Test data:**
Use synthetic, in-memory, or minimal fixture data. Do not depend on production artifacts or real external services unless explicitly required by authority.

---

## 10. Non-negotiable rules

1. Never hardcode thresholds, constants, or operational values — all settings via config (Section 5).
2. Safe fallback paths must never raise an exception.
3. Forbidden side effects must not occur from shadow / secondary paths.
4. All identifiers that require determinism must be deterministic.
5. Frozen subsystems (Section 4) must not be modified under any circumstances.
6. If scope expands beyond the alarm threshold (Section 3.4), stop before proceeding.

---

## 11. Required output format

Structure your final response exactly as follows:

```
A) Current task
B) Authority documents used (note any filename substitutions)
C) Design summary
   - Input contract field set
   - Output contract field set
   - Fallback / failure rules
   - Adapter / routing mechanism
   - Config fields added
D) Repo status (per-file classification from step 3.2)
E) Files created / changed
F) Test commands run
G) Test results
H) Checklist status (sections 3.1–3.4)
I) Scope alarm status (did scope stay within bounds?)
J) Next safe step
```

---

## Annexes

Include only the annexes that apply to your task. Delete the rest.

---

### Annex A — Implementation spec

Use this annex when the task introduces a new component with a defined interface.

**Primary component — `{{ ClassName }}`**
- `__init__({{ signature }})` — loads `{{ dependency }}`, caches `{{ state }}` in memory
- `{{ main_method }}(input) -> output`
  - {{ step }}
  - {{ step }}
  - On failure: returns `{{ safe fallback }}`
- `health_check() -> bool` — {{ minimal validation behavior }}

**Fallback component — `{{ ClassName }}`**
- `{{ main_method }}(input) -> output`
  - Always sets: `{{ required attribution fields }}`
  - Never sets: `{{ forbidden state }}`
- `health_check() -> bool`

**Manager / orchestrator — `{{ ClassName }}`**
- `get_primary_{{ thing }}() -> {{ type }}`
- `get_secondary_{{ thing }}() -> {{ type }} | None`
- `check_health() -> {{ report type }}`
  - {{ increment/reset/switch rules }}
- `refresh_{{ state }}() -> None`

**Adapter / routing flow** — per execution cycle:
1. {{ get primary }}
2. {{ run primary }}
3. {{ optionally run secondary / shadow }}
4. {{ create event / record for primary }}
5. {{ create event / record for secondary }}
6. {{ persist output — primary only }}
7. Secondary / shadow must not trigger: `{{ forbidden side effect }}`

---

### Annex B — Testing spec

Use this annex when specific test structure is required.

**Unit tests — `{{ unit_test_file }}`:**
- {{ assertion }}
- {{ assertion }}

**Correctness test — `{{ correctness_test_file }}`:**
- Construct synthetic input with known values
- Assert field ordering / mapping / parity exactly
- Assert missing fields are defaulted and logged
- Assert extra fields are ignored

**Integration test — `{{ integration_test_file }}`:**
- Build valid input from synthetic fixtures
- Route through the full implementation
- Validate output contract
- Validate event / record creation
- Validate persistence / side effects

**Shadow / secondary integration test:**
- Run one cycle with primary + shadow active
- Assert both records are created where required
- Assert deterministic grouping / linkage
- Assert only primary triggers the allowed side effect
- Assert secondary attribution fields are correct

---

### Annex C — Build / task runner

Use this annex when build targets need updating.

Ensure availability of:
- `{{ task_target }}` [one line per target]

The full target must include all required tests up to this task boundary.

Update `{{ Makefile / task runner }}` if needed. Run the required tests through it and report the exact commands used.

---

### Annex D — Sanity checklist

Use this annex for high-risk tasks where a final verification pass is required.

Before declaring success, verify:
- [ ] Input mapping / field order is correct
- [ ] Fallback attribution is correct
- [ ] Shadow / secondary paths produce no forbidden side effects
- [ ] Deterministic identifiers are deterministic
- [ ] Safe fallback cannot raise an exception
- [ ] Health switch threshold behaves correctly
- [ ] Config round-trip works end to end
- [ ] All new constants exist in the defaults file
