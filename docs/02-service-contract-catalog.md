# Service/API/Event Contract Catalog

## Purpose
Define bounded contexts, ownership, source-of-truth entities, write ownership, read rules, and integration contracts.

## Bounded Contexts
- Core HR (PA/OM)
- Time
- Payroll
- Benefits
- Talent (Recruitment + Performance/Learning)
- ESS/MSS
- Reporting/Integration

## Contract Policy
- API/event contracts are versioned using semantic versioning.
- Backward compatibility is required for minor changes.
- Breaking changes require a major version and deprecation window.
- Cross-context access is allowed only via APIs/events.
- Shared reference data is managed via MDM patterns.

---

## Context Catalog

### 1) Core HR (PA/OM)
- Owner: Core HR Domain Team
- Source-of-truth entities: Employee, Employment, Position, OrgUnit
- Write ownership: Core HR only
- Read rules: Other contexts consume via APIs/events
- Primary APIs:
  - Employee lifecycle
  - Position/Org assignment
  - Employment status/effective dating
- Primary events:
  - EmployeeCreated.v1
  - EmployeeUpdated.v1
  - EmploymentStatusChanged.v1
  - PositionAssigned.v1

### 2) Time
- Owner: Time Domain Team
- Source-of-truth entities: TimeEntry, LeaveRequest, LeaveBalance
- Write ownership: Time only
- Read rules: Payroll, Reporting consume via APIs/events
- Primary APIs:
  - Time capture and validation
  - Leave request lifecycle
  - Time summary retrieval
- Primary events:
  - TimeEntrySubmitted.v1
  - TimeEntryApproved.v1
  - LeaveRequested.v1
  - LeaveApproved.v1

### 3) Payroll
- Owner: Payroll Domain Team
- Source-of-truth entities: PayrollInput, PayrollResult, StatutoryOutput
- Write ownership: Payroll only
- Read rules: Reporting and Compliance consume via APIs/events
- Primary APIs:
  - Payroll run orchestration
  - Adjustment/recalculation
  - Payroll result retrieval
- Primary events:
  - PayrollRunStarted.v1
  - PayrollRunCompleted.v1
  - PayrollVarianceDetected.v1
  - StatutoryOutputGenerated.v1

### 4) Benefits
- Owner: Benefits Domain Team
- Source-of-truth entities: BenefitPlan, BenefitEnrollment
- Write ownership: Benefits only
- Read rules: Core HR and Reporting consume read-only interfaces
- Primary APIs:
  - Enrollment lifecycle
  - Plan eligibility checks
  - Coverage change processing
- Primary events:
  - BenefitEnrolled.v1
  - BenefitChanged.v1
  - BenefitTerminated.v1

### 5) Talent (Recruitment + Performance/Learning)
- Owner: Talent Domain Team
- Source-of-truth entities: Candidate, Application, Goal, PerformanceReview, LearningRecord
- Write ownership: Talent only
- Read rules: Core HR consumes selected outcomes via APIs/events
- Primary APIs:
  - Candidate/application lifecycle
  - Review cycles and outcomes
  - Learning assignment/completion
- Primary events:
  - CandidateCreated.v1
  - ApplicationStatusChanged.v1
  - PerformanceReviewCompleted.v1
  - LearningCompleted.v1

### 6) ESS/MSS
- Owner: Experience Domain Team
- Source-of-truth entities: RequestEnvelope, ApprovalAction (interaction layer records)
- Write ownership: ESS/MSS for request metadata; domain writes delegated to owning contexts
- Read rules: Reads aggregate from domain APIs, no direct table coupling
- Primary APIs:
  - Profile/read models
  - Request submission and tracking
  - Approval action endpoints
- Primary events:
  - RequestSubmitted.v1
  - ApprovalActionTaken.v1
  - RequestRouted.v1

### 7) Reporting/Integration
- Owner: Integration & Analytics Team
- Source-of-truth entities: Curated analytic views, integration run logs
- Write ownership: Reporting/Integration for projections only
- Read rules: Consumes domain events/APIs, no upstream writes
- Primary APIs:
  - Report generation and export
  - Integration status and reconciliation
  - Analytics dataset access
- Primary events:
  - ReportGenerated.v1
  - IntegrationSyncCompleted.v1
  - IntegrationSyncFailed.v1

---

## Contract Catalog Template
Use this template per API/event contract:

- Contract Name:
- Context Owner:
- Type: API | Event
- Version:
- Producers:
- Consumers:
- Input/Output Summary:
- Validation Rules:
- Error Model:
- Compatibility Notes:
- Deprecation Policy:
- Evidence Link:
