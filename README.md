

# Super Heroes Chat (n8n)

Fluxo do n8n que responde a perguntas sobre super-heróis e consulta uma API externa para trazer detalhes (nome, pontos fortes, origem, afiliações e imagem).

## Como funciona
- **Gatilho:** When chat message received.
- **Agente:** AI Agent com instruções em PT-BR para acionar uma tool de busca.
- **Modelo:** OpenAI Chat (`gpt-4.1-mini`).
- **Memória:** Simple Memory (janela curta de contexto).
- **Tool:** HTTP Request para `GET /search/{nome_heroi}` na SuperHero API.

> Dica: envie o **nome do herói em inglês** (ex.: `spider-man`, `wonder woman`) e **URL-encode** o parâmetro.

## Estrutura do fluxo
- Trigger → AI Agent  
- AI Agent ↔️ OpenAI Chat Model  
- AI Agent ↔️ Simple Memory  
- AI Agent ↔️ tool_buscar_heroi (HTTP)

## Requisitos
- n8n (Cloud ou self-hosted)
- Chave da OpenAI configurada nas **Credenciais**
- Token da SuperHero API **em credencial/variável** (não hardcode)

## Como rodar
1. Importe o arquivo `.json` do workflow no n8n.
2. Abra o **AI Agent** e confirme o **System Prompt**.
3. Abra a **tool_buscar_heroi** e substitua o token por variável (ex.: `{{$env.SUPERHERO_TOKEN}}`).
4. Teste no chat: `Fale do Spider-Man`.

## Segurança
- **Não** faça commit de tokens/segredos. Use credenciais/variáveis do n8n.
- Revise nodes HTTP para garantir que headers sensíveis não estejam no JSON.

## Versionamento
- Exporte sempre que alterar o fluxo e faça commit do `.json`.
- (Opcional) Automatize com `n8n export:workflow --backup` para versionar múltiplos fluxos.

  https://github.com/FilippeHarnack/<img width="1242" height="531" alt="Image" src="https://github.com/user-attachments/assets/35dd3067-dd50-41bf-826b-4e94652d9dfa" />
<img width="502" height="168" alt="Image" src="https://github.com/user-attachments/assets/73e91876-d8b8-4f71-9505-27a107b4e0f8" />
<img width="502" height="434" alt="Image" src="https://github.com/user-attachments/assets/3b6c4d93-603a-44c7-9ddf-c9f28f4a010d" />


<
