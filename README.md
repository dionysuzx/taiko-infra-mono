# taiko-infra-mono

This repo contains application manifests, which are used by ArgoCD to automatically manage a Kubernetes cluster.

To update the state of the cluster (update image tags, change configurations), you can simply update this repo, and ArgoCD will update the cluster. You can add, remove, or update application manifests here, and ArgoCD will ensure the cluster state matches for the applications it governs. It won't disrupt resources not managed by ArgoCD, allowing for a hybrid approach.

ArgoCD UI view:

<img width="1602" alt="image" src="https://github.com/user-attachments/assets/5ca25bdc-0639-4be2-97b5-9095cee60aaf">
