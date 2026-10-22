# Idiomas

Norns Sound Creator está traducido a seis idiomas:

| Código | Idioma | `lang` del documento |
|---|---|---|
| `es` | Español (idioma base) | `es` |
| `en` | English | `en` |
| `de` | Deutsch | `de` |
| `zh` | 中文 (chino simplificado) | `zh-Hans` |
| `ja` | 日本語 | `ja` |
| `hi` | हिन्दी | `hi` |

## Cómo se elige el idioma

En este orden de prioridad:

1. **Parámetro de URL** `?lang=xx`, por ejemplo `index.html?lang=zh`. Sirve para enlazar a un idioma concreto desde la landing de Buenos Aires Front u otro sitio. También queda guardado como preferencia.
2. **Preferencia guardada**: lo último que se eligió en ⚙ → Idioma (se guarda en `localStorage`, clave `nsc.settings`).
3. **Idioma del navegador** (`navigator.language`), si es uno de los seis.
4. **Español** como valor por defecto.

## Qué se traduce

- Toda la interfaz: secciones, controles, notas, avisos y mensajes.
- Los nombres de los controles de carácter de cada fuente y de los parámetros de los efectos.
- La **web app exportada**: su interfaz sale en el idioma activo al exportarla.

No se traducen, a propósito:

- Los nombres de UGens y efectos de SuperCollider (`SinOsc`, `RLPF`, `FreeVerb`…), porque son nombres técnicos.
- El código exportado (`.lua`, `.sc`, `.scd`, `.dsp`): los identificadores y parámetros tienen que coincidir con norns y SuperCollider.
- El archivo de instrucciones de la web app exportada: `LEEME.txt` en español y `README.txt` en inglés para el resto.

## Tipografías

Barlow Condensed e IBM Plex Mono no tienen caracteres CJK ni devanagari, así que el CSS cae a fuentes del sistema: Noto Sans JP para japonés, Noto Sans SC / PingFang SC / Microsoft YaHei para chino y Noto Sans Devanagari para hindi.

## Agregar un idioma

Todo está en `index.html`.

1. **Diccionario principal.** Buscá `const I18N={`. Copiá el bloque `en:{…}` y traducí los valores (no las claves). Hoy hay 160 claves y todas tienen que estar.
2. **Lista de idiomas.** Buscá `const LANGS=` y `const LANG_NAMES=` y sumá el código y el nombre en su propio idioma.
3. **Web app exportada.** Buscá `const TT={` dentro de `webAppMain` y sumá un bloque con las mismas claves que `en`. Después sumá el código en la lista de `genWebFiles` (`['es','en','de','zh','ja','hi'].includes(lang)`).
4. **Tipografía.** Si el alfabeto no es latino, agregá una fuente de respaldo en `--disp` y `--mono`.
5. **Probar.** Abrí `index.html?lang=xx` y recorré todas las secciones. Si falta una clave, la app muestra el texto en español.

Para comprobar que no falte ninguna clave, se puede correr esto con Node en la raíz del repo:

```sh
node -e "
const h=require('fs').readFileSync('index.html','utf8');
const s=[...h.matchAll(/<script>([\s\S]*?)<\/script>/g)].map(m=>m[1]).find(x=>x.includes('const I18N='));
const I=new Function(s+';return I18N')(); const ref=Object.keys(I.en);
for(const k in I) console.log(k, ref.filter(x=>!(x in I[k])).join(',')||'ok');"
```
