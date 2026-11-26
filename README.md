# Phira Software · site

Site da consultora de software da Phira Ventures: software à medida, automação de processos e IA para empresas.

> **Estado:** protótipo aprovado em `prototypes/site/index.html`. O passo seguinte é reconstruí-lo em Astro para produção, seguindo este documento. O protótipo é a referência visual e de comportamento, não o código final.

---

## 1. Stack recomendada

| Camada | Escolha | Porquê |
|---|---|---|
| Framework | **Astro** (output estático) | HTML gerado no build, zero JS por defeito, ilhas de JS só onde há animação |
| Estilos | CSS por componente (Astro `<style>`) + tokens globais | Sem framework CSS pesado; os tokens já estão definidos no protótipo (`:root`) |
| Conteúdo | Astro Content Collections (Markdown/JSON) | Casos de estudo, serviços e textos editáveis sem mexer em componentes |
| Idiomas | Rotas `/pt/` e `/en/` com i18n nativo do Astro | Cada língua é uma página real, indexável pelo Google |
| Alojamento | **Vercel** | Pré-visualização automática por branch, CDN, HTTPS |
| Métricas | Vercel Web Analytics ou Plausible | Sem cookies, sem banner de consentimento |

## 2. Estrutura de pastas proposta

```
src/
  components/
    Nav.astro
    Hero/                 ← animação da espiral (ilha JS)
      Hero.astro
      hero.ts
    Connect.astro         ← Ligar → Organizar → Construir + painel de ligações (ilha JS)
    Services.astro
    AiFlow.astro          ← diagrama da IA (ilha JS)
    Cases/
      Cases.astro         ← separadores por setor + slider
      DemoInvoice.astro   ← demo Draft-in (ilha JS)
      DemoContent.astro   ← demo Lunis (ilha JS)
    Method.astro
    Contact.astro
    Footer.astro
  content/
    cases/                ← um ficheiro por caso (setor, citação, KPIs, demo)
    services/
  i18n/
    pt.json
    en.json
  layouts/
    Base.astro            ← <head>, SEO, fontes, tokens
  pages/
    pt/index.astro
    en/index.astro
    pt/casos/[slug].astro ← página própria por caso (bom para SEO)
    en/cases/[slug].astro
public/
  fonts/                  ← Satoshi woff2 (400, 500, 700), só latim
  og/                     ← imagens de partilha 1200×630 por página
  robots.txt
```

### Adicionar um caso de estudo

Criar `src/content/cases/<nome>.md` com: setor (`construcao`, `imobiliario`, …), citação e autor, KPIs, e qual demo mostrar. Os separadores por setor contam os casos sozinhos; setores sem casos mostram "Em breve".

## 3. Desempenho

### Objetivos

| Métrica | Objetivo (telemóvel, 4G) |
|---|---|
| Lighthouse Performance | ≥ 90 |
| LCP (maior elemento visível) | < 2,5 s |
| CLS (saltos de layout) | < 0,1 |
| INP (resposta a cliques) | < 200 ms |
| JS total na página inicial | < 60 KB comprimido |

### O que fazer

**Fontes**
- Alojar a Satoshi em `public/fonts/` (woff2, só subconjunto latim, pesos 400/500/700). Não usar a CDN da Fontshare em produção.
- `<link rel="preload">` só para o peso usado nos títulos. `font-display: swap` com um fallback de métricas parecidas (`size-adjust`) para não haver salto de texto.
- Remover a Figtree e a JetBrains Mono do Google se a Satoshi for suficiente; se a mono ficar, alojá-la também.

**JavaScript**
- Cada animação é uma ilha Astro com `client:visible`: só carrega quando a secção aparece no ecrã.
- O ciclo de animação do hero (`requestAnimationFrame`) tem de parar quando o hero sai do ecrã (IntersectionObserver) e quando o separador fica em segundo plano. No protótipo corre sempre.
- As demos (fatura, Lunis, diagrama IA, painel de ligações) já param fora do ecrã no protótipo; manter isso.
- Respeitar `prefers-reduced-motion`: mostrar o estado final, sem animação (já existe no protótipo).
- Sem bibliotecas de animação; tudo é CSS + JS simples.

**Traduções**
- No protótipo o inglês é trocado por JavaScript depois de carregar. Em produção isso desaparece: cada língua é gerada no build a partir de `i18n/*.json`.

**Layout e imagens**
- Reservar sempre a altura dos blocos animados (hero, demos) para não haver saltos (CLS).
- O hero ocupa ~600vh de scroll; garantir que o primeiro ecrã aparece sem esperar pelo JS (texto e legenda em HTML estático).
- Imagens futuras (logótipos de clientes, fotografias): AVIF/WebP com `<Image>` do Astro, `width`/`height` definidos, `loading="lazy"` abaixo da dobra.

**Medir**
- Lighthouse em cada pull request (Vercel mostra-o na pré-visualização, ou GitHub Action `treosh/lighthouse-ci-action`).
- Depois de publicar: relatório Core Web Vitals no Google Search Console.

## 4. SEO técnico (checklist)

- [ ] `/pt/` e `/en/` com `<link rel="alternate" hreflang="pt-PT">`, `hreflang="en"` e `x-default`.
- [ ] `<title>` e `<meta name="description">` próprios em cada página e língua.
- [ ] Imagem Open Graph 1200×630 por página (partilhas no LinkedIn e WhatsApp).
- [ ] `sitemap.xml` (`@astrojs/sitemap`) e `robots.txt`.
- [ ] Dados estruturados JSON-LD: `Organization` / `ProfessionalService` (nome, morada Lisboa, contacto, `parentOrganization` Phira Ventures).
- [ ] Um só `<h1>` por página; títulos de secção em `<h2>`.
- [ ] Página própria por caso de estudo (`/pt/casos/draft-in`) e, mais tarde, por serviço e por setor.
- [ ] URLs canónicos e redireção do domínio sem/com `www`.
- [ ] Ligar o domínio ao Google Search Console e submeter o sitemap.

## 5. Acessibilidade

- Contraste do creme sobre `#141414` já passa AA; manter os tokens.
- Animações com alternativa estática (`prefers-reduced-motion`).
- Navegação por teclado no slider de casos, separadores de setor e botão PT/EN (já existe no protótipo).
- `aria-label` nas animações decorativas a descrever o que mostram.

## 6. Fluxo de trabalho

- `main` → o que está publicado no domínio.
- Uma branch por alteração (`caso-gesportas`, `secao-ia`, …) com pull request. A Vercel gera um link de pré-visualização para cada uma.
- Merge para `main` só depois de revisto.

## 7. Por confirmar antes de publicar

- [x] Email de contacto: tiago@phira.ventures.
- [ ] Autorização da Draft-in: nome, citação do Pedro Gonçalves e "15+ horas por semana".
- [ ] Números da Lunis, sobretudo "+300% leads".
- [ ] Lista de ferramentas no painel "Ligamos o que já usam": manter só as que conseguimos ligar hoje.
- [ ] Domínio do site.
- [ ] Os números do hero e das demos são exemplos; decidir se levam a etiqueta "exemplo".

## 8. Protótipo

`prototypes/site/index.html` abre diretamente no browser. `?p=0.5` no URL fixa a animação do hero num ponto (0 = início, 1 = fim). Descrição das secções em `prototypes/README.md`.
