🌐 [English](README.md) | [Español](README.es.md) | [Français](README.fr.md) | [Italiano](README.it.md) | [Português](README.pt.md) | [Deutsch](README.de.md)

# youtube-summary

Um comando slash do [Claude Code](https://claude.ai/code) que resume videos do YouTube usando extracao de transcricoes MCP e analise visual de cenas.

## Porque

O YouTube e onde vivem as melhores ideias -- palestras de conferencias, entrevistas com fundadores, analises profundas sobre estrategia. Mas nem sempre tenho 40 minutos para ver um video so para tirar 3 conclusoes-chave. Este comando da-me a substancia em segundos. Leio o resumo, decido se vale a pena ver o video inteiro e sigo em frente.

Para tutoriais, apresentacoes e demos, a transcricao sozinha perde metade da historia -- o que e mostrado no ecra importa. Este comando captura ambos.

## O que faz

Obtem a transcricao e extrai capturas de ecra chave de um video do YouTube, depois produz um resumo estruturado combinando o que foi **dito** e o que foi **mostrado**:

- **Tese central** -- o argumento principal numa ou duas frases
- **Pontos-chave** -- as ideias mais importantes, ordenadas por relevancia, com referencias visuais quando pertinente
- **Destaques visuais** -- slides, codigo, diagramas ou demos chave mostrados no ecra (omitido para videos de tipo talking-head)
- **Conclusoes praticas** -- coisas que podes aplicar do conteudo

## Requisitos

- [Claude Code](https://claude.ai/code)
- Um servidor MCP do YouTube configurado no Claude Code com as ferramentas `youtube_get_transcript` e `youtube_get_screenshots`
- `yt-dlp` e `ffmpeg` instalados (`brew install yt-dlp ffmpeg`) -- para a extracao de capturas

## Instalacao

```bash
cp summary.md ~/.claude/commands/summary.md
```

Ou descarrega diretamente:

```bash
curl -o ~/.claude/commands/summary.md \
  https://raw.githubusercontent.com/entpnomad/youtube-summary/main/summary.md
```

## Uso

```
/summary https://www.youtube.com/watch?v=<video_id>
```

## Exemplos

```
/summary https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

```
/summary https://youtu.be/dQw4w9WgXcQ
```

## Como funciona

1. Obtem a transcricao com timestamps atraves do servidor MCP do YouTube
2. Extrai capturas de ecra nas mudancas de cena visual usando a detecao de cenas do ffmpeg (via `youtube_get_screenshots`)
3. Le as capturas chave para compreender o conteudo visual
4. Combina o conteudo falado + visual num resumo estruturado

## Licenca

MIT
