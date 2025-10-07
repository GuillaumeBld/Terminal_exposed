# Google Cloud CLI usage

Open the terminal pane, then run:
```bash
gcloud init
gcloud auth login
gcloud config set project YOUR_PROJECT_ID
```

Tips:
- Use service account impersonation if possible:
  ```bash
  gcloud auth application-default login
  gcloud iam service-accounts add-iam-policy-binding SA@proj.iam.gserviceaccount.com     --member='user:you@example.com' --role='roles/iam.serviceAccountTokenCreator'
  ```
- Store active configuration in `$HOME/.config/gcloud`, persisted on the named volume.
