# Evolution API v2.3.7 — pacote para Render

Este pacote NÃO altera o código-fonte da Evolution API.
O Dockerfile usa diretamente a imagem oficial:

`evoapicloud/evolution-api:v2.3.7`

## Como subir no Render

1. Crie um repositório GitHub com estes arquivos.
2. No Render, clique em **New > Web Service**.
3. Conecte o repositório.
4. Environment: **Docker**.
5. Crie um PostgreSQL separado para a Evolution API.
6. Crie um Render Key Value/Redis.
7. Copie as variáveis de `.env.example` para **Environment Variables** no Render.
8. Troque `SERVER_URL` pela URL pública que o Render gerar.
9. Troque `AUTHENTICATION_API_KEY` por uma chave forte.
10. Configure `DATABASE_CONNECTION_URI` e `CACHE_REDIS_URI`.
11. Faça o deploy.

Depois abra:

`https://SEU-SERVICO.onrender.com/manager`

Crie a instância `mksan` e conecte o WhatsApp pelo QR Code.

## Integração com o MKSAN V13

No serviço do MKSAN configure:

```text
Atendimento__WhatsApp__Evolution__Enabled=true
Atendimento__WhatsApp__Evolution__BaseUrl=https://SEU-SERVICO-EVOLUTION.onrender.com
Atendimento__WhatsApp__Evolution__ApiKey=SUA_CHAVE_EVOLUTION
Atendimento__WhatsApp__Evolution__InstanceName=mksan
Atendimento__WhatsApp__Evolution__PublicNumber=55DDDNÚMERO
Atendimento__WhatsApp__Evolution__WebhookSecret=UM_SEGREDO_FORTE
```

No webhook da instância Evolution, use:

`https://SEU-MKSAN.onrender.com/api/atendimento/whatsapp/evolution?secret=UM_SEGREDO_FORTE`

Evento principal:

`MESSAGES_UPSERT`
