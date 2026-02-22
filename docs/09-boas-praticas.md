# 09 - Boas Práticas

## Objetivo
Consolidar práticas que reduzem incidentes e aceleram troubleshooting.

## Comandos essenciais
```bash
kubectl diff -f ./k8s/
kubectl apply --dry-run=client -f ./k8s/
kubectl kustomize overlays/dev
kubectl diff -k overlays/dev
kubectl rollout status deployment/<deployment> -n <namespace>
```

## Exemplo prático (AKS)
```bash
kubectl diff -k overlays/prod
kubectl apply -k overlays/prod
kubectl rollout status deployment/api -n app-prod
```

## Erros comuns e correção
- Aplicar sem validação: sempre usar `diff` e `dry-run`.
- Falta de padrão de labels: definir convenção para app, env e owner.

## Referências
- Kubernetes best practices
- Azure Well-Architected for AKS
