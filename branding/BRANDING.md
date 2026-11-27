# Phira Software — branding

Fonte única do branding do site, para usar no código e para o mock-up no Figma. `tokens.json` tem as cores, a tipografia, o espaço e os raios (cada token com a nota de uso); `tokens.css` são as mesmas variáveis em CSS; `logos/` tem o logótipo (tinta creme, nunca se recolore). O mesmo conteúdo existe como design system no Claude, "Phira Software · Branding".

---

Escreve para quem gere uma empresa: frases curtas, concretas, sem jargão. Diz o que fazemos antes de dizer como. Português de Portugal e inglês, sempre em par: cada texto PT tem o seu EN, com o mesmo sentido e o mesmo comprimento aproximado.

## Conteúdo

- Estrutura da mensagem: **Integrar, Organizar, Extrair**. Integramos as ferramentas e os processos de cada área, organizamos os dados para os poder cruzar, e extraímos KPIs, dashboards, modelos financeiros e IA. O software, a automação e a IA aparecem no fim, nunca na abertura.
- Títulos afirmam, não perguntam. Exemplos reais: "Uma visão clara do seu negócio.", "Um sistema onde os dados percorrem toda a empresa.", "Integramos ferramentas e processos.", "Organizamos os dados.", "Dos dados, a visão do negócio."
- Máximo de uma ideia por frase. Se uma frase precisa de "e" duas vezes, divide-a.
- Não escrevas "soluções à medida", "ecossistema" nem "transformação digital". Diz a coisa concreta: o ERP, a folha de Excel, o email, a fatura.
- Números e nomes de ferramentas em `label` (mono, maiúsculas). Valores ilustrativos levam a etiqueta "ilustrativo".

## Cor

Fundo escuro, texto creme, e um subtom suave e mate por setor. O fundo é `bg`, os cartões são `surface`, o que está dentro de um cartão é `surface-raised`. O texto é `text`; o secundário é `text-dim`.

**O padrão dos tons.** Cada caixa tem no máximo UM tom. O tom entra em quatro intensidades, sempre as mesmas, e nunca mais forte do que isto:

| Intensidade | Token | Onde |
| --- | --- | --- |
| Cheio | `slate`, `sage`, `sand`, `clay`, `mauve`, `teal` | Ponto de 8px, ícone, linha fina de gráfico, etiqueta pequena, separador selecionado (com `on-tone` por cima) |
| Tinta | `<tom>-wash` | Fundo de uma caixa de setor, quadrados do hero |
| Brilho | `<tom>-glow` | Gradiente de canto: `radial-gradient(120% 140% at 100% 0%, var(--<tom>-glow), transparent 62%)` sobre `surface` |
| Contorno | `<tom>-line` | Borda da caixa, no lugar de `line` |

Regras:
- Atribui os tons por esta ordem e sem repetir numa mesma vista: `slate`, `sage`, `sand`, `clay`, `mauve`, `teal`. No site: Integrar `slate`, Organizar `sage`, Extrair `sand`. Hero: Supply chain `slate`, Atendimento `sage`, Faturação `sand`, Vendas `clay`, Equipas `mauve`. Casos: Construção `clay`, Distribuição `slate`, Indústria `teal`, Restauração `sand`, Imobiliário `sage`, Serviços `mauve`.
- O tom nunca é um fundo grande e liso, nunca é texto corrido, e nunca é saturado mais do que a tabela. O texto de um cartão continua `text` e `text-dim`; só uma legenda pequena pode usar o tom.
- Não há gradientes entre dois tons, nem sombras.
- Para um tom novo, escolhe um mate claro (luminosidade parecida, contraste de pelo menos 6:1 com `bg`) e cria os seus `-wash`, `-glow` e `-line` a 7%, 13% e 24%.
- Foco: contorno de 2px em `text` com 3px de afastamento. Botão principal: fundo `text`, texto `bg`, `radius-pill`. Botão secundário: transparente com borda `line-strong`.

## Tipografia

Tudo em `sans` (Satoshi; Figtree quando a Satoshi não carrega), peso 500 nos títulos, espaçamento -0.025em. Etiquetas e sobretítulos em `mono` (JetBrains Mono), maiúsculas, `label` e `eyebrow`. Títulos com `display`, `h1` e `h3`; frase de apoio com `lead` em `text-dim`; corpo com `body`.

## Forma e ritmo

- O layout assenta na proporção 1:1,618. O hero é uma espiral dourada: cada setor é um quadrado, o maior é o principal, e a curva em `text` percorre-os do maior ao menor.
- Raios: `radius-lg` em cartões e passos, `radius-md` em caixas internas, `radius-sm` em etiquetas pequenas, `radius-pill` em botões e separadores.
- Espaço: `space-1` a `space-4` dentro das secções, `space-5` como margem lateral máxima.

## Logótipo

O logótipo é sempre `text` (#feead8) sobre `bg` ou `surface`. Nunca muda de cor: sem tons, sem transparência, sem gradiente, sem contorno. Altura de 26px no topo e 22px no rodapé. Usa `phira-wordmark.svg` com o nome e `phira-mark.svg` (o phi) quando só cabe o símbolo. Os logótipos de clientes nos casos mantêm as suas próprias cores e nunca levam o tom do setor.

## Ícones

Ícones de linha fina: 16px, traço de 1,4px, pontas redondas, sem preenchimento, sem emoji. A cor é `text`, ou o tom do setor quando o ícone marca esse setor.
