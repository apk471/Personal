# DevOps Study Notes for Backend Developers

These notes summarize the DevOps topics studied today from the point of view of a backend developer. The goal is not to become a full-time DevOps engineer immediately, but to understand enough to build, ship, debug, and operate backend services with confidence.

---

## What DevOps Means for Backend Work

DevOps is the set of practices that turns code into a running, monitored, repeatable production system.

For a backend developer, the practical meaning is:

- Your code should be easy to build.
- Your tests should run automatically.
- Your service should be packaged predictably.
- Your deployment should be repeatable.
- Your runtime configuration should be explicit.
- Your logs, metrics, and failures should be visible.
- Your team should be able to roll forward or roll back safely.

The core tools you studied fit together like this:

```text
Code push
  -> CI/CD pipeline
  -> GitHub Actions workflow
  -> Build/test/lint
  -> Docker image
  -> Registry
  -> Deployment environment
```

---

## Topics in This Folder

| File | What it covers |
| --- | --- |
| `ci-cd.md` | CI/CD concepts, pipeline stages, backend best practices, release safety |
| `github-actions.md` | `.github/workflows`, YAML syntax, events, jobs, steps, actions, secrets, matrices |
| `docker.md` | Docker images, containers, volumes, Dockerfile, registry, Docker Compose, commands |

---

## Mental Model

### CI/CD

CI/CD is the automation layer that checks and ships your code.

- CI means Continuous Integration: automatically validate code changes.
- CD can mean Continuous Delivery: keep code always deployable.
- CD can also mean Continuous Deployment: automatically deploy after checks pass.

Backend examples:

- Run unit tests on every PR.
- Run integration tests with Postgres/Redis.
- Build a Docker image after merge.
- Push image to a registry.
- Deploy to staging or production.

### GitHub Actions

GitHub Actions is GitHub's built-in automation system. You write YAML files under `.github/workflows/`, and GitHub runs those workflows when events happen.

Backend examples:

- On pull request: lint, test, build.
- On push to `main`: build and publish Docker image.
- On release tag: deploy production.
- On schedule: run nightly tests or dependency checks.

### Docker

Docker packages your app with its runtime environment.

Instead of saying "install Node 20, set these env vars, install these packages, then run this command", you define an image that contains exactly what your service needs.

Backend examples:

- Build a Go API into a small container image.
- Run API + Postgres + Redis locally using Docker Compose.
- Publish an image to Docker Hub or GHCR.
- Deploy the same image to staging and production.

---

## Backend Developer Checklist

For every backend service, try to have:

- A clear build command
- A clear test command
- A Dockerfile
- A local `docker-compose.yml` for dependencies
- A CI workflow that runs tests on PRs
- A workflow that builds the Docker image
- Secrets stored in GitHub Secrets, not in code
- Health checks for deployed services
- Logs that make production debugging possible
- A rollback plan

---

## Common Mistakes to Avoid

- Building different artifacts for staging and production
- Keeping secrets in YAML, Dockerfiles, or committed `.env` files
- Running tests only locally
- Using `latest` everywhere without knowing what version is deployed
- Making Docker images huge by copying unnecessary files
- Installing dependencies at container startup instead of image build time
- Deploying straight from a feature branch without review or checks
- Ignoring failed CI because "it works on my machine"

---

## Study Order

Recommended order for backend devs:

1. Learn CI/CD pipeline stages and why they exist.
2. Learn GitHub Actions workflow structure.
3. Learn Dockerfile basics and image/container lifecycle.
4. Learn Docker Compose for local dependency stacks.
5. Learn secrets, caching, artifacts, and registries.
6. Learn deployment strategies and rollback.

