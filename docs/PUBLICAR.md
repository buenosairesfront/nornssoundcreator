# Publicar y enlazar

## GitHub Pages

La app se sirve con GitHub Pages desde la rama `main`, carpeta raíz:

**https://buenosairesfront.github.io/nornssoundcreator/**

Si hay que activarlo de nuevo: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main` / `(root)` → Save**. El archivo `.nojekyll` evita que GitHub procese el sitio con Jekyll.

Cada push a `main` actualiza la página en uno o dos minutos.

## Landing de Buenos Aires Front

En la landing, la fila **Norns Sound Creator** de la sección "Apps web" usa estas dos claves del objeto `LINKS`:

```js
repos: { sound: "https://github.com/buenosairesfront/nornssoundcreator", ... },
demos: { sound: "https://buenosairesfront.github.io/nornssoundcreator/", ... },
```

- **Probar ↗** abre la app. Sin `?lang=`, la app usa el idioma del navegador del visitante.
- **Código** abre este repositorio.

Para enlazar un idioma concreto, sumá `?lang=` a la URL:

```
https://buenosairesfront.github.io/nornssoundcreator/?lang=es
https://buenosairesfront.github.io/nornssoundcreator/?lang=en
https://buenosairesfront.github.io/nornssoundcreator/?lang=de
https://buenosairesfront.github.io/nornssoundcreator/?lang=zh
https://buenosairesfront.github.io/nornssoundcreator/?lang=ja
https://buenosairesfront.github.io/nornssoundcreator/?lang=hi
```

## Instalar un script de norns desde maiden

Los scripts que exporta la app no se instalan con `;install` (eso es para repositorios de scripts). Se descomprimen y se copian a `dust/code/`, como explica [EXPORTAR.md](EXPORTAR.md).
