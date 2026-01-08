# AI_STATE.md - Eleven Fragrances Shopify USA
> Checkpoint criado em: 07/01/2026
> Última atualização: Baseado no histórico completo da conversa

---

## 📋 CONTEXTO DO PROJETO

### Sobre a Empresa
- **Nome:** Eleven Fragrances LLC (Florida, USA)
- **Modelo:** B2B scent marketing - aluguel de difusores + assinatura de fragrâncias
- **Clientes-alvo:** Hotéis, clínicas, escritórios, lojas, restaurantes, academias
- **CEO:** Leo (opera do Brasil)
- **Sales Rep:** Mateus Lopes (Orlando)
- **Site:** https://eleven-fragrances.myshopify.com/
- **Plataforma:** Shopify (tema Concept/Dawn modificado)

### Modelos de Negócio Definidos
| Modelo | Descrição | Cobertura |
|--------|-----------|-----------|
| **Shop** | Venda única de máquinas + fragrâncias | Nationwide USA |
| **Subscription** | Máquina grátis + fragrância mensal | Nationwide USA |
| **Premium Service** | Instalação + manutenção presencial | Central Florida only |

---

## 🏗️ DECISÕES ARQUITETURAIS TOMADAS

### 1. Estrutura de Páginas
```
Menu Principal:
├── Home
├── How It Works
├── Diffusers (collection)
├── Fragrances (collection)
├── Find Your Scent ← Quiz interativo (em desenvolvimento)
├── For Business
└── Custom Fragrances ← Formulário B2B (pronto)

Footer:
├── FAQ
├── Shipping & Delivery
├── Service Areas (mapa Central Florida)
├── Terms of Service
└── Privacy Policy
```

### 2. Sistema de Cores (DEFINITIVO)
```css
--primary: #1C423E;        /* Verde escuro principal */
--primary-hover: #245751;  /* Verde escuro hover */
--accent: #C9A66B;         /* Dourado - destaques/CTAs */
--background: #FAF8F5;     /* Creme - fundo */
--text: #071110;           /* Texto principal */
--muted: #6B7C7A;          /* Texto secundário */
--border: #E8E4DF;         /* Bordas */
```

### 3. Tipografia (DEFINITIVO)
- **Fonte principal:** Cormorant Garamond (serifada, elegante)
- **Fonte secundária:** Sans-serif para labels/botões
- **Estilo:** Uso de *itálico* para elegância em títulos
- **Exemplo:** "Create Your *Signature* Scent"

### 4. Padrão Visual dos CTAs
```css
/* Botão Primário */
padding: 18px 48px;
background: var(--accent);  /* Dourado */
color: var(--primary);      /* Verde escuro */
font-size: 12px;
letter-spacing: 2px;
text-transform: uppercase;
```

### 5. Estrutura do Quiz - Sistema de Matching
- **5 dimensões de perfil:** energia, temperatura, sofisticação, intensidade, mood
- **Escala:** 1-10 para cada dimensão
- **Algoritmo:** Distância Euclidiana para match com fragrâncias
- **Match mínimo garantido:** 75-78%

---

## 📁 PADRÕES DE CÓDIGO DEFINIDOS

### Estrutura de Sections (Shopify Liquid)
```liquid
{{ 'section-NOME.css' | asset_url | stylesheet_tag }}

<style>
  .PREFIXO-page {
    --PREFIXO-primary: {{ section.settings.color_primary }};
    /* CSS variables configuráveis */
  }
</style>

<div class="PREFIXO-page">
  <!-- Conteúdo HTML -->
</div>

<script>
  // JavaScript
</script>

{% schema %}
{
  "name": "Nome da Section",
  "settings": [
    /* Configurações editáveis no Customize */
  ],
  "blocks": [
    /* Blocos repetíveis */
  ],
  "presets": [
    {
      "name": "Nome da Section"
    }
  ]
}
{% endschema %}
```

### Templates JSON (page.NOME.json)
```json
{
  "sections": {
    "main": {
      "type": "NOME-DA-SECTION",
      "settings": {
        /* Valores default ou configurados */
      },
      "blocks": {
        /* Blocos com settings */
      },
      "block_order": ["block-1", "block-2"]
    }
  },
  "order": ["main"]
}
```

### Convenções de Nomenclatura
- **Sections:** `nome-descritivo.liquid` (ex: `custom-fragrance-form.liquid`)
- **Templates:** `page.nome-da-pagina.json` (ex: `page.custom-fragrances.json`)
- **CSS classes:** Prefixo único por section (ex: `.cf-` para custom-fragrance)
- **IDs no schema:** Usar snake_case (ex: `webhook_url`, `color_primary`)

### Tratamento de Apóstrofos em Liquid
```liquid
<!-- ❌ ERRADO - causa erro de sintaxe -->
{{ section.settings.text | default: 'it's perfect' }}

<!-- ✅ CORRETO - usar "it is" ou aspas duplas no JSON -->
{{ section.settings.text | default: 'it is perfect' }}
```

---

## ✅ O QUE ESTÁ PRONTO

### 1. Formulário B2B Custom Fragrances
**Arquivos:**
- `sections/custom-fragrance-form.liquid` (1430 linhas)
- `templates/page.custom-fragrances.json`

**Estrutura da página:**
| Seção | Conteúdo |
|-------|----------|
| Hero | "Create Your Signature Scent" com CTA |
| Benefits | 3 cards: Exclusivity, Emotional Connection, Competitive Edge |
| Process | 4 steps: Discovery → Development → Refinement → Launch |
| Form | Formulário completo com todos os campos |
| FAQ | 6 perguntas frequentes com accordion |
| CTA Final | Call-to-action |

**Campos do formulário:**
- Nome, Email, Telefone
- Nome da empresa
- Indústria (dropdown: Hotel, Medical, Retail, Fitness, etc.)
- Número de locações
- Tamanho do espaço
- Descrição da marca/identidade (textarea)
- Preferências de aroma (textarea)

**Features:**
- ✅ 100% editável pelo Shopify Customizer
- ✅ Suporta webhook n8n
- ✅ FAQ customizável via blocks
- ✅ Design alinhado com identidade da marca
- ✅ Responsivo mobile/desktop
- ⚠️ Pendente: Ajustar formatação para consistência com homepage

### 2. Templates de Páginas Base
- `templates/index.json` - Homepage
- `templates/collection.json` - Coleções
- `templates/collection.diffusers.json`
- `templates/collection.fragrances.json`
- `templates/page.how-it-works.json`
- `templates/page.for-business.json`

### 3. Documentação
- `QUIZ-BRIEFING-COMPLETO.md` - Briefing completo do quiz
- `GUIA-QUIZ.md` - Guia de instalação do quiz
- `IMPLEMENTATION-GUIDE.md` - Guia geral de implementação
- `INSTALACAO.md` - Instruções de instalação

---

## 🔄 O QUE ESTÁ EM ANDAMENTO

### Quiz "Find Your Scent"
**Status:** MÚLTIPLAS VERSÕES CRIADAS, NENHUMA APROVADA

**Versões criadas:**
| Arquivo | Problema |
|---------|----------|
| `quiz-find-your-scent.liquid` | Versão inicial - muito básica |
| `quiz-section.liquid` | Perguntas diretas demais |
| `quiz-premium.liquid` | Foco em perfume pessoal (deveria ser ambiente) |
| `quiz-ambient-v2.liquid` | Fotos não faziam sentido |
| `quiz-eleven-v3.liquid` | Visual não impactante |
| `quiz-pura-style.liquid` | Bug no step 2 - layout quebrado |
| `quiz-fixed.liquid` | Ainda com problemas visuais |

**Requisitos pendentes:**
1. Perguntas lúdicas e sutis (não diretas)
2. Imagens que conversam com as perguntas
3. Layout fullscreen inspirado na Pura
4. Código limpo e bem estruturado
5. Consistência visual com o site
6. Testar TODOS os steps antes de entregar

**Referência visual:** https://pura.com/pages/fragrance-discovery-quiz/feeling

### Ajustes de Formatação
- Formulário B2B precisa manter padrão visual da homepage
- Integrar perguntas do Google Forms de briefing olfativo

---

## 🚫 O QUE NÃO DEVE SER ALTERADO

### 1. Identidade Visual
- Cores definidas (#1C423E, #C9A66B, #FAF8F5)
- Tipografia Cormorant Garamond com itálicos
- Estilo sofisticado e premium

### 2. Sistema de Matching do Quiz
- 5 dimensões do perfil (energia, temperatura, sofisticação, intensidade, mood)
- Algoritmo de distância Euclidiana
- Estrutura de DNA das fragrâncias

### 3. Estrutura de Preços Definida
| Máquina | Coverage | Buy | Subscribe 6mo |
|---------|----------|-----|---------------|
| Pirad | 1,300 sq ft | $79 | $49.99/mo |
| Square | 6,500 sq ft | $129 | $119.99/mo |
| Design | 1,600 sq ft | $349 | $159.99/mo |
| Tower | 17,500 sq ft | $449 | $269.99/mo |
| Pro 2 | 80,000 sq ft | $899 | $999.99/mo |

### 4. Modelo de Negócio
- Subscription com compromisso mínimo de 6 meses
- Premium Service exclusivo para Central Florida
- Desconto de 15% para planos de 12 meses

### 5. Padrão de Sections do Shopify
- Schema com presets para aparecer no Customize
- CSS variables para cores configuráveis
- Suporte a webhook n8n nas sections de formulário

---

## 🛠️ CONFIGURAÇÕES TÉCNICAS

### Webhook n8n
```javascript
// Endpoint configurável no schema
{
  "type": "url",
  "id": "webhook_url",
  "label": "Webhook URL (optional)",
  "info": "n8n webhook to save responses"
}
```

### Dados enviados pelo Quiz
```javascript
{
  email: "usuario@email.com",
  name: "Nome",
  profile: { energia: 5, temperatura: 7, ... },
  result: "Warm Amber",
  match: 92,
  timestamp: "2026-01-06T..."
}
```

### Dados enviados pelo Formulário B2B
```javascript
{
  name: "Nome",
  email: "email@empresa.com",
  phone: "(xxx) xxx-xxxx",
  company: "Nome da Empresa",
  industry: "Hotel",
  locations: "1",
  space_size: "5001-10000",
  brand_description: "Descrição...",
  scent_preferences: "Preferências...",
  timestamp: "2026-01-07T..."
}
```

### Appstle Subscriptions
- Já configurado na loja
- URL de assinatura: `/products/PRODUTO?selling_plan=subscription`

---

## 📝 NOTAS IMPORTANTES

### Contexto do Cliente
- Interface Shopify em português (Brasil)
- Quiz e site em inglês (mercado americano)
- Leo prefere código limpo e bem estruturado
- Feedback frequente sobre visual - precisa ser impactante

### Erros Comuns a Evitar
1. **Apóstrofos em defaults Liquid** - usar "it is" em vez de "it's"
2. **Nome do type no JSON** - deve ser EXATAMENTE igual ao nome do arquivo .liquid
3. **Section deve existir ANTES de criar template** que a referencia
4. **Imagens genéricas** - devem conversar com o contexto da pergunta

### Interface Shopify (PT-BR)
- "Themes" = "Temas"
- "Edit code" = "Editar código"
- "Sections" = "Seções"
- "Pages" = "Páginas"
- "Add a new section" = "Adicionar uma nova seção"

---

## 📂 ARQUIVOS DO PROJETO

### Sections (prontas para usar)
```
sections/
├── custom-fragrance-form.liquid  ✅ PRONTO
└── quiz-find-your-scent.liquid   🔄 EM REVISÃO
```

### Templates (prontos para usar)
```
templates/
├── index.json                    ✅ PRONTO
├── collection.json               ✅ PRONTO
├── collection.diffusers.json     ✅ PRONTO
├── collection.fragrances.json    ✅ PRONTO
├── page.how-it-works.json        ✅ PRONTO
├── page.for-business.json        ✅ PRONTO
├── page.custom-fragrances.json   ✅ PRONTO
└── page.find-your-scent.json     🔄 AGUARDANDO QUIZ
```

### Versões do Quiz (para referência)
```
quiz-versions/
├── quiz-find-your-scent.liquid   ❌ Básico demais
├── quiz-section.liquid           ❌ Direto demais
├── quiz-premium.liquid           ❌ Foco errado (perfume pessoal)
├── quiz-ambient-v2.liquid        ❌ Fotos sem sentido
├── quiz-eleven-v3.liquid         ❌ Sem impacto visual
├── quiz-pura-style.liquid        ❌ Bug no step 2
└── quiz-fixed.liquid             ❌ Ainda com problemas
```

---

## 🎯 PRÓXIMOS PASSOS RECOMENDADOS

1. **Quiz "Find Your Scent"**
   - Criar do zero com código limpo
   - Seguir referência da Pura
   - Testar TODOS os steps
   - Garantir responsividade

2. **Formulário B2B**
   - Ajustar formatação para consistência com homepage
   - Integrar perguntas do Google Forms de briefing

3. **Fragrâncias**
   - Definir as 11 fragrâncias reais
   - Criar DNA de matching para cada uma
   - Atualizar array no quiz

---

*Checkpoint gerado automaticamente a partir do histórico completo da conversa.*
