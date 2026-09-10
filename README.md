# MeryanShop

Página web de una sola pieza (`index.html`) para MeryanShop, tienda de perfumes originales bajo pedido.

## Estructura

```
index.html          sitio completo (HTML + CSS + JS en un solo archivo)
assets/img/          imágenes del catálogo
  placeholder-*.svg   6 placeholders por estilo (fresco, dulce, elegante, intenso, amaderado, arabe)
```

## Cómo ver el sitio localmente

Abre `index.html` directamente en el navegador, o desde una terminal en esta carpeta:

```bash
start index.html
```

## Pendientes

1. **Fotos reales de los perfumes**: reemplazar los placeholders SVG con fotos reales.
   Sube tus imágenes a `assets/img/` y agrega el campo `img` a cada producto en el arreglo
   `PRODUCTS` dentro del `<script>` de `index.html`, por ejemplo:
   ```js
   {name:"Ámbar Nocturno", cat:"Hombre", tag:"Amaderado", usd:42, img:"assets/img/ambar-nocturno.jpg"}
   ```
2. **Tasas de cambio**: la constante `RATES` en `index.html` tiene valores aproximados
   (USD:1, DOP:60, CLP:950). Actualízalas antes de publicar.
3. **Catálogo completo**: hoy hay 15 productos de muestra en el arreglo `PRODUCTS`. Para un
   catálogo grande (cientos de productos) conviene mover los datos a un `products.json`
   separado y cargarlo con `fetch` en vez de tenerlo hardcodeado en el HTML.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (puede ser público o privado, pero Pages gratis requiere público en cuentas free).
2. Sube estos archivos (`index.html`, `assets/`, este `README.md`).
3. En el repo: **Settings → Pages → Source: branch `main`, carpeta `/root`**.
4. El sitio quedará disponible en `https://<tu-usuario>.github.io/<nombre-repo>/`.
