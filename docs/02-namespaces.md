# 02 - Namespaces

## Objetivo
Organizar workloads por ambiente/time e reduzir risco operacional.

## Comandos essenciais
```bash
kubectl get ns
kubectl create ns <namespace>
kubectl get all -n <namespace>
kubectl config set-context --current --namespace=<namespace>
kubectl delete ns <namespace>
```

## Exemplo prático (AKS)
```bash
kubectl create ns app-dev
kubectl config set-context --current --namespace=app-dev
kubectl get all
```

## Erros comuns e correção
- Recurso "sumiu": geralmente foi criado em outro namespace.
- Exclusão acidental: evitar `delete ns` sem validar impacto.

## Referências
- Kubernetes namespace docs
