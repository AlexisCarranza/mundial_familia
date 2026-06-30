# 🏆 Mundial '26 — Visualizador Interactivo

> **Español** | [English below](#-mundial-26--interactive-visualizer)

---

## ¿Qué es esto?

Un visualizador manual de resultados del **Mundial de Fútbol 2026** pensado para correr directamente en **GitHub Pages** sin ningún backend, API ni base de datos. Un solo archivo HTML con todo adentro: datos, lógica y UI.

## ✨ Funcionalidades

- **Camino a la Final** — Fase de 16vos, Octavos, Cuartos, Semifinales, Tercer puesto y Final con resolución dinámica del bracket
- **Partidos del Día** — Carrusel que muestra los partidos de la fecha actual con badge LIVE pulsante
- **Marcadores en vivo** — Indicador `LIVE` en tiempo real con auto-refresh cada 3 minutos y actualización del título del navegador
- **Tiempo extra** — Badge `ET` amarillo cuando un partido va al alargue
- **Penales** — Badge `PEN`, marcador numérico de la tanda (`3 - 4 pen`) y secuencia visual de cada cobro (`✓` anotado / `✗` fallado)
- **Ganador en negrilla** — El equipo ganador aparece en bold, incluyendo cuando se define por penales
- **Fase de Grupos** — Tabla de posiciones por grupo con goles, puntos y diferencia de gol
- **Estadísticas** — Tabla de goleadores, asistencias y mejores terceros del torneo
- **Diseño mobile-first** — Optimizado para ver desde el celular durante los partidos
- **Easter egg Colombia** 🇨🇴 — Diseño especial en degradado tricolor cuando Colombia juega

## 🛠️ Stack técnico

| Tecnología | Rol |
|---|---|
| HTML5 | Estructura única del proyecto (sin build) |
| React 18 (CDN) | Componentes de UI |
| Babel Standalone (CDN) | Transpilación de JSX en el navegador |
| Tailwind CSS (CDN) | Estilos utilitarios |
| flagcdn.com | Banderas de selecciones por código ISO |
| Google Analytics | Métricas de visitas |

**Principio de diseño:** cero dependencias instaladas, cero servidores, cero configuración. Funciona con un doble clic o desde GitHub Pages.

## 📁 Estructura del proyecto

```
/
└── index.html    ← Todo el proyecto vive aquí
└── README.md
```

## 🔧 Cómo actualizar los datos

Todos los datos viven como constantes JavaScript dentro del `index.html`. No hay API ni integración automática — la actualización es manual e intencional.

### Partido normal (ganó en 90')
```js
{ id: 'm76', ..., hGoals: 2, aGoals: 1, played: true,
  extraTime: false, penalties: false, hPens: 0, aPens: 0,
  penSequence: { home: [], away: [] },
  scorers: { home: ["Casemiro 56'"], away: ["K. Sano 29'"] } }
```

### Partido con tiempo extra (ganó en ET)
```js
{ ..., hGoals: 2, aGoals: 1, played: true,
  extraTime: true, penalties: false, hPens: 0, aPens: 0,
  penSequence: { home: [], away: [] } }
```

### Partido definido por penales
```js
{ ..., hGoals: 1, aGoals: 1, played: true,   // resultado del tiempo jugado
  extraTime: true, penalties: true,
  hPens: 4, aPens: 3,                          // conteo para el bracket
  penSequence: {
    home: ['O','O','X','O','O'],               // O = anotado  |  X = fallado
    away: ['O','O','O','X','O']
  } }
```

### Partido en vivo
```js
{ ..., played: 'live', hGoals: 1, aGoals: 0,
  extraTime: false }   // cambiar a true si entra al alargue
```

## 🚀 Despliegue

1. Hacer fork o clonar el repositorio
2. Activar **GitHub Pages** en `Settings → Pages → Branch: main / root`
3. Acceder a `https://<tu-usuario>.github.io/<nombre-del-repo>/`
4. Actualizar `index.html` con los resultados y hacer commit — los cambios se publican en segundos

## 📄 Licencia

Proyecto personal de uso libre. Sin restricciones de uso o distribución.

---
---

# 🏆 Mundial '26 — Interactive Visualizer

> [Español arriba](#-mundial-26--visualizador-interactivo) | **English**

---

## What is this?

A manual results tracker for the **2026 FIFA World Cup**, designed to run directly on **GitHub Pages** with no backend, API, or database. A single HTML file containing everything: data, logic, and UI.

## ✨ Features

- **Road to the Final** — Round of 32, Round of 16, Quarterfinals, Semifinals, Third place and Final with dynamic bracket resolution
- **Today's Matches** — Carousel showing current day fixtures with a pulsing LIVE badge
- **Live scores** — Real-time `LIVE` indicator with auto-refresh every 3 minutes and browser tab title update
- **Extra time** — Yellow `ET` badge when a match goes to extra time
- **Penalties** — `PEN` badge, numeric shootout score (`3 - 4 pen`) and visual kick-by-kick sequence (`✓` scored / `✗` missed)
- **Winner in bold** — The winning team appears bold, including when decided by penalties
- **Group Stage** — Standings table per group with goals, points and goal difference
- **Statistics** — Top scorers, assists and best third-place teams
- **Mobile-first design** — Optimized for watching on your phone during matches
- **Colombia Easter egg** 🇨🇴 — Special tricolor gradient design when Colombia plays

## 🛠️ Tech stack

| Technology | Role |
|---|---|
| HTML5 | Single project file (no build step) |
| React 18 (CDN) | UI components |
| Babel Standalone (CDN) | In-browser JSX transpilation |
| Tailwind CSS (CDN) | Utility-first styling |
| flagcdn.com | National team flags via ISO codes |
| Google Analytics | Visit metrics |

**Design principle:** zero installed dependencies, zero servers, zero configuration. Works with a double-click or directly from GitHub Pages.

## 📁 Project structure

```
/
└── index.html    ← The entire project lives here
└── README.md
```

## 🔧 How to update data

All data lives as JavaScript constants inside `index.html`. There is no API or automatic integration — updates are manual and intentional.

### Regular match (won in 90')
```js
{ id: 'm76', ..., hGoals: 2, aGoals: 1, played: true,
  extraTime: false, penalties: false, hPens: 0, aPens: 0,
  penSequence: { home: [], away: [] },
  scorers: { home: ["Casemiro 56'"], away: ["K. Sano 29'"] } }
```

### Match with extra time (won in ET)
```js
{ ..., hGoals: 2, aGoals: 1, played: true,
  extraTime: true, penalties: false, hPens: 0, aPens: 0,
  penSequence: { home: [], away: [] } }
```

### Match decided by penalty shootout
```js
{ ..., hGoals: 1, aGoals: 1, played: true,   // score at end of play
  extraTime: true, penalties: true,
  hPens: 4, aPens: 3,                          // numeric count for bracket
  penSequence: {
    home: ['O','O','X','O','O'],               // O = scored  |  X = missed
    away: ['O','O','O','X','O']
  } }
```

### Live match (in progress)
```js
{ ..., played: 'live', hGoals: 1, aGoals: 0,
  extraTime: false }   // set to true when extra time starts
```

## 🚀 Deployment

1. Fork or clone the repository
2. Enable **GitHub Pages** under `Settings → Pages → Branch: main / root`
3. Visit `https://<your-username>.github.io/<repo-name>/`
4. Update `index.html` with results and commit — changes go live in seconds

## 📄 License

Personal project, free to use. No restrictions on use or distribution.
