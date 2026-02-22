# 07 - Debug e Troubleshooting

## Objetivo
Seguir um fluxo rápido de diagnóstico para falhas comuns em produção.

## Comandos essenciais
```bash
kubectl get pods -n <namespace>
kubectl describe pod <pod> -n <namespace>
kubectl logs <pod> -n <namespace> --previous
kubectl get events -n <namespace> --sort-by=.metadata.creationTimestamp
kubectl top pod -n <namespace>
kubectl top node
```

## Exemplo prático (AKS)
```bash
kubectl get pods -n app-prod
kubectl describe pod api-5f4c9bd7f9-xyz12 -n app-prod
kubectl logs api-5f4c9bd7f9-xyz12 -n app-prod --previous
kubectl get events -n app-prod --sort-by=.metadata.creationTimestamp
```

## Erros comuns e correção
- `OOMKilled`: aumentar limites/melhorar consumo de memória.
- `Pending`: falta de recursos/taints/quotas no cluster.

## Referências
- Kubernetes debugging pods docs
- Kubernetes resource metrics docs
