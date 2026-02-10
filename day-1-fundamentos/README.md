# ☸️ Day 1: Fundamentos e Arquitetura do Kubernetes

Neste dia, foquei em entender como o Kubernetes funciona "por baixo do capô" e subi meu primeiro cluster local.

## 🏗 Arquitetura do Cluster

Entendi que o K8s não é uma caixa preta, mas um conjunto de componentes divididos em duas funções:

### 🧠 Control Plane (Gerenciamento)
Quem "manda" no cluster.
- **API Server:** A porta de entrada (REST). Tudo passa por aqui.
- **etcd:** O "banco de dados" chave-valor onde fica o estado do cluster.
- **Scheduler:** O agendador que decide em qual nó um Pod vai nascer.
- **Controller Manager:** O "fiscal" que garante que o estado desejado seja mantido.

### 💪 Workers (Execução)
Onde as aplicações rodam de fato.
- **Kubelet:** O agente que roda em cada nó e fala com o API Server.
- **Kube-proxy:** Responsável pelas regras de rede e IPs.
- **Container Runtime:** Quem roda os containers (Docker/Containerd/CRI-O).

## 🛠 Ferramentas Utilizadas
- **Kind:** Para rodar o cluster localmente usando containers Docker como nós.
- **Kubectl:** A CLI (ferramenta de linha de comando) para interagir com a API.# ☸️ Day 1: Fundamentos e Arquitetura do Kubernetes

Nesse dia, foquei em entender como o Kubernetes funciona "por baixo do capô" e subi meu primeiro cluster local.

## 🏗 Arquitetura do Cluster

Entendi que o K8s não é uma caixa preta, mas um conjunto de componentes divididos em duas funções:

### 🧠 Control Plane (Gerenciamento)
Quem "manda" no cluster.
- **API Server:** A porta de entrada (REST). Tudo passa por aqui.
- **etcd:** O "banco de dados" chave-valor onde fica o estado do cluster.
- **Scheduler:** O agendador que decide em qual nó um Pod vai nascer.
- **Controller Manager:** O "fiscal" que garante que o estado desejado seja mantido.

### 💪 Workers (Execução)
Onde as aplicações rodam de fato.
- **Kubelet:** O agente que roda em cada nó e fala com o API Server.
- **Kube-proxy:** Responsável pelas regras de rede e IPs.
- **Container Runtime:** Quem roda os containers (Docker/Containerd/CRI-O).

## 🛠 Ferramentas Utilizadas
- **Kind:** Para rodar o cluster localmente usando containers Docker como nós.
- **Kubectl:** A CLI (ferramenta de linha de comando) para interagir com a API.
