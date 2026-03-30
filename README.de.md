🌐 [English](README.md) | [Español](README.es.md) | [Français](README.fr.md) | [Italiano](README.it.md) | [Português](README.pt.md) | [Deutsch](README.de.md)

# youtube-summary

Ein [Claude Code](https://claude.ai/code) Slash-Befehl, der YouTube-Videos mithilfe von MCP-Transkript-Extraktion und visueller Szenenanalyse zusammenfasst.

## Warum

YouTube ist der Ort, wo die besten Ideen leben -- Konferenzvortraege, Gruender-Interviews, tiefgehende Strategie-Analysen. Aber ich habe nicht immer 40 Minuten, um ein Video anzuschauen, nur um 3 zentrale Erkenntnisse herauszuziehen. Dieser Befehl gibt mir den Kern in Sekunden. Ich lese die Zusammenfassung, entscheide ob es sich lohnt das ganze Video anzuschauen, und mache weiter.

Bei Tutorials, Praesentationen und Demos verpasst die Transkription allein die Haelfte der Geschichte -- was auf dem Bildschirm gezeigt wird, zaehlt. Dieser Befehl erfasst beides.

## Was er macht

Holt die Transkription und extrahiert wichtige Screenshots aus einem YouTube-Video, dann erstellt er eine strukturierte Zusammenfassung, die kombiniert was **gesagt** und was **gezeigt** wurde:

- **Kernthese** -- das zentrale Argument in ein bis zwei Saetzen
- **Kernpunkte** -- die wichtigsten Ideen, nach Bedeutung geordnet, mit visuellen Referenzen wo relevant
- **Visuelle Highlights** -- zentrale Slides, Code, Diagramme oder Demos auf dem Bildschirm (uebersprungen bei Talking-Head-Videos)
- **Umsetzbare Erkenntnisse** -- Dinge, die du aus dem Inhalt anwenden kannst

## Voraussetzungen

- [Claude Code](https://claude.ai/code)
- Ein YouTube MCP-Server in Claude Code konfiguriert mit den Tools `youtube_get_transcript` und `youtube_get_screenshots`
- `yt-dlp` und `ffmpeg` installiert (`brew install yt-dlp ffmpeg`) -- fuer die Screenshot-Extraktion

## Installation

```bash
cp summary.md ~/.claude/commands/summary.md
```

Oder direkt herunterladen:

```bash
curl -o ~/.claude/commands/summary.md \
  https://raw.githubusercontent.com/entpnomad/youtube-summary/main/summary.md
```

## Verwendung

```
/summary https://www.youtube.com/watch?v=<video_id>
```

## Beispiele

```
/summary https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

```
/summary https://youtu.be/dQw4w9WgXcQ
```

## Wie es funktioniert

1. Holt die Transkription mit Zeitstempeln ueber den YouTube MCP-Server
2. Extrahiert Screenshots bei visuellen Szenenwechseln mithilfe der ffmpeg-Szenenerkennung (via `youtube_get_screenshots`)
3. Liest wichtige Screenshots, um den visuellen Inhalt zu verstehen
4. Kombiniert gesprochenen + visuellen Inhalt zu einer strukturierten Zusammenfassung

## Lizenz

MIT
