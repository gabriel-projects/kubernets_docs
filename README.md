# 📦 Kubernetes kubectl – Comandos Mais Comuns

Este repositório é um **cheat sheet prático** com os comandos mais usados do `kubectl` no dia a dia, organizado por categoria.

O objetivo é servir como **material de estudo**, **consulta rápida** e **revisão antes de entrevistas**.

---

## 🔍 Informações do Cluster

```bash
kubectl version
kubectl cluster-info
kubectl get nodes
kubectl describe node <node-name>
kubectl config get-contexts
kubectl config use-context <context>
```

---

## 📂 Namespaces

```bash
kubectl get namespaces
kubectl get pods -n <namespace>
kubectl config set-context --current --namespace=<namespace>
```

---

## 📦 Pods

```bash
kubectl get pods
kubectl get pods -o wide
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl logs <pod-name> -c <container-name>
kubectl exec -it <pod-name> -- /bin/sh
kubectl delete pod <pod-name>
```

---

## 🚀 Deployments (sem Kustomize)

```bash
kubectl apply -f deployment.yaml
kubectl apply -f ./k8s/
kubectl get deployments
kubectl describe deployment <deployment-name>
kubectl rollout status deployment <deployment-name>
kubectl rollout history deployment <deployment-name>
kubectl rollout undo deployment <deployment-name>
kubectl scale deployment <deployment-name> --replicas=3
kubectl delete -f deployment.yaml
```

---

## 🚀 Deployments (com Kustomize)

```bash
kubectl apply -k .
kubectl apply -k overlays/dev
kubectl apply -k overlays/staging
kubectl apply -k overlays/prod
kubectl get deployments
kubectl describe deployment <deployment-name>
kubectl rollout status deployment <deployment-name>
kubectl rollout history deployment <deployment-name>
kubectl rollout undo deployment <deployment-name>
kubectl delete -k .
```

### Debug antes de aplicar

```bash
kubectl kustomize .
kubectl diff -k .
```

---

## 🌐 Services & Networking

```bash
kubectl get services
kubectl describe service <service-name>
kubectl port-forward svc/<service-name> 8080:80
kubectl get endpoints
```

---

## ⚙️ ConfigMaps & Secrets

```bash
kubectl get configmaps
kubectl describe configmap <name>

kubectl get secrets
kubectl describe secret <name>
kubectl get secret <name> -o yaml
```

---

## 🧪 Debug & YAML

```bash
kubectl get pod <pod-name> -o yaml
kubectl explain pod
kubectl explain deployment.spec
```

---

## 📈 Escalabilidade

```bash
kubectl get hpa
kubectl describe hpa
```

---

## 🧹 Limpeza

```bash
kubectl get all
kubectl delete pod --all
kubectl delete all --all -n <namespace>
```

---

## 🎯 Objetivo

Este repositório serve como:
- material de estudo contínuo
- consulta rápida no dia a dia
- apoio para entrevistas técnicas
