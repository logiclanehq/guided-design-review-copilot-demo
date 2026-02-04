## Sample Inputs - Execution Example

The following inputs were provided step by step in GitHub Copilot Chat
while executing the guided design review prompt.

---

Step 1 – Design Artifact Context
```text
Design artifact type: Software Design Document (SDD)
Design maturity: Review-ready draft
Intended audience: Enterprise Architecture Review Board and delivery team
```
---

Step 2 – System Overview
```text
The system is a cloud-native operational analytics platform that ingests batch data from multiple upstream business systems, processes and aggregates the data, and exposes curated datasets and metrics for reporting and analytics users.

The primary goal is to enable consistent, governed access to operational insights for business analysts and management teams.
```
---

Step 3 – Architectural Summary
```text
The architecture is layered and includes the following components:

- Presentation Layer: Reporting and analytics tools that consume curated datasets.
- API Layer: Secure access endpoints for querying processed data and metrics.
- Processing Layer: Batch validation, transformation, and aggregation logic.
- Data Layer: Persistent storage for operational records, aggregated metrics, and audit logs.
- Integration Layer: Handles inbound batch ingestion from upstream systems and outbound API interactions.
- Security Layer: Cross-cutting authentication, authorization (RBAC), and audit logging.

Upstream systems deliver data in batch to the Integration Layer, which triggers processing workflows. Processed data is stored in the Data Layer and accessed by downstream consumers via the API Layer.
```
---

Step 4 – Non-Functional Requirements
```text
Scalability:
The system must handle growth in data volume and number of reporting users.

Availability:
Target availability is 99.9% for data access and APIs.

Performance:
Batch processing must complete within defined processing windows to meet reporting SLAs.

Security:
Role-based access control is required for all user and system interactions.
Data must be encrypted at rest and in transit.

Compliance:
The design must align with internal enterprise security policies.
```
---

Step 5 – Constraints & Assumptions
```text
Constraints:
- The platform must use existing enterprise cloud standards.
- Budget constraints limit the use of always-on compute resources.

Assumptions:
- Upstream systems provide data in a consistent and agreed schema.
- Reporting tools will consume data through APIs rather than direct database access.

```
---

Step 6 – LLD Alignment
```text
Option A – If LLD exists

Low-level design details are partially available.

- APIs are defined per dataset with versioned endpoints.
- Processing workflows are modularized per data domain.
- Data schemas define partitioning and indexing strategies for analytics queries.

The intent is for LLD components to directly map to the architectural layers defined in the SDD.

Option B – If no LLD exists (very common)
No LLD provided.
