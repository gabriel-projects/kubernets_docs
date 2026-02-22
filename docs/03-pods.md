# 03 - Pods

## Objetivo
Inspecionar saúde, logs e execução de containers.

## Comandos essenciais
```bash
kubectl get pods -n <namespace>
kubectl get pods -o wide -n <namespace>
kubectl describe pod <pod> -n <namespace>
kubectl logs <pod> -n <namespace>
kubectl logs <pod> -c <container> -n <namespace>
kubectl exec -it <pod> -n <namespace> -- /bin/sh
```

## Exemplo prático (AKS)
```bash
kubectl get pods -n app-dev
kubectl describe pod api-7f8f7dd7db-abcde -n app-dev
kubectl logs api-7f8f7dd7db-abcde -n app-dev --tail=200
```

## Erros comuns e correção
- `CrashLoopBackOff`: revisar logs e variáveis de ambiente.
- `ImagePullBackOff`: conferir tag, registry e permissões.

## Referências
- Kubernetes pod lifecycle docs
