# 🚀 Elite SRE Lab — Production Reliability Engineering

![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-blue)
![Docker](https://img.shields.io/badge/Docker-Containers-blue)
![Kafka](https://img.shields.io/badge/Kafka-Event%20Streaming-black)
![Prometheus](https://img.shields.io/badge/Prometheus-Monitoring-orange)
![Grafana](https://img.shields.io/badge/Grafana-Dashboards-yellow)
![SRE](https://img.shields.io/badge/SRE-Reliability-critical)

---

## 🧠 Visão Geral

O **Elite SRE Lab** é um laboratório prático de engenharia de confiabilidade que simula um ambiente real de produção baseado em microserviços.

Construído a partir do **Online Boutique**, o projeto evolui de um simples deploy para um sistema:

* Observável
* Resiliente
* Escalável
* Operável como produção

---

## 🎯 Objetivo

Demonstrar na prática:

* Operação em Kubernetes
* Observabilidade (métricas, logs, tracing)
* Event Streaming com Kafka
* Definição de SLO
* Simulação de incidentes reais

---

## 🧱 Arquitetura

```text
Usuário
   ↓
Frontend
   ↓
Checkout
   ↓
Payment → Shipping
   ↓
Resposta

+ Event Streaming:
Checkout → Kafka → Consumer
```

---

## 🧰 Stack Tecnológica

### ☸️ Orquestração

* Kubernetes

### 🐳 Containerização

* Docker

### 📊 Observabilidade

* Prometheus
* Grafana
* OpenTelemetry

### 📡 Event Streaming

* Kafka

### ⚙️ Automação

* Alertmanager
* HPA (Horizontal Pod Autoscaler)

---

## 📊 Observabilidade

### Modelo adotado: RED Metrics

* **Rate** → requisições por segundo
* **Errors** → taxa de erro
* **Duration** → latência

---

## 📈 SLO (Service Level Objective)

### Serviço crítico: Checkout

* 99% das requisições < 500ms
* < 1% de erro
* Janela de 30 dias

---

## 📡 Kafka (Event Streaming)

### Evento

```json
{
  "event": "order_created",
  "value": 100
}
```

### Fluxo

```text
Checkout → Kafka → Order Consumer
```

---

## 🚨 Incidentes Simulados

* 🔴 Alta latência no Checkout
* 🔴 Falha em cascata (Payment)
* 🔴 Consumer Kafka indisponível
* 🔴 Pico de tráfego (simulação Black Friday)

---

## 🧾 Postmortem

Cada incidente contém:

* Diagnóstico
* Causa raiz
* Ação corretiva
* Lições aprendidas

---

## 🚀 Como Executar

```bash
git clone https://github.com/GoogleCloudPlatform/microservices-demo.git
cd microservices-demo
kubectl apply -f ./release/kubernetes-manifests.yaml
kubectl port-forward svc/frontend 8080:80
```

👉 Acesse: http://localhost:8080

---

## 📂 Estrutura do Projeto

```text
elite-sre-lab/
│
├── docker/
├── kubernetes/
├── monitoring/
├── kafka/
├── docs/
└── scripts/
```

---

## 🧠 Diferenciais do Projeto

* Simulação real de ambiente de produção
* Uso de stack padrão de mercado
* Foco em confiabilidade (SRE)
* Integração entre observabilidade e operação
* Incidentes com análise real

---

## 🚀 Próximos Passos

* 🔍 Tracing distribuído (OpenTelemetry)
* ⚡ Chaos Engineering
* 🔁 CI/CD pipeline
* 📉 Error budget alerting

---

## 👨‍💻 Autor

**Cleiton Botelho Pereira**
Production Reliability Engineering

---

## 🎯 Objetivo Profissional

Atuar como SRE/Production Engineer construindo sistemas confiáveis, escaláveis e orientados a métricas.

---

# ⭐ Se esse projeto te chamou atenção, deixe uma estrela!
