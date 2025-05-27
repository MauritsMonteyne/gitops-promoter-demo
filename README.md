
ArgoCD Applications get dynamically generated if an `argocd.json` file is present in `apps/<env>/<application>/`. Each environment has an ApplicationSet chart gets values from both the base directory and the environment specific directory. 

```
.
├── apps
│   ├── base
│   │   ├── backend
│   │   │   └── values.yaml
│   │   └── frontend
│   │       └── values.yaml
│   ├── dev
│   │   ├── backend
│   │   │   ├── argocd.json
│   │   │   └── values.yaml
│   │   └── frontend
│   │       ├── argocd.json
│   │       └── values.yaml
│   └── prod
│       ├── backend
│       │   ├── argocd.json
│       │   └── values.yaml
│       └── frontend
│           ├── argocd.json
│           └── values.yaml
```

The `argocd.json` hold the helm chart info and because it's defined per environment, each environment can run a different version if needed.

```
{
  "chart": {
    "repository": "https://ameijer.github.io/k8s-as-helm/",
    "name": "pod",
    "version": "1.0.1"
  }
}
```
