# ☸️ Kubernetes Journey: Do Zero ao Cluster

Este repositório documenta minha jornada prática de estudos em orquestração de containers, seguindo o roadmap do **Descomplicando Kubernetes**. 

O objetivo é transformar teoria em manifestos YAML funcionais, explorando cenários reais de administração de clusters, ciclo de vida de aplicações e persistência de dados.

## 🚀 O que tem por aqui?

A estrutura segue minha evolução diária de aprendizado:

### 📂 Dia 1: Fundamentos e Arquitetura
* Entendimento do Control Plane vs Workers.
* Criação de primeiros Pods e interações básicas com a API do K8s.
* Conceitos de Container Runtime (Docker/Containerd).

### 📂 Dia 2: Volumes e Observabilidade
* **Armazenamento provisório (`emptyDir`):** Implementação de volumes compartilhados entre containers no mesmo Pod (Sidecar Pattern) para cache e troca de arquivos temporários.
* **Troubleshooting Dinâmico:** Monitoramento de logs em tempo real (`kubectl logs -f`) para depuração de aplicações distribuídas.
* Ciclo de vida dos Pods e gerenciamento de recursos.

---

## 🛠 Tech Stack
* **Orquestração:** Kubernetes (K8s)
* **Containerização:** Docker
* **Infraestrutura:** Linux

## 📝 Próximos Passos
- [ ] Explorar PersistentVolumes (PV) e Claims (PVC).
- [ ] Implementar Deployments e Services.
- [ ] Configurar Ingress Controllers.

---
*Desenvolvido por Heverton Oliveira | Focado em SRE & Cloud Native*
