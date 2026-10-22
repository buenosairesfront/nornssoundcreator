# Arquitectura

Norns Sound Creator es un único archivo, `index.html`, sin dependencias ni paso de build. Las únicas cargas externas son tipografías de Google Fonts.

## Bloques de `<script>`

En orden:

1. **Definiciones y generadores de código.**
   - `SRC`: las 62 fuentes (clave, biblioteca, nombre, insignia, control de carácter, generador SuperCollider, costo de CPU).
   - `FILTERS`, `FX`, `LFOSC`, `LFODEST`: filtros, efectos y LFO con su código SuperCollider.
   - `genSC` → `Engine_*.sc` (CroneEngine para norns).
   - `genSCD` → `.scd` para SuperCollider de escritorio.
   - `genLua` → script Lua ("Ready to go" o "Solo sonido").
   - `genFaust` → `.dsp` para Faust (VST/AU).
   - `cpuEstimate` → estimación de CPU en norns.
2. **`makeDSP(SR)`**: el motor de audio del navegador, en JavaScript puro, muestra por muestra. Implementa las fuentes, los filtros (coeficientes de SuperCollider donde se puede), la envolvente, el LFO y los efectos. Corre dentro de un `AudioWorklet` (o de un `ScriptProcessor` si el worklet no está disponible).
3. **`I18N`**: diccionarios de la interfaz en `es`, `en`, `ja`, `hi`, `de`, `zh`.
4. **`webAppMain(CFG)`**: la app que va dentro de la web app exportada. Se serializa con `toString()` y se incrusta en el `index.html` exportado junto a `makeDSP`.
5. **`WEBCSS` y `genWebFiles`**: estilos y archivos de la web app exportada (HTML, manifest, service worker, LEEME/README).
6. **La interfaz principal** (IIFE): estado, render de cada sección, exportación, proyectos, teclado, scope y arranque.

## Estado

- `P` es el patch actual (fuentes, voces, envolvente, filtro, LFO, efectos, efectos del sistema, volumen).
- Cada cambio llama a `changed()`, que manda el patch al motor de audio en el siguiente frame, guarda el borrador y registra un paso de deshacer después de 400 ms sin cambios.
- `S` son las preferencias (idioma, tema, vista del scope, biblioteca, modo Lua, archivos, BPM, octava, buffer).

## Almacenamiento (localStorage)

| Clave | Contenido |
|---|---|
| `nsc.settings` | Preferencias, incluido el idioma |
| `nsc.draft` | Patch actual, para seguir después de recargar |
| `nsc.projects` | Proyectos guardados |
| `nscweb:<slug>` | Presets de cada web app exportada |

Todas las lecturas y escrituras están protegidas con `try/catch`, así que la app funciona igual en modo privado (sin guardar).

## Audio

- `ensureAudio()` crea el `AudioContext` en el primer gesto del usuario.
- Primero intenta cargar el worklet desde un Blob, después desde un `data:` URL y, si falla, usa `ScriptProcessor` con el buffer elegido en ⚙.
- Un `AnalyserNode` alimenta el osciloscopio y el espectro.

## Descargas

`saveFile()` usa la capacidad `downloads` cuando la app corre como Artifact de Claude y, si no, un enlace `<a download>` normal (GitHub Pages y local). Los `.zip` se arman en el navegador con `makeZip()` (sin compresión, con CRC32).

## Idioma

Ver [IDIOMAS.md](IDIOMAS.md). La función `t(clave)` busca en `I18N[S.lang]`, después en español y, si no existe, devuelve la clave.
