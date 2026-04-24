# Data Model + Migration/Reconciliation Specification

## 1) Canonical Entity Model

### Core HR
- Employee
- Position
- OrgUnit
- Employment

### Time
- TimeEntry
- LeaveRequest

### Payroll
- PayrollInput
- PayrollResult

### Benefits
- BenefitEnrollment

### Talent
- Candidate
- Application
- Goal
- PerformanceReview
- LearningRecord

## 2) Tenant-Aware Schema Standards
- `tenant_id` on all tenant-scoped entities.
- Tenant-scoped keys and constraints.
- Access control aligned to tenancy policy.
- Cross-tenant reads/writes are blocked by policy.

## 3) Required Audit/Compliance Fields
All regulated/critical entities include:
- `created_at`, `created_by`
- `updated_at`, `updated_by`
- `source_system`
- `version`
- Effective dating fields (as applicable)

Additional controls:
- Retention/archival policy by data class.
- Masking/legal hold controls for sensitive/legal data.

## 4) Entity-Level Specification Template
Use for each canonical entity:

- Entity Name:
- Owning Context:
- Tenant Scoped: Yes/No
- Primary Key:
- Business Key(s):
- Required Fields:
- Optional Fields:
- Effective-Dated: Yes/No
- PII/Sensitive Classification:
- Audit Fields Included: Yes/No
- Retention Class:
- Upstream Source(s):
- Downstream Consumer(s):

## 5) Migration Strategy

### 5.1 Source-to-Target Mapping Catalog
For each source system/table/field:
- Source object and field
- Target entity and field
- Transformation rules
- Validation rules
- Owner and sign-off

### 5.2 Migration Waves
- Wave sequencing aligned with dependency path:
  1. Foundation data setup
  2. Core HR baseline
  3. Time
  4. Payroll
  5. Extended modules
  6. Reporting projections/integration finalization

### 5.3 Staged Validation Checkpoints
- Pre-load validation (format, nullability, reference integrity)
- In-load validation (batch controls, reject handling)
- Post-load validation (counts, keys, business-rule conformance)
- UAT validation (business acceptance evidence)

## 6) Reconciliation Specification
- Define reconciliation rules per domain:
  - Record counts
  - Key totals/control totals
  - Business-rule variances
  - Exception categorization (critical/high/medium/low)
- Exception queue requirements:
  - Owner
  - SLA
  - Resolution status
  - Evidence link

## 7) Rollback Strategy (Per Migration Wave)
- Trigger conditions for rollback.
- Rollback scope and data restoration boundary.
- Decision owner and approval workflow.
- Evidence requirements for rollback execution and recovery.

## 8) Exit Criteria
- Mapping catalog complete and approved.
- Validation checkpoints passed for each migration wave.
- Reconciliation variances within agreed tolerance.
- Open critical reconciliation/compliance issues: 0.
