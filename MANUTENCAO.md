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

Fotos e logos ficam em `assets/img/`, comprimidas (JPEG ~70-82% de qualidade, largura máxima 900px para fotos, PNG para logos com transparência).

**Logo do Rails Girls:** `assets/img/logo-rails-girls.png` — usada no hero, no rodapé e no `<meta>` de SEO (`_config.yml`, `logo:`). Tem contorno branco, funciona em fundo claro ou escuro. Para trocar, substitua esse arquivo (mantendo fundo transparente) nos três lugares citados.

**Logo do local do evento:** fica em `_data/evento.yml`, campo `logo_local`. Quando o local mudar, troque só esse caminho (salve o novo logo em `assets/img/parceiros/`, de preferência uma versão colorida com fundo transparente).

O favicon e o logo usados no rodapé (`img/logo.png`, `img/favicon.png`, `img/apple-touch-icon.png`) são do site antigo (arquivo histórico) e não devem ser mexidos.
