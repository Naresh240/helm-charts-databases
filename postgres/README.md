# Postgres Helm chart with Existing Secrets

## Pre-Requisites

```bash
kubernetes cluster
```

## kubernetes cluster - minikube
[minikube setup](https://github.com/Naresh240/kubernetes/blob/main/minikube-setup/README.md)

## Create Secret

```bash
---
apiVersion: v1
kind: Secret
metadata:
  name: postgresql-secrets
type: Opaque
data: 
  postgres-password: <base64 encoded value>
  password: <base64 encoded value>
  replication-password: <base64 encoded value>
```

# Deploy Helm Chart 

```bash
helm repo add helm-repo https://charts.bitnami.com/bitnami
helm install postgresql-release helm-repo/postgresql --dry-run --debug -f postgres-values.yaml
helm install postgresql-release helm-repo/postgresql -f postgres-values.yaml
```

## Check Pod and connect pod

```bash
kubectl get pods
kubectl exec -it postgresql-release-0 /bin/bash
```

![image](https://user-images.githubusercontent.com/58024415/209758873-8ec46526-88b2-4169-b30b-a43e40d7131e.png)
