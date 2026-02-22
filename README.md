# 📘 AKS Study Notes – kubectl + Troubleshooting

Este repositório foi organizado para estudo de **AKS (Azure Kubernetes Service)** com foco em:
- consulta rápida de comandos
- revisão para entrevistas
- troubleshooting por cenário

## 🗂️ Estrutura

- [Cheat Sheet Rápido](docs/00-cheat-sheet.md)
- [Cluster e Contexto](docs/01-cluster-context.md)
- [Namespaces](docs/02-namespaces.md)
- [Pods](docs/03-pods.md)
- [Deployments](docs/04-deployments.md)
- [Services e Networking](docs/05-services-network.md)
- [ConfigMaps e Secrets](docs/06-configmaps-secrets.md)
- [Debug e Troubleshooting](docs/07-debug-troubleshooting.md)
- [AKS Específico](docs/08-aks-especifico.md)
- [Boas Práticas](docs/09-boas-praticas.md)
- [Glossário](docs/glossario.md)

---

## 🎯 Comandos por cenário

### 1) “Não consigo acessar o app”

```bash
kubectl get svc -A
kubectl describe svc <service-name> -n <namespace>
kubectl get endpoints <service-name> -n <namespace>
kubectl port-forward svc/<service-name> 8080:80 -n <namespace>
```

### 2) “Pod não sobe / fica em CrashLoopBackOff”

```bash
kubectl get pods -n <namespace>
kubectl describe pod <pod-name> -n <namespace>
kubectl logs <pod-name> -n <namespace>
kubectl logs <pod-name> -c <container-name> -n <namespace>
```

### 3) “Deploy não atualiza”

```bash
kubectl rollout status deployment/<deployment-name> -n <namespace>
kubectl rollout history deployment/<deployment-name> -n <namespace>
kubectl rollout undo deployment/<deployment-name> -n <namespace>
```

### 4) “Quero validar antes de aplicar”

```bash
kubectl diff -f ./k8s/
kubectl apply --dry-run=client -f ./k8s/
kubectl kustomize overlays/dev
kubectl diff -k overlays/dev
```

---

## 📌 Convenção dos arquivos

Cada arquivo em `docs/` segue o mesmo padrão:
1. Objetivo
2. Comandos essenciais
3. Exemplo prático (AKS)
4. Erros comuns e correção
5. Referências

---

## 🚀 Próximos passos sugeridos

- Adicionar exemplos com namespace fixo (`app-dev`, `app-prod`)
- Incluir seção de comandos `az aks` para operações administrativas
- Evoluir para MkDocs quando passar de ~15 arquivos
