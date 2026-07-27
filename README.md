# Fincas del Canal — web de inmuebles en Frómista

## 1. Cómo añadir/editar inmuebles
Abre `index.html`, busca el array `const properties = [...]` (dentro de `<script>`) y copia/edita un bloque por cada inmueble:

```js
{
  id: "identificador-unico",
  tipo: "Casa" | "Terreno rústico" | "Solar urbano" | lo que quieras,
  titulo: "Título del anuncio",
  km: "0.5 km",              // distancia orientativa a la iglesia, solo referencia
  precio: "75.000 €",
  m2: "140 m²",
  habitaciones: "3 hab.",
  descripcion: "Texto libre del anuncio.",
  lat: 42.2672,               // coordenadas exactas (clic derecho en Google Maps > "¿Qué hay aquí?")
  lng: -4.4021,
  fotos: ["foto1.jpg", "foto2.jpg"]   // nombres de archivo en la carpeta /images
}
```

Para borrar un inmueble, borra su bloque entero. El catálogo se genera solo a partir de esta lista.

Ahora mismo hay 6 fichas de ejemplo para que veas variedad de producto: 2 casas, 1 solar urbano edificable, 1 terreno de secano (labor), 1 parcela con chopera junto al canal y 1 finca de regadío con derechos de agua. Sustitúyelas todas por tus inmuebles reales cuando los tengas listos.

## 2. Fotos de los inmuebles
Coloca las fotos dentro de la carpeta `images/`, con el mismo nombre de archivo que pusiste en `fotos: [...]`.
Si falta una foto, la web muestra automáticamente un marcador de posición para que sepas cuál falta.
Recomendado: fotos en formato .jpg, máx. 1600px de ancho, para que cargue rápido.

## 3. Fotos de la sección "El pueblo" — cómo conseguirlas reales
Esta sección usa 3 fotos fijas del propio pueblo (no de inmuebles), que van en `images/`:
- `pueblo-iglesia.jpg` — Iglesia de San Martín de Tours
- `pueblo-esclusas.jpg` — Esclusas del Canal de Castilla
- `pueblo-gastronomia.jpg` — algún plato típico o una mesa/bar del pueblo

No puedo descargar y colocar yo mismo fotos de internet en tu web: son de terceros y, salvo que tengan licencia libre y las cites, no se pueden reutilizar así sin más (derechos de autor). Tienes tres opciones, de mejor a peor:

1. **Fotos propias** (la mejor opción): la próxima vez que estés en Frómista, un móvil basta para la iglesia, las esclusas y una mesa con algo de comer. Da autenticidad real a la web y es la única forma de tener fotos que nadie más tiene.
2. **Wikimedia Commons** (gratis, con atribución obligatoria): busca en https://commons.wikimedia.org las categorías *"Church of Saint Martin of Tours, Frómista"* y *"Canal de Castilla"*. La mayoría de las fotos allí son de licencia libre (normalmente CC BY-SA). Pasos:
   - Descarga la imagen y guárdala en `images/` con el nombre correspondiente.
   - En el HTML, sustituye el texto `[tu nombre / autor y licencia si es de un banco de imágenes]` que aparece bajo cada foto, por ejemplo: `Foto: José-Manuel Benito / Wikimedia Commons (CC BY-SA 3.0)`.
   - Si prefieres no mostrar el crédito, puedes borrar esa línea `<span class="photo-credit">...</span>`, pero comprueba antes que la licencia de esa foto en concreto no exige atribución visible.
3. **Banco de imágenes de pago** (Shutterstock, iStock...) si quieres algo muy pulido y sin depender de lo que haya libre.

Evita coger fotos directamente de blogs de turismo o periódicos: la mayoría no están libres, aunque las veas repetidas en muchas webs.

## 4. Conectar el formulario de contacto (gratis, envía email real)
1. Ve a https://formspree.io y crea una cuenta gratuita (hasta 50 envíos/mes).
2. Crea un formulario nuevo y copia el "Form ID" o la URL tipo `https://formspree.io/f/xxxxxxx`.
3. En `index.html`, busca la línea:
   ```js
   const FORMSPREE_ENDPOINT = "https://formspree.io/f/YOUR_FORM_ID";
   ```
   y sustituye `YOUR_FORM_ID` por el tuyo.
4. Formspree te enviará los mensajes a tu email de forma automática.

Mientras no lo conectes, el formulario avisa al visitante de que use WhatsApp o email directo (ya configurados en el bloque `direct-contact`).

## 5. Cambiar tus datos de contacto
Busca en `index.html` esta sección y sustituye por tus datos reales:
```html
<a href="tel:+34600000000">📞 +34 600 000 000</a>
<a href="https://wa.me/34600000000">💬 WhatsApp directo</a>
<a href="mailto:info@fincasdelcanal.es">✉️ info@fincasdelcanal.es</a>
```
(El número de WhatsApp va sin "+" ni espacios en el enlace `wa.me/`.)

## 6. Publicarla gratis en GitHub Pages
1. Crea una cuenta en https://github.com si no tienes.
2. Crea un repositorio nuevo, por ejemplo `fincas-fromista`.
3. Sube estos dos elementos al repositorio: `index.html` y la carpeta `images/` (con tus fotos dentro).
4. En el repositorio, ve a **Settings → Pages**.
5. En "Source", elige la rama `main` y la carpeta `/ (root)` → Guardar.
6. En un par de minutos tu web estará publicada en:
   `https://TU-USUARIO.github.io/fincas-fromista/`

No hace falta servidor, base de datos ni pagar hosting.

## 7. Dominio propio (opcional, más adelante)
Si más adelante quieres algo como `fincasdelcanal.es`, puedes comprar el dominio (unos 10€/año) y apuntarlo a GitHub Pages desde el mismo panel de Settings → Pages → Custom domain. Esto es opcional; la web funciona perfectamente con la URL gratuita de github.io.
