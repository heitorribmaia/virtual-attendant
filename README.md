# 🤖 Virtual Attendant — Atendente Virtual para WhatsApp

Workflow em n8n para atendimento automatizado no WhatsApp, com IA, transcrição de áudios, análise de imagens, controle de horário e integração com Chatwoot e Google Sheets.

---

## 📋 Sobre o Projeto

O **Virtual Attendant** é um agente de atendimento inteligente desenvolvido no n8n para automatizar conversas no WhatsApp via **Evolution API**. Ele utiliza modelos de IA (DeepSeek e Perplexity) para responder mensagens, e possui lógica para escalar o atendimento para um humano quando necessário.

---

## ✨ Funcionalidades

- 💬 **Atendimento automático via WhatsApp** com IA (DeepSeek / Perplexity)
- 🎙️ **Transcrição de áudios** recebidos no WhatsApp
- 🖼️ **Análise de imagens** com OpenAI Vision
- 🕐 **Controle de horário de atendimento** (fora do horário notifica o cliente)
- 👤 **Escalonamento para atendente humano** quando necessário
- 🏷️ **Gerenciamento de etiquetas** no WhatsApp
- 📋 **Registro de clientes** no Google Sheets
- 🗂️ **Histórico de mensagens** por conversa
- 🔗 **Integração com Chatwoot** para gestão de atendimentos

---

## 🛠️ Tecnologias e Integrações

| Ferramenta | Uso |
|---|---|
| [n8n](https://n8n.io) | Plataforma de automação |
| [Evolution API](https://evolution-api.com) | Conexão com WhatsApp |
| [DeepSeek](https://deepseek.com) | Modelo de IA para respostas |
| [Perplexity](https://perplexity.ai) | Modelo de IA alternativo |
| [OpenAI](https://openai.com) | Análise de imagens (Vision) |
| [Chatwoot](https://chatwoot.com) | CRM de atendimento |
| Google Sheets | Cadastro de clientes |

---

## 🚀 Como Usar

### Pré-requisitos

- n8n instalado (self-hosted ou cloud)
- Evolution API configurada e conectada ao WhatsApp
- Contas nas APIs: DeepSeek, Perplexity, OpenAI
- Instância do Chatwoot (opcional)
- Google Sheets com credenciais configuradas

### Importando o Workflow

1. Acesse seu n8n
2. Vá em **Workflows → Import from file**
3. Selecione o arquivo `Virtual-attendant.json`
4. Configure as credenciais de cada nó
5. Ative o webhook e o workflow

### Configurações necessárias

Após importar, atualize as seguintes variáveis no nó **Global**:

- `instancia` → nome da instância da Evolution API
- `api_key_evolution` → chave da Evolution API

E configure as credenciais nos nós de cada serviço (DeepSeek, OpenAI, Chatwoot, Google Sheets).

---

## 📁 Estrutura do Workflow

```
Webhook (entrada)
  └── Switch (tipo de mensagem)
        ├── Texto → IA (DeepSeek/Perplexity) → Resposta
        ├── Áudio → Transcrição → IA → Resposta
        ├── Imagem → Análise OpenAI → Resposta
        └── Verificações
              ├── Horário de atendimento
              ├── Etiqueta humano
              └── Escalonamento para humano
```

---

## ⚠️ Segurança

Nunca suba o arquivo JSON com credenciais reais. Antes de exportar e commitar, remova todas as API keys dos nós.

---

## 📄 Licença

Projeto de uso interno. Todos os direitos reservados.
