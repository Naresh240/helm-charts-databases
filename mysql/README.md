# Mysql Helm chart with Existing Secrets

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
  name: mysql-secrets
type: Opaque
data: 
  mysql-root-password: <base64 encoded value>
  mysql-password: <base64 encoded value>
  mysql-replication-password: <base64 encoded value>
```

# Deploy Helm Chart 

```bash
helm repo add helm-repo https://charts.bitnami.com/bitnami
helm install mysql-release helm-repo/mysql --dry-run --debug -f mysql-values.yaml
helm install mysql-release helm-repo/mysql -f mysql-values.yaml
```

## Check Pod and connect pod

```bash
kubectl get pods
kubectl exec -it mysql-release-0 /bin/bash
```

![image](https://user-images.githubusercontent.com/58024415/209756648-ed94fd0b-a0be-4770-b892-47dbd4cb4321.png)
