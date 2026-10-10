# OpsDesk

**A collaborative operations workspace for modern DevOps teams.**

OpsDesk is an open-source, self-hostable productivity platform designed to simplify everyday DevOps workflows.

It brings together service information, deployment activity, incident management, operational tasks, and team documentation in a single workspace.

Instead of switching between multiple dashboards, issue trackers, CI/CD tools, and chat applications to understand what's happening, OpsDesk provides a unified operational view.

## Why OpsDesk?

Modern DevOps teams often rely on a collection of specialized tools:

- GitHub or GitLab for source control and CI/CD
- Grafana and Prometheus for monitoring
- Jira or similar applications for task management
- Slack or Microsoft Teams for communication
- PagerDuty or equivalent systems for incident response
- Wikis and repositories for operational documentation

These tools work well individually, but important operational context becomes fragmented across them.

OpsDesk is designed to connect these systems rather than replace them.

**One workspace. Existing tools. Less administrative overhead.**

## Core Features

### Unified Operations Dashboard

See the most important information about your systems and operational workload in one place.

- Active incidents and outstanding alerts
- Recent and upcoming deployments
- Service health and ownership
- Pending operational tasks
- Recent changes across environments

### Service Catalog

Maintain a centralized directory of services and infrastructure components.

Each service can include:

- Ownership and contact information
- Source repositories
- Production and staging environments
- Monitoring dashboards
- Deployment pipelines
- Operational runbooks
- Dependencies on other services

### Deployment Management

Understand what changed, when it changed, and who initiated the change.

- Track deployments across environments
- Link releases to commits and pull requests
- Review deployment histories
- Identify failed or incomplete deployments
- Correlate changes with incidents

### Incident Coordination

Provide a shared workspace for investigating and resolving operational incidents.

- Create and categorize incidents
- Assign incident owners
- Record investigation notes
- Maintain incident timelines
- Document resolutions
- Track follow-up actions

### Runbooks and Documentation

Keep operational knowledge accessible without requiring engineers to maintain duplicate documentation.

- Index Markdown documentation stored in Git
- Search troubleshooting procedures
- Associate runbooks with services and incidents
- Link directly to authoritative documentation
- Maintain revision history through existing repositories

### Team Productivity

Support everyday collaboration without turning operations into unnecessary paperwork.

- Shared operational task boards
- Task ownership and priorities
- Shift handoff summaries
- Daily activity views
- Links between incidents, deployments, and tasks

## Integrations

OpsDesk is intended to support integrations with existing development and operations infrastructure.

| Category | Planned Integrations |
|---|---|
| Source Control | GitHub, GitLab |
| CI/CD | GitHub Actions, GitLab CI, Jenkins |
| Monitoring | Grafana, Prometheus |
| Incident Response | PagerDuty, Opsgenie |
| Project Management | Jira, Linear |
| Communication | Slack, Microsoft Teams |
| Authentication | OpenID Connect, OAuth 2.0 |

Integrations should use existing APIs and webhooks whenever practical.

OpsDesk should avoid creating unnecessary copies of data maintained by other systems.

## Example Workflow

**Scenario: A production deployment introduces a service regression.**

1. A deployment event arrives from the connected CI/CD system.
2. OpsDesk records the deployment against its associated service and environment.
3. An alert from the monitoring system identifies elevated error rates.
4. An engineer opens an incident and links it to the affected service.
5. The incident workspace displays relevant deployments, dashboards, and runbooks.
6. The team investigates and performs a rollback using its established deployment tooling.
7. The incident timeline records the resolution.
8. Follow-up work is assigned to the appropriate team members.

The complete operational context remains accessible from the service's workspace.

## Design Principles

### Integrate, Don't Replace

OpsDesk should complement existing operational infrastructure rather than becoming yet another mandatory system of record.

### Read-Only by Default

Integrations should begin with read-only access. Actions that modify infrastructure or external systems must require explicit authorization.

### Humans Remain in Control

Operational decisions, production changes, and incident escalation remain the responsibility of engineers.

### Minimal Configuration

A small team should be able to deploy OpsDesk without an extensive infrastructure project.

### Self-Hosting First

Support deployment on infrastructure controlled by the organization, without requiring a proprietary cloud service.

### Transparency

Operational information should be traceable to its source. Deployment events, incident timelines, and administrative actions should maintain appropriate audit records.

## Proposed Architecture

The initial architecture is intentionally conventional:

- **Frontend:** React with TypeScript
- **Backend:** REST API
- **Database:** PostgreSQL
- **Background Processing:** Worker service for integration events and synchronization
- **Authentication:** OpenID Connect
- **Deployment:** Docker Compose initially, with Kubernetes support considered later

The application would consist of a web interface, API service, background worker, and database.

External integrations would communicate through authenticated APIs and webhooks.

## Deployment

The intended initial deployment method is Docker Compose.

Configuration should use environment variables for database connections, authentication settings, public URLs, and integration credentials.

Installation commands and a working Compose configuration will be documented when the initial implementation is available.

## Security

Security requirements include:

- Role-based access control
- Encryption in transit
- Secure credential storage
- Minimal integration permissions
- Webhook signature verification
- Audit logging for sensitive actions
- Configurable data retention
- Support for organizational identity providers

Sensitive operational actions must not be executable merely because a user can view the corresponding resource.

## Roadmap

### Phase 1: Foundation

- Authentication and user management
- Service catalog
- Unified dashboard
- Deployment event ingestion
- Basic task management
- Git-backed runbook indexing

### Phase 2: Collaboration

- Incident workspaces
- Team handoffs
- Additional integrations
- Search across operational resources
- Role-based access controls

### Phase 3: Advanced Workflows

- Custom dashboards
- Change approvals
- Reporting and operational metrics
- Configurable workflow automation
- Environment comparison

## Non-Goals

OpsDesk is not intended to:

- Replace CI/CD pipelines
- Become a general-purpose infrastructure monitoring engine
- Replace infrastructure-as-code tools
- Automatically modify production infrastructure without authorization
- Require teams to migrate existing operational documentation
- Create additional administrative work merely to populate dashboards

## Contributing

Contributions, feature proposals, bug reports, and documentation improvements will be welcome when the project repository is published.

Development guidelines and contribution instructions will be added alongside the initial implementation.

## License

License to be determined before the first public release.
