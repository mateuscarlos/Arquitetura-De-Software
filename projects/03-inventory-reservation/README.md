# Desafio de Arquitetura: Reserva de Estoque em Alta Concorrência

## 🏢 Contexto do Negócio
Um grande varejista está se preparando para a Black Friday. O produto estrela será vendido com 80% de desconto e há apenas **500 unidades** em estoque físico. Espera-se **50.000 usuários simultâneos** tentando clicar no botão "Comprar" no mesmo segundo.

## ⚠️ O Problema Atual
* No ano passado, o sistema vendeu 600 unidades (100 a mais do que existia) devido a problemas de concorrência no banco de dados. Isso gerou prejuízo e processos judiciais.
* O sistema ficou lento e derrubou o checkout de outros produtos que não estavam na promoção.

## 🎯 Requisitos do Sistema (O que você deve resolver)
1.  **Integridade de Estoque:** É inaceitável vender mais itens do que o disponível (Overselling Zero).
2.  **Alta Disponibilidade:** O serviço de estoque deve aguentar picos de 10k requisições/segundo.
3.  **Experiência do Usuário:** O usuário não pode ficar esperando 30 segundos para saber se conseguiu reservar o item. O feedback deve ser rápido.
4.  **Expiração:** Se o usuário reservar o item e não pagar em 10 minutos, o item deve voltar imediatamente para a prateleira virtual.

## 🧠 Decisões Esperadas
* Como controlar o travamento (Locking) do registro no banco de dados sem deixar o sistema lento?
* Vale a pena usar Banco Relacional ou NoSQL (Key-Value) para controlar o contador?
* Como implementar o mecanismo de TTL (Time-to-Live) para carrinhos abandonados?