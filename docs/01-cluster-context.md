# 01 - Cluster e Contexto

## Objetivo
Entender em qual cluster/contexto você está operando e evitar comandos no ambiente errado.

## Comandos essenciais
```bash
kubectl config get-contexts
kubectl config current-context
kubectl config use-context <context>
kubectl cluster-info
kubectl get nodes -o wide
```

## Exemplo prático (AKS)
```bash
kubectl config use-context aks-prod
kubectl cluster-info
kubectl get nodes -o wide
```

## Erros comuns e correção
- Executar em cluster errado: confirme contexto antes de `apply` ou `delete`.
- Falha de autenticação: renovar credenciais com `az aks get-credentials`.

## Referências
- Kubernetes context docs
- Azure AKS authentication docs
