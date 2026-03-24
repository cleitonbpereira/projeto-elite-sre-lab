# projeto-elite-sre-lab
# Elite SRE Lab — Production Reliability Engineering (Nível Empresa)

---

# 🎯 Visão Geral

O **Elite SRE Lab** é um ambiente prático que simula um sistema de produção moderno baseado em microserviços, com foco em:

* Confiabilidade (SRE)
* Observabilidade
* Arquitetura distribuída
* Resiliência
* Operação em Kubernetes

O sistema é baseado no **Online Boutique**, evoluído para incluir práticas reais de engenharia de produção.

---

# 🧠 Objetivo do Projeto

Demonstrar, na prática, a capacidade de:

* Construir sistemas distribuídos
* Monitorar e medir confiabilidade
* Definir e operar SLOs
* Responder a incidentes reais
* Evoluir sistemas com base em dados

---

# 🧱 Arquitetura do Sistema

## Componentes

* Frontend
* Product Catalog
* Cart Service
* Checkout Service
* Payment Service
* Shipping Service
* Recommendation Service

## Infraestrutura

* Kubernetes (orquestração)
* Prometheus (métricas)
* Grafana (visualização)
* Kafka (event streaming)
* Alertmanager (alertas)

---

## 🔄 Fluxo de Requisição

```text
Usuário → Frontend → Checkout → Payment → Shipping → Resposta
                             ↓
                          Kafka (eventos)
```

---

# 📊 Observabilidade (Nível Produção)

## Estratégia

Adotado modelo **RED Metrics**:

* Rate (taxa de requisições)
* Errors (taxa de erro)
* Duration (latência)

---

## Métricas Monitoradas

### Aplicação (crítico)

* Latência por endpoint (P95, P99)
* Taxa de erro por serviço
* Throughput (requests/sec)

### Infraestrutura

* CPU por pod
* Memória
* Restart de pods

---

## Limitação atual

* Tracing distribuído (planejado com OpenTelemetry)
* Logs estruturados (próxima evolução)

---

# 📈 SLO (Service Level Objectives)

## Serviço: Checkout

### SLIs

* Latência de requisição
* Taxa de erro HTTP

---

### SLO Definido

* 99% das requisições com latência < 500ms
* Taxa de erro < 1%
* Janela de medição: 30 dias

---

### Error Budget

* 1% de falhas permitidas por período

---

### Estratégia de medição

Baseado em Prometheus:

* histogram_quantile para latência
* rate de erros por status HTTP

---

# 📡 Event Streaming (Kafka)

## Objetivo

Desacoplar serviços e melhorar resiliência

---

## Evento implementado

```json
{
  "event": "order_created",
  "value": 100
}
```

---

## Fluxo

```text
Checkout → Kafka → Order Consumer
```

---

## Benefícios

* Tolerância a falhas
* Processamento assíncrono
* Escalabilidade

---

# 🔁 Resiliência de Sistema

## Estratégias adotadas

* Retry (planejado)
* Timeout entre serviços
* Isolamento via microserviços

---

## Evolução futura

* Circuit Breaker
* Bulkhead pattern

---

# ⚙️ Automação (Confiabilidade como Código)

## Horizontal Pod Autoscaler (HPA)

Escalonamento baseado em CPU:

* Checkout Service escala automaticamente

---

## Alertas

* Alta latência
* Alta taxa de erro
* Uso excessivo de CPU

---

## Ferramentas

* Prometheus
* Alertmanager

---

# 🚨 Gerenciamento de Incidentes

---

## Incidente 1 — Alta Latência no Checkout

### Sintoma

* Aumento no tempo de resposta

### Impacto

* Degradação da experiência do usuário

---

### Diagnóstico

* CPU elevada
* Saturação do serviço

---

### Ação

* Escalonamento horizontal (HPA)

---

### Resultado

* Normalização da latência

---

---

## Incidente 2 — Falha em Cascata (Payment)

### Sintoma

* Checkout falhando intermitentemente

---

### Causa

* Latência elevada no Payment Service

---

### Impacto

* Falha em pedidos

---

### Diagnóstico

* Dependência crítica degradada

---

### Ação

* Identificação via métricas
* Isolamento do problema

---

---

## Incidente 3 — Consumer Kafka indisponível

### Sintoma

* Eventos acumulando

---

### Impacto

* Processamento atrasado

---

### Diagnóstico

* Consumer offline

---

### Ação

* Reinício do consumer
* Validação de backlog

---

---

# 🧾 Postmortem (Modelo Profissional)

## Incidente: Alta Latência Checkout

### Resumo

Latência elevada durante pico de carga

---

### Impacto

* Experiência degradada
* Potencial perda de conversão

---

### Linha do Tempo

10:00 — aumento de tráfego
10:05 — latência elevada
10:10 — investigação iniciada
10:15 — escalonamento aplicado

---

### Causa Raiz

Capacidade insuficiente sob carga

---

### Ações Corretivas

* Implementação de HPA
* Ajuste de limites de CPU

---

### Lições Aprendidas

* Necessidade de autoscaling antecipado
* Monitoramento mais agressivo

---

# 📂 Estrutura do Projeto

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

# 🧠 Narrativa de Engenharia

Este projeto demonstra a evolução de um sistema:

1. Deploy inicial de microserviços
2. Observabilidade implementada
3. Introdução de eventos (Kafka)
4. Definição de SLO
5. Simulação e resolução de incidentes
6. Melhoria contínua baseada em dados

---

# 🎯 Resultado Final

O projeto simula:

* Um ambiente real de produção
* Práticas modernas de SRE
* Tomada de decisão baseada em métricas

---

# 🚀 Próximos Passos

* Tracing distribuído (OpenTelemetry)
* Chaos Engineering
* Logs estruturados
* CI/CD pipeline
* Error budget alerting

---

# 👨‍💻 Autor

Cleiton Botelho Pereira
Production Reliability / SRE Journey

---

# 📌 Conclusão

Este projeto representa a aplicação prática de princípios de Site Reliability Engineering, com foco em:

* Confiabilidade
* Observabilidade
* Resiliência
* Operação em larga escala
