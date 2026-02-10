# 📋 Cheat Sheet - Day 2: Comandos Essenciais, Diagnóstico e Stress Test

Este guia reúne os comandos utilizados para gerenciamento imperativo vs declarativo, interação com containers e testes de consumo de recursos (CPU/Memória).

---

## 🏗 Criação e Gerenciamento (Imperativo vs Declarativo)

**Gerar YAML sem criar o Pod (Dry Run):**
Essencial para criar modelos ("rascunhos") rápidos sem sujar o cluster.
`kubectl run giropops --image nginx --port 80 --dry-run=client -o yaml > pods.yaml`

**Criar/Atualizar via Arquivo (Declarativo):**
Lê o arquivo e aplica o estado desejado. Se mudou algo no YAML, ele atualiza.
`kubectl apply -f pods.yaml`

**Criação Rápida (Imperativo):**
Sobe um pod imediatamente. Bom para testes rápidos, ruim para histórico.
`kubectl run strigus --image nginx --port 80`

---

## 👁 Visualização e Listagem

**Listagem Geral (Todos os Namespaces):**
Vê o que está rodando no cluster inteiro (kube-system, monitoring, etc).
`kubectl get pods -A`

**Listagem Detalhada (IP e Nó):**
Mostra em qual Node o pod caiu e qual IP ele pegou.
`kubectl get pods -o wide`

**Visualização em Tempo Real (Watch):**
Atualiza a tela a cada 2s. Ótimo para ver o status mudando (`Pending` -> `ContainerCreating` -> `Running`).
`watch kubectl get pods`

**Exportar Configuração Atual:**
Vê o YAML final que o K8s aplicou (incluindo campos default que você não escreveu).
`kubectl get pods strigus -o yaml`

---

## 🔌 Acesso e Interação (Entrando no Pod)

**Exec (Novo Processo - Seguro):**
Abre um terminal "novo" dentro do container. Se você sair, o container continua rodando.
`kubectl exec -ti giropops -- bash`

**Attach (Processo Principal - Cuidado!):**
Conecta seu terminal ao processo principal (PID 1).
⚠️ **Perigo:** Se der `Ctrl+C` aqui, você pode matar o container!
`kubectl attach girus-1 -c girus-1 -ti`

**Logs (Leitura de Saída):**
Lê o que o container escreveu na saída padrão (stdout). Use `-c` se houver mais de um container.
`kubectl logs girus -c nginx`

---

## 🩺 Diagnóstico e Monitoramento de Recursos

**Raio-X do Pod (Describe):**
O comando mais importante para debug. Mostra **Eventos** (erros de agendamento, imagem ou OOMKilled).
`kubectl describe pod giropops`

**Top (Consumo Real):**
Mostra quanto de CPU e Memória o Pod está gastando agora.
`kubectl top pod giropops`

---

## 🐧 Comandos Internos (Dentro do Container) & Stress Test

*Estes comandos são rodados após fazer um `kubectl exec` ou usados como argumentos para testar limites.*

**Verificar Memória (RAM):**
Mostra uso e sobra de memória em MB.
`free -m`

**Listar Processos:**
Vê o que está rodando. O processo com PID 1 é o mestre do container.
`ps -ef`

**Inspecionar Comando de Inicialização:**
Descobre qual comando exato subiu um processo (ex: PID 1).
`cat /proc/1/cmdline`

**🔥 Teste de Estresse (OOM Kill):**
Tenta ocupar 130MB de RAM propositalmente. Usado para testar se os `limits` do Pod funcionam e forçar um erro de "Out Of Memory".
`stress --vm-bytes 130M --vm 1`
