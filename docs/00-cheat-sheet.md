# 00 - Cheat Sheet Rápido

## Objetivo
Resumo dos comandos mais usados no dia a dia para consulta em segundos.

## Comandos essenciais
```bash
kubectl get nodes
kubectl get ns
kubectl get pods -A
kubectl get svc -A
kubectl describe pod <pod> -n <ns>
kubectl logs <pod> -n <ns>
kubectl rollout status deployment/<deploy> -n <ns>
kubectl get events -n <ns> --sort-by=.metadata.creationTimestamp
```

## Exemplo prático (AKS)
```bash
kubectl config use-context <aks-context>
kubectl get pods -n app-dev
kubectl logs deploy/api -n app-dev --tail=100
```

## Erros comuns e correção
- Contexto errado: valide com `kubectl config current-context`.
- Namespace errado: sempre informe `-n <namespace>`.

## Referências
- Kubernetes Docs: kubectl quick reference
- Azure AKS docs
