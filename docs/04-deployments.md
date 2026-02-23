# 04 - Deployments

## Objetivo
Gerenciar rollout, rollback e escala de aplicações stateless.

## `kubectl apply -f` vs `kubectl apply -k`

### `kubectl apply -f`
Aplica arquivos YAML **diretamente** (arquivo único ou pasta).

Quando usar:
- Você já tem os manifests finais prontos.
- Estrutura simples, sem variações por ambiente.

Exemplos:
```bash
kubectl apply -f deployment.yaml
kubectl apply -f ./k8s/
```

### `kubectl apply -k`
Aplica manifests **gerados pelo Kustomize** a partir de um `kustomization.yaml`.

Quando usar:
- Você tem múltiplos ambientes (dev/staging/prod).
- Precisa reutilizar base e aplicar overlays sem duplicar YAML.

Exemplos:
```bash
kubectl apply -k overlays/dev
kubectl apply -k overlays/prod
```

Resumo rápido:
- `-f`: aplica YAML pronto.
- `-k`: monta e aplica YAML via Kustomize.

## Comandos essenciais
```bash
kubectl get deploy -n <namespace>
kubectl apply -f ./k8s/ -n <namespace>
kubectl rollout status deployment/<deployment> -n <namespace>
kubectl rollout history deployment/<deployment> -n <namespace>
kubectl rollout undo deployment/<deployment> -n <namespace>
kubectl scale deployment/<deployment> --replicas=3 -n <namespace>
```

## Deployments (com Kustomize)
```bash
kubectl apply -k overlays/dev
kubectl apply -k overlays/staging
kubectl apply -k overlays/prod
kubectl rollout status deployment/<deployment> -n <namespace>
kubectl rollout history deployment/<deployment> -n <namespace>
kubectl rollout undo deployment/<deployment> -n <namespace>
kubectl diff -k overlays/dev
kubectl kustomize overlays/dev
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
