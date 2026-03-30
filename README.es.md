🌐 [English](README.md) | [Español](README.es.md) | [Français](README.fr.md) | [Italiano](README.it.md) | [Português](README.pt.md) | [Deutsch](README.de.md)

# youtube-summary

Un comando slash de [Claude Code](https://claude.ai/code) que resume videos de YouTube mediante extraccion de transcripciones MCP y analisis visual de escenas.

## Por que

YouTube es donde viven las mejores ideas: charlas de conferencias, entrevistas a fundadores, analisis profundos sobre estrategia. Pero no siempre tengo 40 minutos para ver un video solo para sacar 3 conclusiones clave. Este comando me da lo esencial en segundos. Leo el resumen, decido si vale la pena verlo completo y sigo adelante.

Para tutoriales, presentaciones y demos, la transcripcion sola se pierde la mitad de la historia: lo que se muestra en pantalla importa. Este comando captura ambas cosas.

## Que hace

Obtiene la transcripcion y extrae capturas de pantalla clave de un video de YouTube, y luego produce un resumen estructurado combinando lo que se **dijo** y lo que se **mostro**:

- **Tesis central** — el argumento principal en una o dos frases
- **Puntos clave** — las ideas mas importantes, ordenadas por relevancia, con referencias visuales cuando corresponde
- **Momentos visuales destacados** — diapositivas, codigo, diagramas o demos clave mostrados en pantalla (se omite en videos de tipo talking-head)
- **Conclusiones practicas** — cosas que puedes aplicar del contenido

## Requisitos

- [Claude Code](https://claude.ai/code)
- Un servidor MCP de YouTube configurado en Claude Code con las herramientas `youtube_get_transcript` y `youtube_get_screenshots`
- `yt-dlp` y `ffmpeg` instalados (`brew install yt-dlp ffmpeg`) — para la extraccion de capturas

## Instalacion

```bash
cp summary.md ~/.claude/commands/summary.md
```

O descargalo directamente:

```bash
curl -o ~/.claude/commands/summary.md \
  https://raw.githubusercontent.com/entpnomad/youtube-summary/main/summary.md
```

## Uso

```
/summary https://www.youtube.com/watch?v=<video_id>
```

## Ejemplos

```
/summary https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

```
/summary https://youtu.be/dQw4w9WgXcQ
```

## Como funciona

1. Obtiene la transcripcion con marcas de tiempo a traves del servidor MCP de YouTube
2. Extrae capturas de pantalla en los cambios de escena visual usando la deteccion de escenas de ffmpeg (via `youtube_get_screenshots`)
3. Lee las capturas clave para comprender el contenido visual
4. Combina el contenido hablado + visual en un resumen estructurado

## Licencia

MIT
