# 08 - AKS Específico

## Objetivo
Cobrir comandos administrativos do AKS com `az aks` e integração com `kubectl`.

## Comandos essenciais
```bash
az aks list -o table
az aks get-credentials -g <resource-group> -n <aks-name> --overwrite-existing
az aks show -g <resource-group> -n <aks-name> -o table
az aks nodepool list -g <resource-group> --cluster-name <aks-name> -o table
az aks command invoke -g <resource-group> -n <aks-name> --command "kubectl get nodes"
```

## Exemplo prático (AKS)
```bash
az aks get-credentials -g rg-platform -n aks-prod --overwrite-existing
kubectl config current-context
kubectl get nodes
```

## Erros comuns e correção
- `Unauthorized`: refazer login (`az login`) e atualizar credenciais do cluster.
- Contexto duplicado/confuso: usar `--overwrite-existing` e revisar `kubectl config get-contexts`.

## Referências
- Azure AKS CLI docs
- Azure AKS operations docs
