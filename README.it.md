🌐 [English](README.md) | [Español](README.es.md) | [Français](README.fr.md) | [Italiano](README.it.md)

# youtube-summary

Un comando slash di [Claude Code](https://claude.ai/code) che riassume i video di YouTube tramite estrazione di trascrizioni MCP e analisi visiva delle scene.

## Perche

YouTube e dove vivono le migliori idee: conferenze, interviste a fondatori, analisi approfondite sulla strategia. Ma non sempre ho 40 minuti per guardare un video solo per estrarne 3 punti chiave. Questo comando mi da la sostanza in pochi secondi. Leggo il riassunto, decido se vale la pena guardarlo per intero e vado avanti.

Per tutorial, presentazioni e demo, la trascrizione da sola perde meta della storia: quello che viene mostrato a schermo conta. Questo comando cattura entrambi.

## Cosa fa

Recupera la trascrizione ed estrae le schermate chiave da un video di YouTube, poi produce un riassunto strutturato che combina cio che e stato **detto** e cio che e stato **mostrato**:

- **Tesi centrale** — l'argomento principale in una o due frasi
- **Punti chiave** — le idee piu importanti, ordinate per rilevanza, con riferimenti visivi dove pertinente
- **Momenti visivi salienti** — slide, codice, diagrammi o demo chiave mostrati a schermo (saltati per i video di tipo talking-head)
- **Spunti pratici** — cose che puoi applicare dal contenuto

## Requisiti

- [Claude Code](https://claude.ai/code)
- Un server MCP YouTube configurato in Claude Code con gli strumenti `youtube_get_transcript` e `youtube_get_screenshots`
- `yt-dlp` e `ffmpeg` installati (`brew install yt-dlp ffmpeg`) — per l'estrazione delle schermate

## Installazione

```bash
cp summary.md ~/.claude/commands/summary.md
```

Oppure scarica direttamente:

```bash
curl -o ~/.claude/commands/summary.md \
  https://raw.githubusercontent.com/entpnomad/youtube-summary/main/summary.md
```

## Utilizzo

```
/summary https://www.youtube.com/watch?v=<video_id>
```

## Esempi

```
/summary https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

```
/summary https://youtu.be/dQw4w9WgXcQ
```

## Come funziona

1. Recupera la trascrizione con timestamp tramite il server MCP YouTube
2. Estrae schermate ai cambi di scena visivi usando il rilevamento scene di ffmpeg (via `youtube_get_screenshots`)
3. Legge le schermate chiave per comprendere il contenuto visivo
4. Combina il contenuto parlato + visivo in un riassunto strutturato

## Licenza

MIT
