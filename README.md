# 🛡️ JEFATURA DE CIBERDEFENSA — FAE
## Monitor de Páginas · Fuerza Aérea Ecuatoriana

---

## 📁 Estructura del proyecto

```
fae-ciberdefensa/
├── fae_cybermonitor.html   ← Archivo principal (todo en uno)
└── README.md               ← Este archivo
```

> El archivo HTML es **autocontenido** — imagen, estilos y código están dentro de un solo archivo. No necesita servidor ni dependencias adicionales para funcionar.

---

## 🚀 Cómo abrir en VS Code

### Opción 1 — Live Server (recomendado)

1. Instala VS Code → [https://code.visualstudio.com](https://code.visualstudio.com)
2. Abre VS Code y ve a **Extensiones** (`Ctrl+Shift+X`)
3. Busca **Live Server** (autor: Ritwick Dey) e instálalo
4. Abre la carpeta del proyecto: `Archivo → Abrir carpeta`
5. Clic derecho sobre `fae_cybermonitor.html` en el explorador
6. Selecciona **"Open with Live Server"**
7. Se abrirá automáticamente en tu navegador en `http://127.0.0.1:5500`

### Opción 2 — Abrir directo en navegador

1. Navega a la carpeta donde guardaste el archivo
2. Doble clic sobre `fae_cybermonitor.html`
3. Se abre en tu navegador predeterminado

> ⚠️ **Nota:** Para que el mapa mundial cargue correctamente necesitas conexión a internet (descarga el mapa desde un CDN). El resto funciona sin conexión.

---

## 🌐 URLs monitoreadas

| Sistema | URL |
|---------|-----|
| 🖥️ Sistemas FAE | https://sistemas.fae.mil.ec/ |
| 📡 Chasqui FFAA | https://chasqui.ffaa.mil.ec/ |
| 🔍 Consultas Web | https://sistemas.fae.mil.ec/consultas-web/pages/inicio.jsf |
| ✉️ Correo FAE | https://correo.fae.mil.ec/static/login/ |
| 💾 Almacenamiento | https://almacenamiento.fae.mil.ec/index.php/login |
| 🌐 Portal FAE | https://portal.fae.mil.ec/faeweb/ |

---

## ⚙️ Funcionalidades

### Panel izquierdo — Monitor de endpoints
- ✅ Verificación de estado en tiempo real (HTTP HEAD + fallback imagen)
- 📊 Latencia en milisegundos por endpoint
- 📈 Porcentaje de uptime basado en historial de checks
- 🔄 Verificación automática cada **60 segundos**
- ↗️ Botón **"Abrir sitio"** en cada tarjeta para acceso directo

### Panel derecho — Mapa de amenazas estilo Kaspersky
- 🌍 Mapa mundial real (Natural Earth / TopoJSON)
- 🎯 Todos los ataques apuntan a **Quito — FAE**
- ⚡ 3 a 6 arcos simultáneos activos en todo momento
- 🔴 Colores por severidad: Rojo (Crítico), Ámbar (Alto), Azul (Medio)
- 💥 Animación de impacto con ondas al llegar a Quito
- 📡 Ticker inferior con IP, ciudad origen y tipo de ataque en tiempo real
- 70+ ciudades fuente reales de todo el mundo

---

## 🎨 Tecnologías utilizadas

| Tecnología | Uso |
|------------|-----|
| HTML5 + CSS3 | Estructura y estilos |
| JavaScript (ES6+) | Lógica de verificación y animaciones |
| Canvas 2D API | Motor de renderizado del mapa de ataques |
| D3.js v7 | Proyección cartográfica Natural Earth |
| TopoJSON | Datos geográficos de países |
| Google Fonts (Inter + JetBrains Mono) | Tipografía |
| world-atlas@2 | Geometría de países (CDN) |

---

## 🔧 Personalización

### Agregar o cambiar URLs monitoreadas

Abre `fae_cybermonitor.html` y busca la sección `ENDPOINTS` en el JavaScript:

```javascript
const TARGETS = [
  { id:'sistemas', name:'Sistemas FAE', icon:'🖥️', url:'https://sistemas.fae.mil.ec/' },
  // Agrega más entradas aquí con el mismo formato
  { id:'nuevo',    name:'Nuevo Sistema', icon:'🔒', url:'https://tu-url.mil.ec/' },
];
```

### Cambiar el intervalo de verificación

Busca esta línea al final del script:

```javascript
setInterval(startCheck, 60000);  // 60000ms = 60 segundos
```

Cámbialo por el intervalo deseado (en milisegundos).

### Cambiar el objetivo del mapa (ciudad base)

Busca en el JavaScript:

```javascript
const HOME = { lat:-0.22, lon:-78.51 };  // Quito, Ecuador
```

---

## 📋 Requisitos del sistema

- Navegador moderno: Chrome 90+, Firefox 88+, Edge 90+, Safari 14+
- Conexión a internet (para mapa y fuentes)
- Resolución recomendada: 1280×720 o superior

---

## ℹ️ Notas importantes

- La verificación usa `fetch` en modo `no-cors` — detecta si el servidor responde pero **no puede leer el código HTTP**. Un servidor caído no responderá; uno en línea sí.
- Los ataques del mapa son **simulados** con datos realistas (IPs, ciudades y tipos de ataque representativos).
- La imagen del escudo está **embebida en base64** dentro del HTML — no requiere archivo externo.

---

*Jefatura de Ciberdefensa — Fuerza Aérea Ecuatoriana*
