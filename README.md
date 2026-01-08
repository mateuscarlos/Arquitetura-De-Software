# 🏛️ Architecture & Decision Log (ADL)

Bem-vindo ao meu repositório de **Análises Arquiteturais e Padrões de Design**.

Este repositório atua como um *Knowledge Base* demonstrando minha abordagem para resolver problemas complexos de software em ambientes corporativos (Enterprise). Aqui documento não apenas o "como" (código), mas principalmente o "porquê" (decisões, trade-offs e estratégias).

## 🎯 Objetivo
Demonstrar a aplicação prática de padrões de arquitetura para resolver requisitos não-funcionais críticos, como:
* **Alta Disponibilidade & Resiliência** (Circuit Breakers, Queues, Fallbacks).
* **Integração com Legado** (ACL, Strangler Fig).
* **Escalabilidade** (Event-Driven Architecture, Caching Strategies).
* **Observabilidade** (Distributed Tracing, Health Checks).

## 📚 Catálogo de Projetos (Case Studies)

Abaixo estão listados os estudos de caso e desenhos de solução contidos neste repositório. Cada projeto representa um cenário de negócio distinto com desafios técnicos específicos.

| Projeto | Cenário de Negócio | Padrões Chave | Stack |
| :--- | :--- | :--- | :--- |
| **[📂 01. Telemetry Billing](./projects/01-telemetry-billing/README.md)** | Processamento de alta volumetria de dados IoT para faturamento contratual. | *Event-Driven, Anti-Corruption Layer (ACL), Decoupling* | .NET 8, AWS SQS, Oracle, Redis |
| **[📂 02. Financial Reconciliation](./projects/02-financial-reconciliation/README.md)** | Conciliação de 2 milhões de transações diárias com arquivos bancários. | *Batch Processing, Idempotency, Event-Driven* | .NET, AWS S3, SFTP |
| **[📂 03. Inventory Reservation](./projects/03-inventory-reservation/README.md)** | Controle de estoque em alta concorrência durante Black Friday. | *Distributed Locking, TTL, Cache-Aside* | Redis, PostgreSQL |
| **[📂 04. Secure Telemedicine](./projects/04-secure-telemedicine/README.md)** | Plataforma de telemedicina com segurança e auditoria. | *Encryption at Rest, Signed URLs, Audit Log* | .NET, AWS S3, KMS |

---

## 🛠️ Ferramentas & Metodologias
Utilizo as seguintes abordagens para documentação e desenho:
* **C4 Model:** Para visualização em diferentes níveis de abstração (Context, Container, Component).
* **ADR (Architecture Decision Records):** Para registrar o contexto das escolhas técnicas.
* **Mermaid.js:** Para diagramas como código (Diagrams as Code).

---
*Disclaimer: Os projetos aqui apresentados são cenários de referência baseados em padrões de mercado. Quaisquer semelhanças com sistemas reais são coincidências ou abstrações genéricas para fins educacionais.*