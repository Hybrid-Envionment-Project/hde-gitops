# hde-gitops
HDE Kubernetes manifests reconciled by Argo CD
Desired-state repository for the Hybrid Development Environment (HDE) Phase 3.
Argo CD reconciles the manifests in this repository to the approved Kubernetes target.

## Scope
Binary Bit Ops/Nexus remains the live PHP/MySQL application on Truehost cPanel.
This repository does not authorise a Kubernetes migration of that application.

## Rules
- Changes are made by pull request only; direct pushes to `main` are blocked.
- At least one independent approval is required before merging.
- No secrets, credentials, kubeconfig files or real hostnames are committed here.
- Secrets are supplied at runtime by the managed secrets service.

## Governed delivery path
Protected GitHub PR -> independent approval -> Tekton build and test -> Trivy and
secrets gates -> immutable artifact and evidence -> Argo CD reconciliation -> Kubernetes.

## Layout
- `apps/`   application manifests
- `base/`   shared base configuration
- `envs/`   per-environment overlays (for example `dev`, `prod`)

## Owners
See `.github/CODEOWNERS`.
