# MeryanShop

Página web de MeryanShop, tienda de perfumes originales bajo pedido. Catálogo completo (420 productos) migrado desde el negocio original.

## Estructura

```
index.html               sitio completo (HTML + CSS + JS)
assets/data/products.js   catálogo completo: window.PRODUCTS = [ {name, dop, priceLabel, size, cat, tag, page, slot}, ... ]
assets/img/catalogo-1..4.webp   mosaicos fotográficos reales del catálogo (cada uno cubre 9 páginas de productos)
```

Las fotos de los productos no son un archivo por perfume: cada `catalogo-N.webp` es un
mosaico con muchas fotos, y cada producto tiene `page`/`slot` para ubicar su recorte dentro
del mosaico (función `visualFor()` en `index.html`, misma técnica que el catálogo original).

## Cómo ver el sitio localmente

Abre `index.html` directamente en el navegador (funciona sin servidor, porque el catálogo
se carga con un `<script src="assets/data/products.js">`, no con `fetch`):

```bash
start index.html
```

## Moneda

- El precio maestro de cada producto está en RD$ (pesos dominicanos, moneda real del
  negocio). USD y CLP se calculan a partir de `RATES` en `index.html`.
- **Tasas de cambio**: la constante `RATES` (USD:1, DOP:60, CLP:950) es aproximada.
  Actualízala antes de publicar.
- **Detección automática por país**: al cargar la página, `detectCurrencyByCountry()`
  consulta `https://ipapi.co/json/` (servicio gratuito de geolocalización por IP) y cambia
  la moneda activa según el país del visitante (República Dominicana → RD$, Chile → CLP$,
  Estados Unidos → USD; cualquier otro país se queda en USD). El visitante puede cambiarla
  manualmente en cualquier momento con los botones de arriba. Si el servicio de
  geolocalización falla o está bloqueado, el sitio simplemente se queda en USD.

## Agregar o editar productos

Edita `assets/data/products.js`. Cada producto es un objeto:

```js
{name:"Dior Sauvage EDP", dop:10650, priceLabel:"RD$10,650", size:"100 ML", cat:"Hombre", tag:"Intenso", page:12, slot:7}
```

- `dop`: precio en pesos dominicanos (número, se usa para calcular USD/CLP).
- `cat`: "Hombre", "Mujer" o "Unisex".
- `tag`: estilo mostrado como etiqueta (Fresco, Dulce, Elegante, Intenso, Amaderado, Árabe).
- `page`/`slot`: en qué mosaico y posición está su foto. Si agregas un producto nuevo sin
  foto propia en los mosaicos existentes, puedes darle `page`/`slot` de otro producto similar
  (compartirán foto) o subir una imagen propia y usar un campo `img` en vez de `page`/`slot`
  (requiere adaptar `photoStyle()` para usar `<img>` en ese caso).

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (puede ser público o privado, pero Pages gratis requiere público en cuentas free).
2. Sube estos archivos (`index.html`, `assets/`, este `README.md`).
3. En el repo: **Settings → Pages → Source: branch `main`, carpeta `/root`**.
4. El sitio quedará disponible en `https://<tu-usuario>.github.io/<nombre-repo>/`.
