# action-argocd-webhook-notification

**action-argocd-webhook-notification** is a github action that send a notification to argocd.

## Inputs

```yaml
- name: Notify Argocd
  uses: numerique-gouv/action-argocd-webhook-notification@v1
  id: notify
  with:
    # ex: numerique-gouv/action-argocd-webhook-notification
    deployment_repo_path: "${{ secrets.DEPLOYMENT_REPO_URL }}"
    # value of webhook.github.secret in argocd helm chart
    argocd_webhook_secret: "${{ secrets.ARGOCD_PREPROD_WEBHOOK_SECRET }}"
    argocd_url: https://argocd.example.com
```

## Exemple

```yaml
name: Argocd notify
run-name: Argocd notify

on:
  push:

jobs:
  argocd-notify:
    runs-on: linux
    steps:
      - uses: numerique-gouv/action-argocd-webhook-notification@main
        id: notify
        with:
          deployment_repo_path: "${{ secrets.DEPLOYMENT_REPO_URL }}"
          argocd_webhook_secret: "${{ secrets.ARGOCD_PREPROD_WEBHOOK_SECRET }}"
          argocd_url: https://argocd.example.com
```
