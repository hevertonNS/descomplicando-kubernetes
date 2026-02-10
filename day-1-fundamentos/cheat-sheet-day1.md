# 📋 Cheat Sheet - Day 1

## 🔧 Preparando o Ambiente (Kind & Kubectl)
Criar um cluster local com Kind:
`kind create cluster --name meu-cluster`

Listar os clusters ativos:
`kind get clusters`

## 🚀 Gerenciando Pods (Imperativo vs Declarativo)

**Modo Imperativo (Rápido, via linha de comando):**
Cria um pod chamado 'nginx-run' usando a imagem do nginx:
`kubectl run nginx-run --image=nginx`

**Modo Declarativo (Profissional, via arquivo YAML):**
Aplica a configuração do arquivo que criamos:
`kubectl apply -f primeiro-pod.yaml`

## 🔍 Inspeção e Debug
Ver se os pods estão rodando (Running):
`kubectl get pods`

Ver em qual Node o pod está rodando e seu IP:
`kubectl get pods -o wide`

Ver os detalhes técnicos (Eventos, Erros de imagem, etc):
`kubectl describe pod meu-primeiro-pod`

## 🗑 Limpeza
Deletar o pod:
`kubectl delete pod meu-primeiro-pod`
