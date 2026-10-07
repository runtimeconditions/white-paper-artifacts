# Runtime Conditions Profiles: A Shared Contract Between Workloads and Platforms

**Milestone:** Outline
**Status:** Proposed outline for contributor discussion
**Initiative:** [CNCF TOC Issue #2285](https://github.com/cncf/toc/issues/2285)

## Outline

### 1. Introduction: the runtime requirements handoff

1.1 Runtime needs scattered across source, SDKs, and conversations
1.2 Non-standardized discovery, clunky onboarding, and deployment failures
1.3 Paper thesis: a portable demand profile indicates workload demands from platform capabilities

### 2. The model: demand before fulfillment

2.1 Workload demand: required integrations and configuration inputs
2.2 Platform fulfillment: environment-specific matching and delivery
2.3 Restaurant analogy: diner, concierge, restaurant, order
2.4 Boundary: profiles describe demand; platforms choose how to meet it

### 3. The profile as a shared contract

3.1 Compact example: checkout service with cache and datastore needs
3.2 Profile essentials: workload identity, conditions, interfaces, extensions
3.3 Validation: structure, added extension vocabulary
3.4 Portability and safety: no provider choice, target topology, or secret values

### 4. From workload signals to a validated profile

4.1 Sources: code declarations, SDK/framework metadata, package metadata
4.2 Generation and developer review
4.3 Local and CI validation; early diagnostics
4.4 Packaging and distribution, including OCI artifacts and Referrers API
4.5 Policy envforcement: policy-as-code tooling, admissions webhook

**Figure:** Workload signals → generator → profile → validation

### 5. From profile to platform fulfillment

5.1 Demand-to-capability matching
5.2 Catalogs, adapters, policy, and deployment workflows
5.3 Configuration binding and service delivery
5.4 Environment-specific choices: local development, production, regulated environments; defaults vs options
5.5 Early failure cases: unsupported capability, incompatible API, missing binding, policy violation

**Figure:** Profile → capability match → policy and fulfillment → deployment

### 6. Single-environment example: a workload that consumes an API

6.1 Declare the API requirement in generated profile
6.2 Publish and validate the profile (admissions webhook, Kyverno)
6.3 Match the requirement against an API catalog (Kratix -> Backstage/OpenAPI)
6.4 Set least-privilege policy (Kratix -> Kyverno, Cilium)
6.5 Bind the API endpoint and deploy (Helm chart, Backstage plugin)

**Figure:** Shows above steps happening in parallel

### 7. Multi-environment example: one profile, different fulfillments

7.1 Base scenario: single profile with multiple Condition demands (e.g. API, Postgres, Redis)  
7.2 Reuse the same generated demand profile in each environment  
7.3 Development: low-cost, self-managed Postgres and Redis  
7.4 Production: managed, high-availability datastore and cache  
7.5 Federal/banking: isolated, policy-approved services and restricted connectivity  
7.6 Platform-owned catalogs/adapters select implementations and provide environment-specific bindings

**Figure or table:** One profile’s demand alongside each environment’s fulfillment choices

### 8. AI workload example: vector search and model serving

8.1 RAG service profile: vector-search interface and model-inference API (OpenAI only if it is a true workload dependency)  
8.2 Development: local vector store and model-serving container; its separate profile declares CUDA compatibility, which the platform fulfills and connects to the RAG service  
8.3 Production: managed vector service and scalable model endpoint, selected and bound by the platform  
8.4 Regulated environment: isolated vector store and model serving on approved accelerators  
8.5 NVIDIA/CUDA constraints only when required by workload libraries; GPU SKU, provider, and placement remain platform choices

**Boundary:** Each profile describes one workload. Extension-defined accelerator requirements stay outside the core vocabulary; platform orchestration connects profiles and fulfills them per environment.

### 9. Benefits by audience

9.1 Developers: explicit needs, less platform-specific knowledge, earlier feedback
9.2 Platform engineers: clear demand, earlier compatibility checks, controlled fulfillment
9.3 Shared outcome: fewer bespoke handoffs; stable application intent across environments

### 10. Adoption and next steps

10.1 Start with one workload and one external dependency
10.2 Add profile generation and validation to an existing workflow
10.3 Connect one catalog or platform capability
10.4 Expand from evidence; keep existing systems and ownership boundaries

### 11. Boundaries and open questions

11.1 Discovery quality and generator limits
11.2 Vocabulary and interoperability, including AI and accelerator requirements
11.3 Platform-specific adapters and fulfillment responsibility
11.4 Community review questions; no roadmap or CNCF endorsement claims

### 12. Getting involved

12.1 Specification, tooling, and examples
12.2 Repository, issues, discussions, and demos
12.3 Contribution and review paths

### Appendices

A. Glossary
B. Select profile examples
C. References to the specification and adjacent projects
