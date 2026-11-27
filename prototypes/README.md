# Protótipos

Experiências de design antes de montar o site final.

## site

Página principal completa, bilingue (PT/EN, botão na navegação; arranca em inglês se o browser não estiver em português). Marca Phira: fundo `#141414`, texto creme `#FEEAD8`, fonte Satoshi (Fontshare; Figtree como substituto), logótipo φ oficial.

Ordem das secções:

1. **Hero animado.** Os dados soltos fogem do rato (difíceis de agarrar); com o scroll encaixam nos quadrados áureos de cada área, cada área mostra os seus KPIs, os dados correm pela espiral até ao painel central e acaba no símbolo φ com "Ordem natural para a sua empresa". `?p=0.5` no URL fixa a animação num ponto.
2. **Software à medida.** Ligar → Organizar (dados cruzados entre áreas) → Construir, mais o painel animado "Ligamos o que já usam" (exemplos de ERP, faturação, ficheiros, email, banco, CRM, e-commerce, RH).
3. **Serviços** por área da empresa.
4. **IA.** "A IA adapta-se à sua empresa. Não o contrário." Diagrama animado fontes → dados centralizados → agentes → equipa, o que fazemos / não fazemos, e 4 agentes.
5. **Casos por setor.** Separadores por setor (`#construcao`, `#imobiliario`, …); setores sem caso mostram "Em breve". Casos atuais: Draft-in (citação do Pedro Gonçalves, KPIs, demo fatura → folha de obra) e Lunis.ai (KPIs, demo plano de conteúdos + WhatsApp).
6. **Método + confiança.** 4 passos em espiral (Compreender, Âmbito, Construção, Evolução) e "Construído por quem já construiu empresas. Com o apoio da Phira Ventures".
7. **Contacto.**

Para adicionar um caso: copiar um bloco `<div class="slide" … data-sector="…">` dentro de `#slider` e mudar o setor; os separadores contam os casos sozinhos.

Os números no hero e nas demos são exemplos ilustrativos.
