# CLAUDE.md — Rails Girls São Paulo (railsgirls.com.br)

Site mantido por um grupo voluntário com pouco tempo. A regra principal de qualquer mudança aqui é: **o site precisa continuar publicando sem que ninguém mexa nele por mais de um ano.** Na dúvida entre "mais moderno" e "menos coisa que pode quebrar", escolha a segunda.

## Stack (não mudar sem discussão no grupo)

- GitHub Pages com **build nativo de Jekyll** (gem `github-pages`, `~> 232`). Sem GitHub Actions.
- Só plugins da allowlist do GitHub Pages (`jekyll-seo-tag`, `jekyll-sitemap`). Nada de plugin customizado.
- **Proibido:** npm, Node, package.json, bundlers JS, Tailwind com build, Bootstrap, jQuery, qualquer framework JS.
- HTML semântico + CSS moderno vanilla (custom properties, grid, flexbox, `clamp()`). JS só quando não há alternativa nativa, e sempre respeitando `prefers-reduced-motion`.
- O `Gemfile` existe só para preview local. `Gemfile.lock` fica no `.gitignore`.

## Estrutura

- `_data/evento.yml` — **única fonte de verdade da edição atual** (status, data, local, link de inscrição). Atualizar edição = editar só esse arquivo. Ver `MANUTENCAO.md`.
- `_data/patrocinadores.yml`, `_data/apoiadores.yml`, `_data/edicoes_anteriores.yml`, `_data/impacto.yml`, `_data/depoimentos.yml`, `_data/organizadoras.yml`, `_data/faq.yml`, `_data/social.yml` — todo o conteúdo variável da home. Editar esses arquivos, não o HTML, para atualizar conteúdo.
- `_layouts/default.html`, `_includes/*.html` — layout e uma include por seção da home (ver ordem abaixo).
- `index.html` — home; monta as includes na ordem definida.
- `assets/css/`, `assets/img/`, `assets/js/` — estilos, imagens e o pouco JS do layout novo.
- Páginas de edições antigas (`saopaulo2019.html`, `saopaulo2024.html`, `saopaulo2024-2-edicao.html`, `speaker-details.html`) e os assets que elas usam (`css/style.css`, `js/main.js`, `lib/`, parte de `img/`: `logo.png`, `gallery/`, `speakers/`, `supporters/`, favicons) — **arquivo histórico congelado**. Não editar, não adicionar front matter, não apagar nada que elas referenciam. (`speaker-details.html` já tem um link quebrado pré-existente para `contactform/contactform.js` — não é para consertar; está fora do escopo do congelamento.)
- `CNAME` — não tocar.
- `plan/` — material de referência de design (screenshots, textos, decisões de implementação). Ignorado pelo Jekyll (`exclude` em `_config.yml`) e pelo git (`.gitignore`). É referência de **layout/estrutura**, não fonte de verdade de conteúdo publicado — screenshots antigos podem ter data/local desatualizados.

## Como verificar qualquer mudança

```sh
bundle install
bundle exec jekyll serve
```

Conferir: a home em cada `status` do `evento.yml`, as páginas do arquivo histórico com CSS/imagens carregando, e o layout em largura de celular.

## Ordem das seções da home

1. Hero (logo, bloco de edição dinâmico, carrossel de fotos)
2. Info do evento (workshop + local)
3. Banner de missão institucional
4. Patrocinadores/apoiadores por tier (Ruby, Diamante, Safira, Esmeralda, Apoio)
5. Edições anteriores
6. Nosso impacto (stats)
7. Depoimentos
8. Empresas apoiadoras + CTA "seja um apoiador"
9. Organizadoras
10. Redes sociais
11. CTA final
12. FAQ
13. Footer (institucional + redes + link para arquivo histórico + copyright)

## Bloco de edição (`_data/evento.yml`, campo `status`)

- `sem_data`: texto atemporal, sem nenhuma data, aponta para as redes sociais. Precisa continuar fazendo sentido mesmo se ninguém mexer por dois anos.
- `inscricoes_abertas`: data, local e botão para `link_inscricao`.
- `encerradas`: data e local, sem botão, aviso de inscrições encerradas.
- `realizado`: agradecimento e convite para acompanhar as próximas edições.

Nenhum outro lugar da home tem data ou ano escrito à mão, exceto o ano do copyright no footer, gerado com `site.time`.

## Tokens de design

Extraídos do site Framer ao vivo (`railsgirlssp.framer.website`) em 2026-09-21, direto do CSS computado — não foi copiado HTML/CSS do Framer, só lidos os valores de cor/fonte.

**Cores**
```css
--color-primary: #911802;      /* vermelho principal: títulos, botões, ícones */
--color-primary-dark: #490606; /* footer, banner CTA escuro */
--color-acento: #d63a2f;       /* botão do CTA final */
--color-text: #2b2b2b;
--color-text-muted: #757575;
--color-bg-soft: #fff0f0;      /* cards e seções destacadas */
--color-bg-soft-alt: #ffdddd;
--color-gray: #a8a8a8;
--color-bg-neutro: #e9e6e3;    /* barra de copyright do footer */
--color-white: #ffffff;
```

**Tipografia** (Google Fonts, gratuitas — carregadas via `<link>`, sem build):
- Títulos: `Baloo 2`, peso 700. No Framer os tamanhos são fixos (96/64/50px desktop) — aqui usamos `clamp()` para responsividade real.
- Corpo: `Inter`.

**Outros:** `border-radius` de 12px em cards, ~40px em botões (pill), variações pontuais em outros elementos (8px, 20px, 28px).

## Animação

Decisão: manter uma sugestão de movimento (o Framer usa reveal-on-scroll), mas sem biblioteca. Fade/slide sutil via CSS (`opacity` + `transform` com `transition`), disparado por um `IntersectionObserver` vanilla pequeno (`assets/js/reveal.js`). Tudo dentro de `@media (prefers-reduced-motion: no-preference)` — com a preferência de movimento reduzido ativada, os elementos aparecem direto, sem transição alguma. Sem parallax, sem lib de motion, sem JS pesado.

## Imagens

Convenção: os arquivos em `assets/img/...` já existem com o nome final que devem ter; enquanto o conteúdo real não é exportado do Framer, o arquivo contém um placeholder simples (SVG com rótulo). Único placeholder restante: `assets/img/placeholders/og-image.svg` (imagem de Open Graph, referenciada em `_config.yml`).
