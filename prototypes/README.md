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

Primeira versão completa da página principal, com a marca da Phira (fundo `#141414`, texto creme `#FEEAD8`, fonte Satoshi, logótipo φ oficial).

Secções: hero animado · manifesto e oferta (piloto sem custo) · serviços por área · inteligência artificial (com exemplo animado de leitura de fatura) · método em 4 passos · caso de estudo · porquê nós · contacto.

- A espiral do hero roda no sentido do símbolo φ e termina com o símbolo desenhado.
- A Satoshi vem da Fontshare (`api.fontshare.com`); Figtree fica como substituto.
- Por preencher: `[EMAIL]` e `[EMAIL DE CONTACTO]`; confirmar com o cliente o caso da construtora antes de publicar.
