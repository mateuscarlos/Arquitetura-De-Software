# Desafio de Arquitetura: Plataforma de Telemedicina e Prontuário Seguro

## 🏢 Contexto do Negócio
Uma HealthTech precisa lançar um módulo onde médicos possam gravar as videoconsultas e anexar laudos em PDF para os pacientes. Devido à natureza sensível dos dados (Saúde), a segurança e a auditoria são prioridade zero.

## ⚠️ O Problema Atual
* Atualmente, os arquivos são salvos em pastas de rede sem criptografia.
* Não há registro de quem acessou o prontuário do paciente (Audit Log falho).
* O upload de arquivos grandes (vídeos de 1GB) trava o servidor de aplicação.

## 🎯 Requisitos do Sistema (O que você deve resolver)
1.  **Segurança (Data at Rest):** Todos os arquivos e dados do banco devem ser criptografados.
2.  **Gestão de Acesso:** Apenas o médico do paciente e o próprio paciente podem acessar o vídeo/laudo. O link não pode ser público.
3.  **Auditabilidade:** Cada visualização de arquivo deve gerar um log imutável para fins jurídicos.
4.  **Performance de Upload:** O upload de vídeos longos não pode consumir memória/CPU do servidor principal da API.

## 🧠 Decisões Esperadas
* Como gerenciar o upload de arquivos grandes sem passar pela API principal? (Signed URLs?)
* Qual a estratégia para garantir que, mesmo se o banco vazar, os dados pessoais estejam ilegíveis?
* Como separar os dados de log (Auditoria) dos dados transacionais para evitar gargalos?