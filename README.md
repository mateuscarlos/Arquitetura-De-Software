# Arquitetura de Referência: Modernização de Legado (Enterprise)

Este repositório documenta padrões arquiteturais e estratégias para modernização de sistemas monolíticos em ambientes corporativos, com foco em resiliência e observabilidade na AWS.

## 🏗️ Cenário de Referência: Processamento de Alta Volumetria (Oil & Gas / Pedágios)

A solução proposta utiliza o padrão **Strangler Fig** para migrar gradualmente funcionalidades de um legado (.NET Framework) para microsserviços (.NET Core), garantindo zero downtime.

### Desenho da Solução (C4 Model - Container View)

```mermaid
graph TD
    Client[Client App / Edge Device] -->|HTTPS| ALB[AWS Application Load Balancer]
    
    subgraph "Camada de Modernização (AWS)"
        ALB -->|Rota /api/v2| BFF[BFF .NET 8]
        BFF -->|Pub| SQS[Amazon SQS]
        
        subgraph "Processamento Assíncrono"
            Worker[Worker Service .NET] -->|Sub| SQS
            Worker -->|Write| DynamoDB[(DynamoDB - Hot Data)]
            Worker -->|Archive| S3[S3 Bucket - Cold Data]
        end
    end
    
    subgraph "Legado (On-Premise / EC2)"
        ALB -->|Rota /api/v1 (Fallback)| Monolito[Legado .NET 4.8]
        Monolito -->|Read/Write| Oracle[(Oracle DB)]
    end
    
    Worker -.->|Sync Event| Oracle