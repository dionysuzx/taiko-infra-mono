# taiko-infra-mono

This repo contains application manifests, which are used by ArgoCD to declaratively and automatically manage a Kubernetes cluster.

A parent application manages all the child applications. To update the state of the cluster (update images, change configurations), you can simply update this repo, and ArgoCD will update the cluster. You can also add new applications, and ArgoCD will add them automatically.

See here for the ArgoCD UI view:

<img width="1900" alt="image" src="https://github.com/user-attachments/assets/3a843996-d2fa-42e1-aa24-4388be05b2a8">


