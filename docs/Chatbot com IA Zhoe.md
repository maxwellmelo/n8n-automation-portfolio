## Resumo do Workflow

Este workflow implementa um **chatbot WhatsApp inteligente** com as seguintes funcionalidades:

- Recebimento de mensagens via webhook (Z-API)
- Processamento de texto, áudio e imagens
- Integração com OpenAI para respostas inteligentes
- Gerenciamento de estado com Redis
- Detecção automática de intervenção humana
- Sistema de botões interativos
- Auditoria em Google Sheets
- Alertas por email

---

## Informações Sensíveis Removidas

### 1. Credenciais Z-API

| Original | Substituído por |
|----------|-----------------|
| Instance ID real | `DEMO_ZAPI_INSTANCE_ID` |
| Token de autenticação | `DEMO_ZAPI_TOKEN` |
| Client Token | `DEMO_ZAPI_CLIENT_TOKEN` |
| Credential ID do node | `DEMO_ZAPI_NODE_ID` |

**Motivo:** Tokens de API permitem envio de mensagens e acesso à conta.

### 2. Credenciais Evolution API

| Original | Substituído por |
|----------|-----------------|
| API Key | `DEMO_EVOLUTION_API_KEY` |

**Motivo:** Chave de API para serviço alternativo de mensageria.

### 3. Credenciais Redis

| Original | Substituído por |
|----------|-----------------|
| Credential ID | `DEMO_REDIS_ID` |
| Credential Name | `Redis_DEMO` |

**Motivo:** Acesso ao banco de dados de cache/sessão.

### 4. Credenciais OpenAI

| Original | Substituído por |
|----------|-----------------|
| Credential ID | `DEMO_OPENAI_ID` |
| Credential Name | `OpenAI_DEMO` |

**Motivo:** Acesso à API de IA que pode gerar custos.

### 5. Google Sheets

| Original | Substituído por |
|----------|-----------------|
| Spreadsheet ID | `DEMO_GOOGLE_SHEETS_ID` |
| Credential ID | `DEMO_GOOGLE_API_ID` |
| Account Name | `Google_Sheets_DEMO` |
| URLs da planilha | URLs genéricas |

**Motivo:** Acesso a dados de auditoria e informações de clientes.

### 6. Gmail

| Original | Substituído por |
|----------|-----------------|
| Email pessoal | `seu-email@exemplo.com` |
| Credential ID | `DEMO_GMAIL_ID` |
| Credential Name | `Gmail_DEMO` |

**Motivo:** Dados pessoais de contato.

### 7. Webhook IDs

| Original | Substituído por |
|----------|-----------------|
| Webhook principal | `DEMO_WEBHOOK_MAIN_ID` |
| Webhook timeout | `DEMO_WEBHOOK_TIMEOUT_ID` |
| Webhook Gmail | `DEMO_WEBHOOK_GMAIL_ID` |

**Motivo:** IDs de webhook podem ser explorados.

### 8. URLs e Domínios

| Original | Substituído por |
|----------|-----------------|
| URL do site da empresa | `https://www.sua-empresa.com.br` |
| URL da API | `http://api.sua-empresa.com.br` |
| URL do S3 (áudio) | `https://seu-bucket.s3.amazonaws.com/audio_exemplo.mp3` |

**Motivo:** Informações de infraestrutura e negócio.

### 9. Números de Telefone

| Original | Substituído por |
|----------|-----------------|
| Número pessoal | `55XXXXXXXXXXX` |

**Motivo:** Dados pessoais.

### 10. Nomes do Negócio

| Original | Substituído por |
|----------|-----------------|
| Nome da empresa | `[SUA EMPRESA]` |
| Nome do bot | `[ASSISTENTE]` |

**Motivo:** Preservar identidade do negócio para demonstração.

---

## Modificações para Demonstração

### 1. Nome do Workflow

- **Antes:** `Chatbot com IA Zhoe - Z-API`
- **Depois:** `[DEMO] Chatbot WhatsApp com IA - Portfolio`

### 2. Sticky Note de Demonstração

Adicionado um sticky note no início explicando:
- Que é uma versão de demonstração
- Funcionalidades demonstradas
- Limitações da versão demo
- Instruções para uso

### 3. Prompt da IA Simplificado

O prompt do agente de IA foi:
- Substituído por uma versão genérica/template
- Removidos detalhes específicos do negócio (fluxos de atendimento)
- Mantida a estrutura para demonstrar a arquitetura
- Adicionadas instruções para personalização

**Motivo:** O prompt contém a lógica de negócio e conhecimento proprietário que representa capital intelectual.

### 4. Sticky Note de Documentação

O sticky note existente foi atualizado para:
- Remover referências específicas
- Indicar que é versão de portfólio
- Listar funcionalidades de forma genérica

---

## Estrutura do Workflow (Preservada)

```
1. ENTRADA
   └── Webhook (recebe mensagens WhatsApp)

2. VALIDAÇÃO
   ├── Filtro de callbacks
   ├── Filtro de grupos
   └── Detecção de origem (usuário/bot/humano)

3. PROCESSAMENTO DE MENSAGEM
   ├── Texto simples
   ├── Resposta a botão
   ├── Mensagem editada
   ├── Áudio (transcrição OpenAI)
   └── Imagem (análise de visão GPT-4)

4. GERENCIAMENTO DE ESTADO
   ├── Armazenamento em Redis
   ├── Timeout de conversa
   └── Detecção de abandono

5. INTELIGÊNCIA ARTIFICIAL
   ├── Agente LangChain
   ├── Memória de contexto (Redis)
   └── Validação de resposta

6. ENVIO DE RESPOSTA
   ├── Texto simples
   ├── Imagem/Vídeo/Áudio
   └── Botões interativos

7. AUDITORIA
   ├── Google Sheets (logs)
   └── Analytics de conversa

8. MONITORAMENTO
   ├── Verificação de status (agendada)
   └── Alertas por email
```

---
## Como Usar o Workflow Demo

1. **Importe** o arquivo `[DEMO] Chatbot WhatsApp IA - Portfolio.json` no n8n
2. **Configure** suas próprias credenciais:
   - Z-API ou Evolution API
   - Redis
   - OpenAI
   - Google Sheets (opcional)
   - Gmail (opcional)
3. **Personalize** o prompt do agente para seu negócio
4. **Configure** o webhook no seu provedor de WhatsApp
5. **Teste** com mensagens de exemplo

---

## Notas Importantes

- Este workflow é **apenas para demonstração de habilidades técnicas**
- Para implementação completa, é necessário desenvolver os prompts e fluxos específicos
- A estrutura e arquitetura demonstram boas práticas de desenvolvimento n8n
- O código de processamento (JavaScript) foi preservado para demonstrar técnicas avançadas
