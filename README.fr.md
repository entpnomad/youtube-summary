🌐 [English](README.md) | [Español](README.es.md) | [Français](README.fr.md) | [Italiano](README.it.md) | [Português](README.pt.md) | [Deutsch](README.de.md)

# youtube-summary

Une commande slash [Claude Code](https://claude.ai/code) qui resume les videos YouTube grace a l'extraction de transcriptions MCP et l'analyse visuelle des scenes.

## Pourquoi

YouTube est l'endroit ou vivent les meilleures idees : conferences, interviews de fondateurs, analyses approfondies de strategie. Mais je n'ai pas toujours 40 minutes pour regarder une video juste pour en tirer 3 points cles. Cette commande me donne l'essentiel en quelques secondes. Je lis le resume, je decide si ca vaut le coup de tout regarder, et je passe a autre chose.

Pour les tutoriels, les presentations et les demos, la transcription seule rate la moitie de l'histoire : ce qui est montre a l'ecran compte. Cette commande capture les deux.

## Ce que ca fait

Recupere la transcription et extrait les captures d'ecran cles d'une video YouTube, puis produit un resume structure combinant ce qui a ete **dit** et ce qui a ete **montre** :

- **These centrale** — l'argument principal en une ou deux phrases
- **Points cles** — les idees les plus importantes, classees par importance, avec des references visuelles quand c'est pertinent
- **Moments visuels marquants** — diapositives, code, diagrammes ou demos cles montres a l'ecran (ignore pour les videos de type talking-head)
- **Points d'action** — ce que vous pouvez appliquer du contenu

## Prerequis

- [Claude Code](https://claude.ai/code)
- Un serveur MCP YouTube configure dans Claude Code avec les outils `youtube_get_transcript` et `youtube_get_screenshots`
- `yt-dlp` et `ffmpeg` installes (`brew install yt-dlp ffmpeg`) — pour l'extraction des captures

## Installation

```bash
cp summary.md ~/.claude/commands/summary.md
```

Ou telechargez directement :

```bash
curl -o ~/.claude/commands/summary.md \
  https://raw.githubusercontent.com/entpnomad/youtube-summary/main/summary.md
```

## Utilisation

```
/summary https://www.youtube.com/watch?v=<video_id>
```

## Exemples

```
/summary https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

```
/summary https://youtu.be/dQw4w9WgXcQ
```

## Comment ca marche

1. Recupere la transcription horodatee via le serveur MCP YouTube
2. Extrait des captures d'ecran aux changements de scene visuels grace a la detection de scenes de ffmpeg (via `youtube_get_screenshots`)
3. Lit les captures cles pour comprendre le contenu visuel
4. Combine le contenu parle + visuel dans un resume structure

## Licence

MIT
