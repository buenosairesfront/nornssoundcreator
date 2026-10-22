# Guía de uso

La app está dividida en 9 secciones numeradas, más una barra superior y un teclado fijo abajo.

## Barra superior

- **↶ / ↷**: deshacer y rehacer (hasta 80 pasos).
- **⚙**: idioma, tema (sistema / claro / oscuro), motor de audio y tamaño de buffer del modo compatible.
- **Osciloscopio / Espectro / Ambos**: cambia la vista del scope. Abajo muestra nota, frecuencia, pico en dB y voces sonando.
- **CPU norns**: estimación del uso de CPU que tendría el motor en una norns. Cian por debajo de 55 %, amarillo hasta 80 %, magenta arriba.
- **🎲 Sorpresa**: genera un sonido al azar (1 a 3 fuentes, filtro, envolvente, LFO y hasta 2 efectos).
- **🧬 Mutar**: varía un poco el sonido actual. Los controles que cambiaron se resaltan en amarillo.
- **⟲ Reset**: vuelve al sonido inicial. Se puede deshacer.
- **A / B**: guarda dos versiones del sonido para compararlas.

## 01 Fuentes

Biblioteca de 62 fuentes en cuatro pestañas:

- **norns**: TestSine, PolyPerc (cuadrada, pulsos, pluck, bajo, pad, vidrio) y las variantes U-MA de PolyPerc (sierra, triángulo, seno, ruido).
- **SuperCollider**: osciladores core (SinOsc, Saw, Pulse, VarSaw, Blip, Formant, PMOsc, Klank, Pluck, Gendy…).
- **Ruido y caos**: ruidos, Dust, Crackle, LFNoise y generadores caóticos (Logistic, Henon, Lorenz, Latoocarfian…).
- **sc3-plugins**: DPW, BlitB3Saw, VOSIM, Gendy4/5, Perlin3, MdaPiano, DWGPlucked.

Tocá un nombre para sumarlo al mixer. **▶** lo escucha solo, sin sumarlo.

Insignias: **=** mismo algoritmo que SuperCollider · **≈** aproximación en el navegador · **U** variante U-MA.

## 02 Mixer

Hasta 12 canales. Cada uno tiene fader de nivel con vúmetro, **M** (mute), **S** (solo), pan, semitonos (±24), fino (±50 cents) y, según la fuente, un control de carácter (ancho, feedback, armónicos, caos, densidad…). **×** quita el canal.

## 03 Voces

- **Polifonía**: de 1 a 8 voces. Cuando se superan, se roba la más vieja.
- **Salida de voces**: 1 bus (centro), 2 buses (alterna izquierda/derecha) o 1 por voz (repartidas en el estéreo).
- **Volumen** general.

## 04 Envolvente

ADSR con curva -4 (igual a `Env.adsr` de SuperCollider). El gráfico usa un eje de tiempo comprimido para que se lean bien las etapas cortas y largas. Con OFF la envolvente pasa a un gate simple.

## 05 Filtro

- **core**: RLPF, RHPF, BPF, BRF, Resonz, LPF, HPF, MoogFF.
- **sc3-plugins**: DFM1, MoogLadder, RLPFD.
- **Corte** (20 Hz a 18 kHz) y **resonancia**.
- **CV teclado**: el corte sigue la nota tocada.
- **Env**: la envolvente abre el filtro.

## 06 LFO

Formas: triángulo, seno, cuadrada, aleatoria suave, S&H duro y S&H suave. Modula corte, resonancia, afinación, volumen o pan. Velocidad de 0,05 a 30 Hz.

## 07 Efectos

Tocá un efecto para sumarlo a la cadena. Se aplican en orden y se reordenan con ↑ ↓.

- **core**: FreeVerb, CombC delay, Chorus, Flanger, Phaser, Distorsión (tanh), Wavefolder, PitchShift, Compander, Limiter.
- **sc3-plugins**: Decimator, Greyhole.

Abajo están los **efectos del sistema norns** (reverb con envío y compresor). En la exportación se activan con los parámetros del sistema, no dentro del motor.

## 08 Exportar

Ver [EXPORTAR.md](EXPORTAR.md).

## 09 Proyectos

- **Guardar** guarda el sonido actual con su nombre en este navegador.
- **Nuevo** empieza un proyecto vacío.
- **Exportar .json / Importar .json** pasa proyectos a otro dispositivo.
- Tocá un nombre de la lista para renombrarlo. **Borrar** pide confirmación.

El borrador actual se guarda solo, así que al recargar la página seguís donde estabas.

## Teclado

- Teclado en pantalla de una octava, con **− / +** para cambiar de octava (C0 a C7).
- **Test C3**: nota sostenida (on/off).
- **Gate**: nota mientras mantenés apretado.
- **Arp**: arpegio con BPM ajustable (50 a 200).
- Teclado de la compu: `A W S E D F T G Y H U J K` = de C a C de la octava siguiente.

El navegador necesita un toque o una tecla para activar el audio.
