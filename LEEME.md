# Sitio web del Bosque Escuela El Cacomixtle

Sitio estático con seis secciones (Inicio, Mapa 3D, Repositorio, Anuncios, Kids y Contacto). Anuncios y actividades Kids se editan en `datos/anuncios.json` y `datos/kids.json`. No necesita base de datos.

## Estructura

```
index.html               página completa (textos, estilos y código)
lib/                     three.js r128 y OrbitControls (visor 3D)
datos/terreno.png        alturas del DSM remuestreadas a 1 m (cm sobre la altitud mínima = R*256 + G)
datos/terreno.json       georreferencia de la malla (UTM 14 N, EPSG:32614)
datos/ortofoto_4096.jpg  ortofoto para la textura (≈25 cm/px)
datos/ortofoto_8192.jpg  ortofoto en alta resolución (≈12.5 cm/px), solo en equipos que la soportan
datos/curvas.svg         curvas de nivel cada 5 m derivadas del DSM suavizado
datos/trabajos.json      lista de trabajos del repositorio y sus sitios en el mapa
```

Todo se generó a partir de los productos del vuelo del 11/11/2026: `...-dsm.tif` y `...-orthophoto.jpg`.

## Cómo verlo en tu computadora

Por seguridad, los navegadores no cargan los datos del mapa si abres `index.html` con doble clic. Ábrelo con un servidor local:

```
cd "SITIO WEB BOSQUE ESCUELA"
python -m http.server 8000
```

Luego entra a http://localhost:8000. Para publicarlo en internet, sube la carpeta completa a GitHub Pages, Netlify o al servidor de tu institución.

## Cómo editar

- **Textos de Información y Contacto:** en `index.html`, busca los comentarios `EDITAR AQUÍ`.
- **Agregar trabajos:** agrega registros a `datos/trabajos.json`. El campo `sitio` acepta `{"E":…, "N":…}` (UTM 14 N) o `{"lat":…, "lon":…}`. Usa `null` si el trabajo abarca todo el bosque.
- **Ubicar un sitio con clic:** en el Mapa 3D, usa "Registrar sitio" y luego "Copiar JSON" para obtener el bloque que va en `trabajos.json`.

## Publicarlo gratis en GitHub Pages

1. Crea una cuenta en https://github.com.
2. Crea un repositorio público (por ejemplo, `bosque-escuela`).
3. En el repositorio, entra a "Add file" → "Upload files" y arrastra el **contenido** de esta carpeta: `index.html` y las carpetas `datos`, `img` y `lib`. No arrastres la carpeta que los contiene. Después pulsa "Commit changes".
4. Entra a Settings → Pages. En "Source", elige "Deploy from a branch"; en "Branch", elige `main` y `/ (root)`. Pulsa "Save".
5. En unos minutos el sitio queda en `https://TU-USUARIO.github.io/bosque-escuela/`.
