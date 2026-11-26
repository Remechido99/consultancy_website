# Protótipos

Experiências de design antes de montar o site final.

## hero-espiral

Hero animado da página principal. Página HTML única, sem dependências (só Google Fonts).

- O scroll controla a animação: peças de várias áreas da empresa (supply chain, atendimento, faturação, vendas, operações) encaixam em quadrados de proporção áurea, a espiral desenha-se até ao ponto central, aparece um painel ("visão clara") e termina no contorno da espiral do logótipo.
- A geometria (quadrados + espiral) é calculada em JS a partir do tamanho do palco: rectângulo áureo deitado no computador, em pé no telemóvel.
- `?p=0.5` no URL fixa a animação num ponto (útil para rever fases).
- Com "reduzir movimento" ativo no sistema, mostra só o estado final.
- A espiral do logótipo é provisória: trocar pelo SVG oficial da Phira.

Abrir localmente: abrir `hero-espiral/index.html` no browser.

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

Por confirmar antes de publicar:
- `[EMAIL]` e `[EMAIL DE CONTACTO]`.
- Autorização da Draft-in (nome, citação do Pedro e "15+ horas") e números da Lunis (sobretudo "+300% leads").
- Lista de ferramentas no painel "Ligamos o que já usam": manter só as que conseguimos ligar.
- Os números no hero e nas demos são exemplos ilustrativos.
