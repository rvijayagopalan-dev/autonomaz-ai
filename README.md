# AutonomaZ AI

AutonomaZ is an enterprise AI factory platform concept for turning enterprise knowledge, research and workflows into governed autonomous capabilities.

## Website demo

Open [`demo/autonomaz-website.html`](demo/autonomaz-website.html) in a browser. The standalone responsive demo includes:

- Public website: solutions, factory portfolio, case studies, guides and demos
- Client workspace: overview, factory catalog, instances, activity and workspace settings
- Provisioning request flow: select a factory blueprint, environment, region, access profile and data classification

## Important prototype note

The client workspace uses illustrative tenant data. Sign-in is not implemented and provisioning is simulated in the browser. No cloud infrastructure is created. Production use requires a secured backend, SSO/OIDC or SAML, MFA, tenant isolation, authorization, approvals, audited provisioning APIs and secrets management.

## Run locally

No build step or external dependencies are required. Open the HTML file directly in a modern browser, or serve the repository with any static web server.

## Product direction

The intended platform includes a public digital experience, multi-tenant client control plane, factory blueprint registry, provisioning orchestrator, isolated factory execution environments, governance and AgentOps.
