# taiko-infra-mono

This repo contains application manifests, which are used by ArgoCD to automatically manage a Kubernetes cluster.

To update the state of the cluster (update image tags, change configurations), you can simply update this repo, and ArgoCD will update the cluster. You can add, remove, or update application manifests here, and ArgoCD will ensure the cluster state matches for the applications it governs. It won't disrupt resources not managed by ArgoCD, allowing for a hybrid approach.

You can also use Kustomize to manage multiple environments like:

```
taiko-infra-mono/
├── apps/
│   ├── taiko-client-application.yaml
│   └── taiko-geth-application.yaml
├── overlays/
│   ├── base-overlay/
│   │   ├── kustomization.yaml
│   │   └── common-overlay.yaml
│   ├── staging/
│   │   ├── kustomization.yaml
│   │   ├── taiko-client-overlay.yaml
│   │   └── taiko-geth-overlay.yaml
│   └── prod/
│       ├── kustomization.yaml
│       ├── taiko-client-overlay.yaml
│       └── taiko-geth-overlay.yaml
├── root-application-staging.yaml
└── root-application-prod.yaml
```

So for example you can:

1. Build image on `main` in other repos.
2. Trigger repo event, and update the patch for the staging environment.
3. ArgoCD automatically updates staging with latest build.

Here is the ArgoCD UI view:

<img width="1602" alt="image" src="https://github.com/user-attachments/assets/5ca25bdc-0639-4be2-97b5-9095cee60aaf">
