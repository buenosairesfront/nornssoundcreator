# Exportar

Todo se exporta desde la sección **08 Exportar**. Antes de exportar, poné un nombre al sinte: de ahí sale el nombre del motor (`Engine_NombreEnCamelCase`) y de la carpeta.

Hace falta al menos una fuente en el mixer.

## Para norns

### Script Lua

- **Ready to go**: script completo con páginas, controles, arpegio, MIDI y el logo U-MA en la página 1.
  - `E1` cambia de página · `E2` elige parámetro · `E3` cambia el valor
  - `K2` mantiene un C3 · `K3` arpegio on/off
- **Solo sonido**: motor, parámetros y entrada MIDI. Ideal para tocar por MIDI o para seguir desarrollando el script.

### Archivos

Elegí `.lua`, `.sc` o los dos. **Descargar .zip** arma:

```
nombre/
├── nombre.lua
└── lib/
    └── Engine_Nombre.sc
```

### Instalar en norns

1. Descomprimí el `.zip`.
2. Copiá la carpeta `nombre/` a `dust/code/` (por SMB, SFTP o desde maiden).
3. En norns: **SYSTEM → RESTART** (hace falta para que SuperCollider compile el motor nuevo).
4. Abrí el script desde **SELECT**.

Todas las fuentes se suman en un solo motor, porque norns carga un motor por script. Si el motor usa sc3-plugins, norns ya los trae instalados.

**Copiar Lua / Copiar .sc** copian el código al portapapeles. **Ver código** muestra los cuatro formatos (`.lua`, `.sc`, `.scd`, `.dsp`).

## Sin norns

### Web app

Un `.zip` con una app independiente del sonido:

```
nombre/
├── index.html
├── manifest.webmanifest
├── sw.js
├── icon-192.png
├── icon-512.png
└── LEEME.txt   (README.txt en los otros idiomas)
```

Tiene controles editables, teclado, MIDI, grabación a WAV, presets y se puede instalar en el celular. La interfaz de la web app sale en el idioma elegido en Norns Sound Creator (es, en, de, zh, ja, hi).

Para instalarla en el celular, subí la carpeta a un hosting con https (por ejemplo GitHub Pages o Netlify Drop) y en Chrome usá **Instalar app**.

### SuperCollider (.scd)

Mismo sonido que en norns, para SuperCollider en Windows, Mac o Linux:

1. Abrí el `.scd` en [SuperCollider](https://supercollider.github.io).
2. Hacé clic dentro del paréntesis principal y presioná `Ctrl+Enter` (`Cmd+Enter` en Mac).
3. Se abre una ventana con los controles. Tocá con un teclado MIDI o con el botón C3.
4. `Ctrl+.` / `Cmd+.` detiene todo.

Si el sonido usa fuentes o efectos de sc3-plugins, hay que tenerlos instalados.

### VST / AU (Faust .dsp)

1. Abrí https://faustide.grame.fr y pegá el código (o arrastrá el archivo).
2. **Export** → elegí tu sistema (windows / osx / linux) y `vst` (o `juce` / `au` en Mac).
3. Copiá el plugin a la carpeta de plugins de tu DAW.

Es polifónico por MIDI. Faust no tiene equivalente directo para algunas fuentes (Gendy, caóticos, MdaPiano, DWGPlucked…): se reemplazan por la más parecida y el `.dsp` lo indica en un comentario.

## Proyectos (.nsc.json)

Desde **09 Proyectos → Exportar .json** se guarda el patch completo:

```json
{ "app": "norns-sound-creator", "v": 2, "patch": { ... } }
```

**Importar .json** lo vuelve a cargar en cualquier navegador.
