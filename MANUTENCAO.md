# Manutenção do site

## Como atualizar uma edição

Edite só o arquivo `_data/evento.yml`. O campo `status` controla o que aparece no topo da home.

### `status: sem_data`
Use quando não há data marcada. Mostra um texto atemporal apontando para as redes sociais — nenhum outro campo é exibido.
```yaml
status: sem_data
nome: Rails Girls São Paulo
data: 2026-10-17
horario: 9h até 19h
local: Vórtx
logo_local: /assets/img/parceiros/vortx.png
endereco: R. Gilberto Sabino, 215, 3o andar - Pinheiros, São Paulo/SP
link_inscricao: https://luma.com/c28tapf3
inscricoes_ate: 2026-10-10
```
(`data`, `local`, `endereco`, `link_inscricao` e `inscricoes_ate` ficam no arquivo mas são ignorados nesse status — pode deixar os valores da última edição.)

### `status: inscricoes_abertas`
Mostra data, local e o botão "Participe" com o link de inscrição.
```yaml
status: inscricoes_abertas
nome: 11a Edição do Rails Girls
data: 2026-10-17
horario: 9h até 19h
local: Vórtx
logo_local: /assets/img/parceiros/vortx.png
endereco: R. Gilberto Sabino, 215, 3o andar - Pinheiros, São Paulo/SP
link_inscricao: https://luma.com/c28tapf3
inscricoes_ate: 2026-10-10
```

### `status: encerradas`
Mostra data e local, sem botão, com aviso de que as inscrições encerraram.
```yaml
status: encerradas
nome: 11a Edição do Rails Girls
data: 2026-10-17
horario: 9h até 19h
local: Vórtx
logo_local: /assets/img/parceiros/vortx.png
endereco: R. Gilberto Sabino, 215, 3o andar - Pinheiros, São Paulo/SP
link_inscricao: https://luma.com/c28tapf3
inscricoes_ate: 2026-10-10
```

### `status: realizado`
Mostra um agradecimento e convite para acompanhar a próxima edição.
```yaml
status: realizado
nome: 11a Edição do Rails Girls
data: 2026-10-17
horario: 9h até 19h
local: Vórtx
logo_local: /assets/img/parceiros/vortx.png
endereco: R. Gilberto Sabino, 215, 3o andar - Pinheiros, São Paulo/SP
link_inscricao: https://luma.com/c28tapf3
inscricoes_ate: 2026-10-10
```

## Outros conteúdos editáveis sem tocar HTML

- `_data/patrocinadores.yml` — patrocinadores por tier (Ruby/Diamante/Safira/Esmeralda/Apoio)
- `_data/apoiadores.yml` — grid de empresas apoiadoras
- `_data/edicoes_anteriores.yml` — cards de edições passadas
- `_data/impacto.yml` — números do "Nosso impacto"
- `_data/depoimentos.yml` — depoimentos de ex-participantes
- `_data/organizadoras.yml` — time de organizadoras
- `_data/faq.yml` — perguntas frequentes
- `_data/social.yml` — links de redes sociais e e-mails de contato

## Imagens

A maior parte das fotos e logos foi baixada direto do site Framer (com autorização — não foi copiado HTML/CSS, só as imagens) e já está em `assets/img/`, comprimida (JPEG ~70-82% de qualidade, largura máxima 900px para fotos, PNG para logos com transparência).

**Logo do Rails Girls:** `assets/img/logo-rails-girls.png` — versão nova (só o texto script, sem o ícone de rubi), usada no hero, no rodapé e no `<meta>` de SEO (`_config.yml`, `logo:`). Já vem com contorno branco, funciona em fundo claro ou escuro. Se precisar trocar de novo, substitua esse arquivo (mantendo fundo transparente) nos três lugares citados.

**Ainda faltam** (ficaram como placeholder SVG em `assets/img/placeholders/`, porque no Framer são desenhados como SVG direto no código da página, não como arquivo de imagem — não deu pra extrair):

| O que é | Placeholder atual | Onde ajustar o caminho |
|---|---|---|
| Logo do patrocinador Rails Foundation | `assets/img/placeholders/patrocinadores/rails-foundation.svg` | `_data/patrocinadores.yml` |
| Logo da apoiadora 4Linux | `assets/img/placeholders/apoiadores/4linux.svg` | `_data/apoiadores.yml` |
| Logo da apoiadora GetNinjas | `assets/img/placeholders/apoiadores/getninjas.svg` | `_data/apoiadores.yml` |
| Logo da apoiadora Campus Code | `assets/img/placeholders/apoiadores/campuscode.svg` | `_data/apoiadores.yml` |
| Imagem de Open Graph (preview em redes sociais) | `assets/img/placeholders/og-image.svg` | `_config.yml` (`image:`) |

Para cada uma: exporte a imagem real, salve em `assets/img/` (fora de `placeholders/`) e atualize o caminho.

O favicon e o logo usados no rodapé (`img/logo.png`, `img/favicon.png`, `img/apple-touch-icon.png`) são do site antigo e não precisam de exportação.

**Logo do local do evento:** fica em `_data/evento.yml`, campo `logo_local`. Quando o local mudar, troque só esse caminho (salve o novo logo em `assets/img/parceiros/`, de preferência a versão "sem assinatura" colorida, com fundo transparente). O da Vórtx (`assets/img/parceiros/vortx.png`) veio de `plan/vortx/Logo_Vórtx_Novo_semAssinatura_Colorido.png`, o material de marca que a Vórtx forneceu — ver `plan/vortx/BrandBook Vórtx - 2025 - Atualizada.pdf` para as outras variações (com tagline, preto, branco, vertical) se precisar delas em outro contexto.

## Conteúdo a confirmar antes de publicar

- `_data/organizadoras.yml` — a associação foto↔nome foi inferida pela proximidade no código-fonte da página (a página de origem não tinha `alt` nas fotos), não por uma marcação explícita. Vale conferir visualmente se bateu.
- `_data/edicoes_anteriores.yml` — a foto da edição "2025 - Novembro" bate com o local (tem a marca "alice" visível); as outras duas fotos foram atribuídas sem uma confirmação equivalente, vale conferir.
- `_data/faq.yml` — a pergunta "Como faço para participar?" foi reescrita de forma atemporal; a resposta original no Framer falava de inscrições encerradas (específico daquele momento), o que conflitaria com o status dinâmico da home.
- `_data/social.yml` — falta o link de WhatsApp (nenhuma versão anterior do site tinha esse link registrado).

## Acessos e responsáveis

_Preencha estes campos — não foram inventados nomes._

- **Domínio (registro.br):** renovação em ______, responsável: ______
- **Owners da organização no GitHub:** ______
- **E-mail de contato (`contato@railsgirls.com.br`):** quem recebe/monitora: ______
- **E-mail de dúvidas (`duvidas@railsgirls.com.br`):** quem recebe/monitora: ______
- **DNS:** onde está configurado (provedor/painel): ______
