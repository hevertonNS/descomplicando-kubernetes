# ☸️ Day 2: Pods Avançados, Ciclo de Vida e Recursos

Neste módulo, aprofundei meus conhecimentos além do "Pod Simples". Aprendi como tornar as aplicações mais robustas e como containers colaboram entre si.

## 1. Multi-Containers e Sidecars
Um Pod pode conter múltiplos containers que trabalham juntos.
- **Conceito:** Eles compartilham o mesmo IP (localhost) e podem compartilhar Volumes.
- **Padrão Sidecar:** Um container auxiliar que ajuda o principal (ex: um container gera logs, o outro coleta e envia para o Datadog/Splunk).

## 2. InitContainers
São containers que rodam **antes** dos containers principais iniciarem.
- **Características:** Eles precisam terminar com sucesso (exit code 0) para o Pod subir.
- **Uso:** Criar diretórios, baixar repositórios git, esperar um banco de dados ficar pronto.

## 3. Probes (Sondas de Saúde)
O Kubernetes precisa saber se a aplicação está bem.
- **LivenessProbe:** "A aplicação travou?". Se falhar, o K8s **reinicia** o container.
- **ReadinessProbe:** "A aplicação pode receber tráfego?". Se falhar, o K8s **para de enviar requisições** (remove do Service), mas não reinicia.
- **StartupProbe:** Para aplicações legadas que demoram muito para iniciar.

## 4. Resources (CPU e Memória)
- **Requests:** O mínimo garantido que o container precisa para ser agendado em um Node.
- **Limits:** O teto máximo. Se passar da memória, ocorre o **OOMKill** (Out of Memory Kill).
