# smartapp-gitops

Repo GitOps cho Lab 06 (web = podinfo). Có sẵn 2 phiên bản:

- tag `v1` — podinfo 6.13.0 (phiên bản khởi đầu, cũng là `main`)
- tag `v2` — podinfo 6.14.0 (phiên bản nâng cấp)

## Trainee làm gì
1. **Fork** repo này về tài khoản của bạn.
2. Sửa `repoURL` trong `argocd/smartapp-staging.yaml` thành fork của bạn, rồi `kubectl apply -f`.
3. **Nâng cấp** bằng 1 trong 2 cách:
   - *Commit qua Web IDE:* sửa `newTag: "6.13.0"` -> `"6.14.0"` trong `overlays/*/kustomization.yaml`, commit thẳng lên `main`. ArgoCD tự đồng bộ.
   - *Đổi tag:* sửa `targetRevision: v1` -> `v2` trong Application.

Cấu trúc:
```
base/{deployment,service,kustomization}.yaml
overlays/staging/kustomization.yaml      # replicas 2
overlays/production/kustomization.yaml   # replicas 5
argocd/smartapp-staging.yaml             # Application mẫu (đổi repoURL)
```
