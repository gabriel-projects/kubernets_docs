# 06 - ConfigMaps e Secrets

## Objetivo
Gerenciar configuração e dados sensíveis de forma separada da imagem.

## Comandos essenciais
```bash
kubectl get configmap -n <namespace>
kubectl describe configmap <name> -n <namespace>
kubectl get secret -n <namespace>
kubectl describe secret <name> -n <namespace>
kubectl create secret generic <name> --from-literal=KEY=VALUE -n <namespace>
```

## Exemplo prático (AKS)
```bash
kubectl create secret generic api-secrets --from-literal=ConnectionStrings__Db=... -n app-dev
kubectl get secret api-secrets -n app-dev
```

## Erros comuns e correção
- Chave não lida pelo app: validar nome da variável/volume mount.
- Secret visível em logs: remover logs sensíveis e rotacionar segredo.

## Referências
- Kubernetes configmap docs
- Kubernetes secret docs
