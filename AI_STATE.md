# AI_STATE.md — Eleven Fragrances Shopify USA
Última atualização: 07/01/2026

## Estado Atual (o que está pronto)
- Quiz "Find Your Scent" v2 FINALIZADO:
  - `sections/quiz-find-your-scent.liquid`
  - `templates/page.find-your-scent.json`
  - 5 steps (4 perguntas + captura de email), matching por DNA (5 dimensões) e webhook n8n opcional
  - 11 fragrâncias padrão (placeholders) + suporte a fragrâncias custom por blocks no Customizer
- Formulário B2B Custom Fragrances v3 FINALIZADO:
  - `sections/custom-fragrance-form-v3.liquid`
  - Briefing olfativo completo (5 seções, 15+ campos), FAQ, responsivo, webhook n8n no Customizer

## Integrações (status)
- n8n: workflow EF-14 “Olfactory Briefing (Shopify)” IMPORTADO, porém pendente configuração:
  - configurar Email (Notify Leo)
  - configurar Trello (Create Card)
  - configurar Google Sheets (Log) + criar aba `12_BRIEFINGS` na planilha
  - copiar Production URL do Webhook e colar no Customizer do formulário
  - ativar e testar ponta-a-ponta

## Pendências imediatas (prioridade)
1. Finalizar EF-14 no n8n (email + trello + sheets + ativar + testar)
2. Integrar webhook do formulário no Shopify Customizer (production URL)
3. Substituir as 11 fragrâncias placeholders do quiz por fragrâncias/produtos reais (via blocks no Customizer)
4. Trocar imagens do quiz (step images) por imagens próprias (via Customizer)
5. Ajustes de consistência visual: garantir que páginas e o formulário B2B sigam o mesmo padrão de spacing/typography/CTAs da homepage

## Arquivos relevantes
- Quiz: `sections/quiz-find-your-scent.liquid` | `templates/page.find-your-scent.json`
- B2B v3: `sections/custom-fragrance-form-v3.liquid`
- Workflow: `workflows/olfactory-briefing-workflow.json` (EF-14 importado)
