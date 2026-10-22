# Norns Sound Creator · U-MA サウンド

Diseño de sonidos para **norns / norns shield** y **SuperCollider**, directo en el navegador.
Armás el motor con fuentes, filtro, envolvente, LFO y efectos, lo escuchás en vivo y te llevás los archivos listos para usar.

**▶ Probar:** https://buenosairesfront.github.io/nornssoundcreator/

Parte de [Buenos Aires Front](https://www.instagram.com/buenos.aires.front/) · herramientas U-MA.

**Idiomas:** Español · English · Deutsch · 中文 · 日本語 · हिन्दी

---

## Qué hace

- **62 fuentes de sonido** en 4 bibliotecas: norns (PolyPerc y variantes U-MA), SuperCollider core, ruido y caos, sc3-plugins.
- **Mixer de hasta 12 fuentes** con nivel, pan, afinación (semitonos y cents), mute/solo y un control de carácter por fuente.
- **Voces:** polifonía de 1 a 8 y salida en 1 bus, 2 buses o 1 por voz.
- **Envolvente ADSR** (curva -4, igual que `Env.adsr` de SuperCollider).
- **11 filtros** (RLPF, RHPF, BPF, BRF, Resonz, LPF, HPF, MoogFF + DFM1, MoogLadder, RLPFD) con seguimiento de teclado y de envolvente.
- **LFO** con 6 formas y 5 destinos (corte, resonancia, afinación, volumen, pan).
- **12 efectos** en cadena reordenable, más la reverb y el compresor del sistema norns.
- **Osciloscopio, espectro y CPU estimada de norns** en tiempo real.
- **Sorpresa, Mutar, comparación A/B, deshacer/rehacer.**
- **Proyectos** guardados en el navegador, exportables como `.json`.

## Qué exporta

| Destino | Archivo | Para qué |
|---|---|---|
| norns | `.zip` con `nombre.lua` + `lib/Engine_Nombre.sc` | Script listo para `dust/code/` ("Ready to go" o "Solo sonido") |
| SuperCollider | `.scd` | Tocar el mismo sonido en Windows, Mac o Linux, con ventana de controles y MIDI |
| VST / AU | `.dsp` (Faust) | Plugin para tu DAW vía [Faust IDE](https://faustide.grame.fr) |
| Web app | `.zip` con `index.html`, manifest, service worker e íconos | App instalable en el celular, con MIDI, grabación WAV y presets |

## Uso rápido

1. Abrí la app y tocá el teclado (o **Test C3**) para activar el audio.
2. Sumá fuentes desde **01 Fuentes** y mezclalas en **02 Mixer**.
3. Ajustá envolvente, filtro, LFO y efectos.
4. En **08 Exportar**, poné un nombre y descargá el `.zip`.
5. Descomprimí y copiá la carpeta a `dust/code/` de tu norns.

La guía completa está en [`docs/GUIA.md`](docs/GUIA.md).

## Idiomas

La app detecta el idioma del navegador. También se puede elegir desde ⚙ o forzar con la URL:

| Idioma | Enlace |
|---|---|
| Español | [`?lang=es`](https://buenosairesfront.github.io/nornssoundcreator/?lang=es) |
| English | [`?lang=en`](https://buenosairesfront.github.io/nornssoundcreator/?lang=en) |
| Deutsch | [`?lang=de`](https://buenosairesfront.github.io/nornssoundcreator/?lang=de) |
| 中文 | [`?lang=zh`](https://buenosairesfront.github.io/nornssoundcreator/?lang=zh) |
| 日本語 | [`?lang=ja`](https://buenosairesfront.github.io/nornssoundcreator/?lang=ja) |
| हिन्दी | [`?lang=hi`](https://buenosairesfront.github.io/nornssoundcreator/?lang=hi) |

Cómo funciona la traducción y cómo sumar un idioma: [`docs/IDIOMAS.md`](docs/IDIOMAS.md).

## Documentación

- [`docs/GUIA.md`](docs/GUIA.md): guía de uso, sección por sección.
- [`docs/EXPORTAR.md`](docs/EXPORTAR.md): formatos de exportación y cómo instalarlos.
- [`docs/IDIOMAS.md`](docs/IDIOMAS.md): idiomas, `?lang=` y cómo agregar uno nuevo.
- [`docs/ARQUITECTURA.md`](docs/ARQUITECTURA.md): cómo está hecho el código.
- [`docs/PUBLICAR.md`](docs/PUBLICAR.md): GitHub Pages y enlace desde la landing de Buenos Aires Front.
- [`CHANGELOG.md`](CHANGELOG.md): historial de cambios.

## Correr en local

Es un único archivo HTML sin dependencias de build:

```sh
git clone https://github.com/buenosairesfront/nornssoundcreator
cd nornssoundcreator
python3 -m http.server 8000
# abrir http://localhost:8000
```

También funciona abriendo `index.html` directo en Chrome, aunque algunos navegadores limitan el AudioWorklet en `file://` (la app cae al modo compatible).

## Compatibilidad

- Chrome / Edge (escritorio y Android): completo, incluido MIDI.
- Safari / Firefox: audio y exportación; sin Web MIDI en Firefox ni Safari.
- El audio del navegador es una aproximación (marcada con ≈). El `.sc` exportado es el sonido real en norns.

---

## English

Sound design for norns and SuperCollider in the browser. Build an engine from 62 sources, filter, envelope, LFO and effects, hear it live, and export a ready norns script (`.lua` + `Engine_*.sc`), a SuperCollider `.scd`, Faust code for VST/AU, or an installable web app. The interface is available in Spanish, English, German, Chinese, Japanese and Hindi. Try it: https://buenosairesfront.github.io/nornssoundcreator/?lang=en

## Deutsch

Sounddesign für norns und SuperCollider im Browser. Baue eine Engine aus 62 Quellen, Filter, Hüllkurve, LFO und Effekten, höre sie live und exportiere ein fertiges norns-Skript, SuperCollider-`.scd`, Faust-Code für VST/AU oder eine installierbare Web-App. Ausprobieren: https://buenosairesfront.github.io/nornssoundcreator/?lang=de

## 中文

在浏览器中为 norns 和 SuperCollider 设计声音。用 62 种音源、滤波器、包络、LFO 和效果器搭建引擎,实时试听,并导出可直接使用的 norns 脚本、SuperCollider `.scd`、用于 VST/AU 的 Faust 代码或可安装的网页应用。试用:https://buenosairesfront.github.io/nornssoundcreator/?lang=zh

## 日本語

ブラウザで norns と SuperCollider のサウンドをデザイン。62 種類の音源、フィルター、エンベロープ、LFO、エフェクトでエンジンを組み、その場で試聴し、norns スクリプト、SuperCollider `.scd`、VST/AU 用 Faust コード、インストール可能な Web アプリとして書き出せます。試す:https://buenosairesfront.github.io/nornssoundcreator/?lang=ja

## हिन्दी

ब्राउज़र में norns और SuperCollider के लिए साउंड डिज़ाइन। 62 स्रोतों, फ़िल्टर, एनवेलप, LFO और इफ़ेक्ट से इंजन बनाएँ, तुरंत सुनें, और तैयार norns स्क्रिप्ट, SuperCollider `.scd`, VST/AU के लिए Faust कोड या इंस्टॉल होने वाला वेब ऐप निर्यात करें। आज़माएँ: https://buenosairesfront.github.io/nornssoundcreator/?lang=hi
