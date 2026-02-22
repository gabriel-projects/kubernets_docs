# 05 - Services e Networking

## Objetivo
Expor aplicações e validar conectividade entre pods/serviços.

## Comandos essenciais
```bash
kubectl get svc -n <namespace>
kubectl describe svc <service> -n <namespace>
kubectl get endpoints <service> -n <namespace>
kubectl port-forward svc/<service> 8080:80 -n <namespace>
kubectl get ingress -n <namespace>
```

## Exemplo prático (AKS)
```bash
kubectl get svc -n app-dev
kubectl get endpoints api -n app-dev
kubectl port-forward svc/api 8080:80 -n app-dev
```

## Erros comuns e correção
- Service sem endpoint: selector não bate com labels do pod.
- Timeout externo: validar tipo do service, ingress e NSG.

## Referências
- Kubernetes service docs
- Kubernetes ingress docs
