# CLI Terminal — Aprende la terminal desde cero

Aplicación web interactiva tipo **Duolingo** para aprender a manejar la **terminal de comandos (CLI)** desde cero. Combina teoría clara con práctica real mediante un emulador de terminal y un sistema de archivos virtual.

Es una app **autocontenida en un solo archivo HTML** (`cli-duo.html`): no necesita instalación, build ni servidor.

## Características

- **Fase de teoría** antes de cada minijuego. Cada comando se explica con la estructura obligatoria:
  1. ¿Qué es y qué hace?
  2. ¿Cómo funciona internamente?
  3. ¿Para qué sirve en la vida real?
  4. ¿Cómo se usa? (sintaxis + ejemplos visuales)
- **Fase de práctica tipo Duolingo**: preguntas de opción múltiple + retos en una **terminal real**.
- **Emulador de terminal con Virtual File System**: los comandos de verdad crean, mueven y borran archivos. Soporta banderas, comodines, redirección, tuberías (`|`) y encadenado (`&&`, `||`).
- **Gamificación**: XP, vidas (❤️) y rachas diarias (🔥).
- **Persistencia** con `localStorage`: el progreso se guarda en el navegador.

## Comandos incluidos

`pwd` · `ls` (`-l`, `-a`, `-h`) · `cd` · `mkdir` · `touch` · `cat` · `echo` · `cp` · `mv` · `rm` (`-r`) · `head` · `tail` · `wc` · `grep` · `find` · `man` · `history` · `chmod` · `clear` · `help`

Además: redirección (`>`, `>>`, `<`), tuberías (`|`), encadenado (`&&`, `||`) y comodines (`*`, `?`).

## Lecciones

| # | Lección | Contenido |
|---|---------|-----------|
| 1 | Ubicarse | `pwd`, `ls` |
| 2 | Navegar | `cd` |
| 3 | Crear | `mkdir`, `touch` |
| 4 | Leer y escribir | `cat`, `echo` |
| 5 | Organizar | `cp`, `mv`, `rm` |
| 6 | Banderas | `ls -l/-a`, `rm -r`, comodines |
| 7 | Buscar y leer | `head`, `tail`, `wc`, `grep`, `find`, `man` |
| 8 | Tuberías | redirección, `|`, `&&` y `||` |
| 9 | Permisos | `chmod` |

## Cómo usarla

**Opción 1 — Local:** descarga el repo y abre `cli-duo.html` en tu navegador (doble clic).

**Opción 2 — En línea:** accede a GitHub Pages (ver más abajo).

## Tecnologías

- HTML + JavaScript vanilla (sin dependencias de build)
- [Tailwind CSS](https://tailwindcss.com/) vía CDN
- Google Fonts (Nunito)

## Estructura

```
mi_proyecto_App_terminal/
├── cli-duo.html   # La aplicación completa
├── index.html     # Redirección para GitHub Pages
└── README.md
```

## Cómo funciona la validación

La teoría y la práctica están desacopladas. El motor `runLine()` interpreta cada línea (separando por `&&`/`||` y por `|`), y el parser de cada etapa detecta las redirecciones. Los comandos se ejecutan **de verdad** sobre el sistema de archivos virtual (cambia `cwd`, crea inodos, escribe archivos, aplica permisos). Cada reto valida el **resultado real** con una función `check(ctx)` que inspecciona el estado resultante (`isFile`, `isDir`, `fileContent`, `permOf`, `cwd`, `piped`, `cmds`), no el texto tecleado.

---

Proyecto de práctica de desarrollo de software. ¡Aprende la terminal jugando!
