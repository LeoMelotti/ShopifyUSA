# ShopifyUSA – AI Context (Fonte Única da Verdade)

## Projeto
- Loja Shopify B2B da Eleven Fragrances (EUA)
- Tema base: Concept by RoarTheme (v5.2.0)
- Tema customizado (não usar como stock theme)

## Stack
- Shopify Online Store 2.0
- Liquid
- JavaScript Vanilla (ES6+)
- CSS custom (override do theme)

## Regras Importantes do Tema Concept
- Respeitar estrutura original do tema Concept
- Evitar alterar core sections do tema quando possível
- Customizações preferencialmente via:
  - sections custom
  - templates JSON
  - snippets reutilizáveis
- CSS sobrescrito via assets/theme.css
- Variáveis e fontes em snippets/css-variables.liquid

## Padrões Visuais Obrigatórios
- Fontes:
  - BC Sklonar Light (logo)
  - Elza Bold (títulos)
  - Elza Regular (body)
  - Richmond Display (subtítulos)
- Paleta fixa conforme brandbook Eleven Fragrances
- Estética premium, B2B, limpa

## Regras de Código
- Proibido jQuery
- Proibido inline JS
- JavaScript sempre em assets
- Nada de lógica complexa em Liquid
- Usar metafields sempre que possível

## Estrutura Atual Importante
- Homepage construída via index.json
- Templates custom:
  - page.how-it-works.json
  - page.for-business.json
  - page.find-your-scent.json
  - page.custom-fragrances.json
- Sections custom:
  - quiz-find-your-scent.liquid
  - custom-fragrance-form.liquid

## Estado Atual
- Tema funcional
- Identidade visual completa aplicada
- Customizações avançadas já implementadas
- Novas features devem respeitar tudo acima

## Instruções para IA
- Nunca sugerir trocar de tema
- Nunca reestruturar arquitetura sem perguntar
- Sempre considerar que este projeto já está avançado
- Qualquer mudança deve ser incremental
