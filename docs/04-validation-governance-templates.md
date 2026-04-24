# Validation Governance Templates

## 1) 80% KPI Scorecard Template

| Capability | Weight | Target Threshold | Actual Score | Evidence Link | Owner | Status |
|---|---:|---:|---:|---|---|---|
| Functional coverage | 30 |  |  |  |  |  |
| Compliance/legal fit | 20 |  |  |  |  |  |
| Data migration readiness | 15 |  |  |  |  |  |
| Integration readiness | 10 |  |  |  |  |  |
| Security/audit readiness | 10 |  |  |  |  |  |
| Performance/reliability readiness | 10 |  |  |  |  |  |
| UAT/business acceptance | 5 |  |  |  |  |  |
| **Total** | **100** |  |  |  |  |  |

### Gate Rule
- Phase close allowed only when:
  - Weighted score >= 80
  - Critical legal/payroll gaps = 0

## 2) Traceability Matrix Template

| Capability ID | Epic/Story | Status | Test/UAT Evidence | Gap Severity | Owner | Release |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

## 3) Role-Based UAT Templates

### UAT Template (Common)
- UAT ID:
- Role:
- Scenario:
- Preconditions:
- Steps:
- Expected Result:
- Actual Result:
- Pass/Fail:
- Defect/Gap ID:
- Severity:
- Evidence Link:
- Tester:
- Date:

### Role Coverage Sets
- HR Admin
- Employee
- Manager
- Payroll Specialist
- Compliance

## 4) Gap Severity Model
- Critical: blocks phase completion or introduces legal/payroll non-compliance.
- High: major business impact; cannot be deferred without approval.
- Medium: manageable workaround; fix planned in release backlog.
- Low: minor issue; does not block acceptance.

## 5) Gate Policy
- Critical gaps block phase completion.
- Phase closes only when score >= 80 and critical legal/payroll gaps = 0.

## 6) Evidence Register Template

| Evidence ID | Type (Test/UAT/Audit/Report) | Linked Capability/Story | Owner | Link | Date | Verified By |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |
