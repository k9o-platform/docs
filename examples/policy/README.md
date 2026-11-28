# Policy examples

One file per policy surface, each holding two YAML documents:

1. A **policy bundle**: named rules (`name`, `when`, `action` or `requires_approval_from`, optional `requires_proof`) and the `policy.<surface>` block that references them.
2. An **IAM policy**: the principal-bound ceiling, limited to `when` and `action: allow|deny`, and its `applications` block.

The ceiling is evaluated first. The bundle can only narrow it.

The guide at https://docs.kilimanjaro.dev/guides/unified-policy explains the model and links to every file here.

## Examples

### Data and storage

| Surface | Example | Summary |
|---|---|---|
| Collections | [`collections.yaml`](collections.yaml) | Row operations on a collection, bound custom actions and encrypted-column reveal. |
| Collection actions | [`collection_actions.yaml`](collection_actions.yaml) | Dispatch of a custom action bound to a collection. |
| Storage buckets | [`buckets.yaml`](buckets.yaml) | Object operations in a bucket (read, upload, delete, list) and the bucket lifecycle (create, update, remove). |
| Analytics datasets | [`datasets.yaml`](datasets.yaml) | Per-dataset access on the analytics query path. |
| Analytics queries | [`analytics.yaml`](analytics.yaml) | Queries against an analytics dataset. |
| Streams | [`streams.yaml`](streams.yaml) | Operations on a user-defined stream. |
| Raw SQL | [`raw_sql.yaml`](raw_sql.yaml) | Read-only raw SQL under the confined query role, and governed raw migrations. |
| Data export | [`data_export.yaml`](data_export.yaml) | The bulk data-portability export job. |
| Realtime | [`realtime.yaml`](realtime.yaml) | Subscribing to and replaying the realtime change feed. |

### Compute and AI

| Surface | Example | Summary |
|---|---|---|
| Functions | [`functions.yaml`](functions.yaml) | Function invocation and function lifecycle. |
| Workflows | [`workflows.yaml`](workflows.yaml) | Workflow authoring and runs. |
| Forms | [`forms.yaml`](forms.yaml) | Form authoring. |
| Event triggers | [`triggers.yaml`](triggers.yaml) | Event-trigger create, read, update and delete. |
| Job schedules | [`forge_schedules.yaml`](forge_schedules.yaml) | Scheduled-job authoring and manual runs. |
| Tools | [`tools.yaml`](tools.yaml) | Calls to a tool (MCP tool invocation), routed by name and classification. |
| LLM models | [`llms.yaml`](llms.yaml) | Direct model invocation and reading the model catalogue. |

### Secrets, keys and custody

| Surface | Example | Summary |
|---|---|---|
| Secrets | [`secrets.yaml`](secrets.yaml) | Creating a secret and revealing its value. A secret is addressed by its immutable id, never its path. |
| Application crypto | [`crypto.yaml`](crypto.yaml) | Encrypt, decrypt and rewrap through the API. |
| Project key (KEK) | [`kek.yaml`](kek.yaml) | Crypto-shredding the project key. One verb, no qualifier. |
| Custody mode | [`custody_mode.yaml`](custody_mode.yaml) | Starting a custody-mode transition. One verb, no qualifier. |
| Key-release policy | [`skr_policy.yaml`](skr_policy.yaml) | The project key-release trust anchor for confidential workloads. |
| Workload measurement policies | [`cwi_measurement_policies.yaml`](cwi_measurement_policies.yaml) | Measurement allowlists for confidential workload identities. |
| Trust-tier policy | [`trust_tier_policy.yaml`](trust_tier_policy.yaml) | The project trust-tier policy. |
| Erasure triggers | [`erasure_triggers.yaml`](erasure_triggers.yaml) | Configuration of erasure triggers. |

### Identity and access

| Surface | Example | Summary |
|---|---|---|
| Identity providers | [`auth_providers.yaml`](auth_providers.yaml) | Identity-provider configuration. |
| Sign-in flows | [`auth_flows.yaml`](auth_flows.yaml) | Sign-in flow authoring. |
| Project members | [`project_members.yaml`](project_members.yaml) | Membership and role grants. |
| Groups | [`groups.yaml`](groups.yaml) | Group management and membership. |
| API keys | [`api_keys.yaml`](api_keys.yaml) | Rotating the project API keys. |
| IAM policies | [`iam_policies.yaml`](iam_policies.yaml) | Creating, editing and widening IAM policies. |
| Policy bundles | [`policies.yaml`](policies.yaml) | The policy bundle lifecycle, including publish and rollback. |
| Delegated invocation | [`delegation.yaml`](delegation.yaml) | Acting on behalf of a named end user, or confined to one. |
| Magic-link redirects | [`magic_link_redirects.yaml`](magic_link_redirects.yaml) | The allowlist of magic-link redirect URLs. |
| Extension members | [`extension_members.yaml`](extension_members.yaml) | Extension-scoped member grants. |

### Project and platform administration

| Surface | Example | Summary |
|---|---|---|
| Project administration | [`project.yaml`](project.yaml) | Project delete, restore, update and residency-region changes. |
| Schema migrations | [`migrations.yaml`](migrations.yaml) | Reading, queueing, approving and running schema migrations. |
| Extensions | [`extensions.yaml`](extensions.yaml) | Extension lifecycle, configuration and invocation. |
| Audit log | [`audit_log.yaml`](audit_log.yaml) | Querying and exporting the project audit log. |
| Compliance bundle | [`compliance_bundle.yaml`](compliance_bundle.yaml) | Exporting the signed compliance-attestation bundle. |
| SIEM forwarding | [`siem.yaml`](siem.yaml) | SIEM webhook configuration. |
| Bring-your-own storage | [`byos.yaml`](byos.yaml) | Binding an organisation storage account to the project. |
| Gates | [`gates.yaml`](gates.yaml) | Creating a project-scoped gate token. One verb, no qualifier. |
| Views | [`views.yaml`](views.yaml) | View authoring. |
| Dashboards | [`dashboards.yaml`](dashboards.yaml) | Dashboard authoring. |
| Studio queries | [`studio_queries.yaml`](studio_queries.yaml) | Saved Studio (data explorer) query authoring. |
| Showroom | [`showroom.yaml`](showroom.yaml) | The demo-provisioning surface. |
