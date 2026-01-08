# Desafio de Arquitetura: Conciliação Financeira de Alta Volumetria

## 🏢 Contexto do Negócio
Uma Fintech de meios de pagamento processa cerca de **2 milhões de transações diárias**. No final do dia (D+0), é necessário garantir que todas as transações registradas no sistema interno batam exatamente com os arquivos de extrato enviados pelos bancos parceiros e bandeiras de cartão (Arquivos CNAB/EDI).

## ⚠️ O Problema Atual
* O processo atual é um script monolítico que roda na madrugada.
* Com o aumento do volume, o script está demorando mais de 6 horas para rodar, invadindo o horário comercial e travando o banco de dados principal.
* Quando ocorre um erro na linha 500.000, o processo para e precisa ser reiniciado do zero.
* O time financeiro não tem visibilidade das divergências até que o TI extraia um relatório manual.

## 🎯 Requisitos do Sistema (O que você deve resolver)
1.  **Janela de Processamento:** O sistema deve processar os 2 milhões de registros em, no máximo, **1 hora**.
2.  **Resiliência:** Se um arquivo estiver corrompido ou uma linha falhar, o processamento dos outros arquivos não pode parar.
3.  **Observabilidade:** O time financeiro precisa de um Dashboard em tempo real mostrando o progresso e as divergências encontradas (Conciliado vs. Pendente).
4.  **Legado:** A ingestão deve aceitar arquivos de texto posicionais (Flat Files) vindos de servidores SFTP antigos.

## 🧠 Decisões Esperadas
* Qual estratégia de processamento usar? (Batch, Stream, Event-Driven?)
* Como garantir que a leitura dos arquivos não derrube o banco de dados da operação online?
* Como lidar com a idempotência (evitar processar o mesmo arquivo duas vezes)?