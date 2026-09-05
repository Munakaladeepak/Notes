# Cloud and Deployment

**Priority:** Medium · **Prerequisite:** [[11 - REST and HTTP/README|REST and HTTP]] · **Related:** [[14 - Git/README|Git]], [[17 - Security/README|Security]]

## Service categories

Cloud platforms provide compute, storage, managed databases, networking, identity and access management, queues, monitoring, and secret management. The exact AWS and Google Cloud product names may differ, but the concepts transfer.

## Deployment pipeline

A pipeline may compile/build, run unit and integration tests, scan dependencies, package an artifact or container, deploy to an environment, run health checks, and monitor. CI means continuous integration; CD commonly means continuous delivery or deployment. Automated deployment still needs rollback and observability.

## Environments and configuration

Development, QA/testing, staging, and production have different data and risk. Configuration such as ports, database URLs, API endpoints, and feature flags belongs outside code. Secrets belong in environment variables or a secret manager, not Git or frontend bundles.

## Containers and availability

A container packages an application and dependencies in an isolated process environment. An image is the template; a running container is an instance. A health check may distinguish process alive from application ready. Load balancers distribute traffic. Backups are not useful unless restoration is tested.

## Scaling and resilience

Vertical scaling increases one machine’s resources. Horizontal scaling adds instances. Stateless services scale more easily. Queues absorb bursts. Timeouts, retries with backoff, circuit breakers, idempotency, and graceful degradation improve resilience, but retries can amplify load if used carelessly.

## Security and operations

Use least privilege, network segmentation, HTTPS, patching, audit logs, monitoring, alerts, and cost controls. Availability, latency, error rate, saturation, and resource utilization are common operational signals.

## Checklist

- [ ] Compute, storage, databases, networking, IAM
- [ ] CI/CD pipeline concepts
- [ ] Environments and configuration
- [ ] Containers, images, health checks
- [ ] Load balancing and scaling
- [ ] Backups and restore testing
- [ ] Timeouts, retries, queues, resilience
- [ ] Monitoring, logs, alerts, cost and security
