# VivaBem Saúde 

Landing page estática para uma clínica de saúde fictícia, feita em HTML, CSS e JavaScript puros — sem framework, sem build e sem backend.

## Como rodar

Não é um projeto Node/React, então não existe `npm install` nem `npm run dev`. Duas formas de abrir:

1. **Duplo clique** no `index.html` — abre direto no navegador.
2. **Servidor local** (evita restrições do navegador com caminhos de arquivo):
   ```
   python -m http.server 5500
   ```
   ou, se preferir usar Node sem instalar nada:
   ```
   npx serve .
   ```
   Depois acesse `http://localhost:5500`.

## Estrutura de arquivos

```
index.html   → estrutura e conteúdo da página
style.css    → todo o visual (cores, tipografia, layout, responsividade)
script.js    → menu mobile + comportamento do formulário
```

Só três arquivos, sem dependências externas além das fontes do Google Fonts e das imagens do Unsplash carregadas por URL.

## Funcionalidades

- **Menu fixo (sticky)** no topo, com fundo levemente translúcido (`backdrop-filter: blur`) que reage ao scroll.
- **Menu hamburger** no mobile: o `script.js` alterna uma classe `.open` no `<nav>` e atualiza `aria-expanded` no botão para leitores de tela.
- **Seções de âncora**: os links do menu (`#sobre`, `#servicos`, `#equipe`, `#contato`) rolam suavemente até a seção, via `scroll-behavior: smooth` no CSS.
- **Formulário 100% estático**: o `submit` é interceptado com `event.preventDefault()`, o formulário é limpo e uma mensagem de confirmação aparece na tela. Não há `action`, não há `fetch`, não há envio de dados para lugar nenhum — é só simulação visual, como pedido no briefing.
- **Layout assimétrico proposital**: em vez de grades de cards idênticos, a seção de serviços tem um item "destaque" com foto grande e três itens menores em lista; a equipe tem um card deslocado verticalmente; os diferenciais aparecem como lista horizontal com linha divisória, não como cards repetidos.

## Decisões de design (curiosidades)

- **Tipografia**: `Newsreader` (serifada, para títulos) + `Karla` (sem serifa, para o corpo). É uma combinação pouco comum de propósito — fugindo da dupla "serifa quente + sans genérica" que qualquer gerador de site tende a usar por padrão.
- **Paleta verde-sálvia**: três tons de verde (`#6E8F6C`, `#48633F`, `#2F4A31`) fazem o trabalho de cor primária, cor de destaque e cor de fundo escuro (rodapé e seção de diferenciais), evitando gradientes.
- **Formas orgânicas discretas**: a imagem do hero e a imagem da seção "Sobre" usam `border-radius` assimétrico (ex.: `130px 14px 14px 14px`) para fugir do cantinho arredondado uniforme de todo card genérico. Por trás da imagem do hero há uma forma bege sólida (`.hero-media-shape`), sem sombra pesada nem blur.
- **Sem ícones decorativos aleatórios**: os únicos ícones SVG usados (nos serviços e nos diferenciais) são inline no HTML, desenhados à mão em poucos traços — não vieram de uma biblioteca de ícones genérica.
- **Sem "eyebrow" em caixa alta**: os pequenos rótulos acima dos títulos (ex.: "Sobre a VivaBem") usam itálico na fonte serifada, não o clássico texto todo em maiúsculas espaçado que aparece em quase todo template.

## Acessibilidade

- `alt` descritivo em todas as imagens.
- Todos os campos do formulário têm `<label for>` associado.
- Foco de teclado visível (`:focus-visible`) em toda a página, inclusive no menu.
- HTML semântico: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<form>`.
- Respeita `prefers-reduced-motion`: quem desativa animações no sistema não vê transições.

## Responsividade

Dois breakpoints principais no CSS (`960px` e `720px`):
- Acima de 960px: layout em duas colunas nas seções de hero, sobre, serviços e contato.
- Entre 720px e 960px: as colunas viram uma só, mas o menu de topo ainda aparece por extenso.
- Abaixo de 720px: o menu vira hamburger, os campos "Cidade" e "Estado" do formulário empilham, e o espaçamento das seções diminui para caber melhor na tela.

## Imagens

Todas vêm do Unsplash, carregadas por URL direta (sem download local). Se algum link quebrar no futuro (Unsplash às vezes remove fotos), basta trocar a URL no `src` da tag `<img>` correspondente — cada uma já tem um `alt` explicando o que deveria aparecer ali.
