# Runtime Conditions Profiles White Paper

**Milestone:** Audience, Goals, and Refining Scope  
**Initiative:** [CNCF TOC Issue #2285](https://github.com/cncf/toc/issues/2285)  

## The problem we are addressing

Runtime requirements are commonly scattered across various code artifacts (README files, SDKs, package files, etc), tickets, and conversations. The application team may know that a workload needs a cache, a relational database, an API, and a message bus. The platform team may know how to provide those capabilities in one environment. A gap exists between the two, in discovering the application's requirements consistently, in an automated way, to compare them with existing platform capabilities.

The paper should present Runtime Conditions Profiles as a common reference point between workload demand and platform fulfillment. It should not imply that a profile replaces service catalogs, deployment manifests, or any other platform tooling. Instead, it should explain how a profile can give existing platforms better input for fulfillment automation.

## Audience

#### Developers - anyone who codes

This includes application developers, AI-native application builders, and anyone who owns code that depends on databases, caches, APIs, message buses, model services, or other external runtime integrations.

The paper should answer questions such as:

- How do I describe what my application needs without learning every platform-specific provisioning mechanism?
- How can runtime requirements be discovered from code, SDKs, frameworks, or package metadata?
- What should I expect a generated Runtime Conditions Profile to contain?
- How can I review or validate that profile as part of normal development and CI?

The paper should respect the developer's goal: ship an application without turning every application team into an infrastructure implementation team.

#### Platform engineers

This includes platform engineers, internal developer platform builders, platform product owners, and anyone who wants to run code that depends on external tooling similar to the list above - databases, caches, APIs, etc.

The paper should answer questions such as:

- How can a platform receive a clear statement of workload demand before deployment?
- How can a profile be matched to capabilities offered by a particular environment?
- How can that workload demand be fulfilled differently in development, production, and regulated environments?
- How can policy, provisioning, and deployment automation consume the profile?

The paper should make the platform boundary explicit: the profile describes demand; the platform decides how that demand is fulfilled.

### Secondary audience

The paper may also serve:

- SDK and framework authors who can package metadata about the integrations their libraries expose.
- Service, API, and capability-catalog owners who publish the supply side of an integration.
- Security engineers who want documented integration requests for auditabilty and compliance checks.
- CNCF contributors and adjacent ecosystem projects evaluating how a demand-side artifact could complement their existing capabilities.

These readers should be given enough context to see where Runtime Conditions Profiles fit into the SDLC, without necessarily diving into their specific concerns.

## Goals

The white paper should:

1. **Explain the demand/fulfillment distinction.** Establish that a workload can declare the runtime capabilities and configuration inputs it requires without specifying a provider, solution, or cluster topology.

2. **Show how the model removes deployment friction.** Connect the profile to earlier dependency discovery, compatibility checks, and deployment automation.

3. **Give developers and platform engineers a shared mental model.** Use plain language and a memorable restaurant analogy, then connect that analogy to a small number of concrete technical examples.

4. **Make the workflow tangible.** Include a step-by-step flowchart and demos that show how signals from application code or SDK metadata can become a validated profile and then drive platform automation. Each demo should solve a real-world platform/deployment challenge, using CNCF projects where possible.

5. **Show environment-specific fulfillment.** Demonstrate that one workload's demand can be fulfilled by different implementations in different environments while the application-facing intent remains stable.

6. **Provide a practical starting point.** Help readers understand how to try the tooling, generate or inspect a profile, connect it to a platform workflow, and identify a small first use case.

7. **Explain how to participate.** Point readers to the GitHub org, open issues, discussions, and contribution paths, as well as demo suites so they can test solutions, propose extensions, improve tooling, or participate in identifying downstream use cases.

8. **Help organizations adopt the idea responsibly.** Provide guidance for introducing a demand-side artifact into CNCF and ecosystem projects without requiring an organization-wide rewrite.

9. **Position the work for community review.** Describe the problem and potential value clearly enough that CNCF contributors can validate the claims, identify gaps, and suggest improvements across adjacent projects and specifications.

## Scope

### In scope

- **Problem and model:** Explain Runtime Conditions Profiles as a portable, demand-side description of a workload's runtime integrations, and show how profiles connect application integration requirements with a platform's capability catalog.
- **Restaurant analogy:** Use the diner, concierge, restaurant, menu, and order to explain the relationship between an application, platform engineering, platform capabilities, and environment-specific fulfillment.
- **Deployment workflow:** Include at least one visual, step-by-step flow from code and/or SDK mappings to a generated profile, platform fulfillment, and deployment.
- **Representative examples and demos:** Use a small number of examples that highlight the use of CNCF projects to demonstrate platform automation - e.g. API matching in Backstage resulting in the generation of CiliumNetworkPolicies.
- **Getting started and organizational adoption:** Give readers a clear guide for onboarding and explain how teams can introduce the profile as a shared contract without replacing their existing systems.
- **Getting involved:** Point readers to the GitHub organization, issues, discussions, and demo suitesa as well as guidance for proposing extensions and identifying downstream use cases.

### Out of scope

- **Exhaustive coverage:** Listing an inventory of every integration, provider, SDK, cloud service, vendor, or extension.
- **Implementation prescription:** Going too deep into one platform architecture, deployment engine, catalog product, infrastructure provider, or fulfillment implementation.
- **Full technical reference:** Duplicating the complete specification, conformance requirements, extension-authoring guidance, or language-profiler documentation.
- **Roadmap and endorsement:** Defining a roadmap or imply CNCF endorsement of the current specification, implementation, or a single adoption path - things that should live in GitHub issues and discussions.