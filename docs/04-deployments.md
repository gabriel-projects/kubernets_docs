# 04 - Deployments

## Objetivo
Gerenciar rollout, rollback e escala de aplicações stateless.

## Comandos essenciais
```bash
kubectl get deploy -n <namespace>
kubectl apply -f ./k8s/ -n <namespace>
kubectl rollout status deployment/<deployment> -n <namespace>
kubectl rollout history deployment/<deployment> -n <namespace>
kubectl rollout undo deployment/<deployment> -n <namespace>
kubectl scale deployment/<deployment> --replicas=3 -n <namespace>
```

## Exemplo prático (AKS)
```bash
kubectl apply -f ./k8s/api-deployment.yaml -n app-dev
kubectl rollout status deployment/api -n app-dev
kubectl rollout history deployment/api -n app-dev
```

## Erros comuns e correção
- Rollout travado: verificar readiness/liveness probe.
- Nova versão não sobe: revisar imagem e recursos solicitados.

## Referências
- Kubernetes deployment docs
