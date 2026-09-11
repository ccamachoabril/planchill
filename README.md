# Planchill

Sitio estático (sin build) con intro de video controlado por scroll + itinerario del 19 de septiembre.

## Estructura
- `index.html` — todo el sitio (intro + app), HTML/CSS/JS plano, sin dependencias.
- `assets/intro.mp4` — video del intro (720×1280, 8s, controlado por scroll).
- `vercel.json` — headers de caché para el video.

## Cómo funciona el intro
La sección `#introScrub` mide 400vh. Mientras el usuario hace scroll dentro de esa altura,
el script calcula el progreso (0 a 1) y lo mapea a `video.currentTime`. Al llegar a 1,
el scroll continúa de forma natural hacia la app del itinerario que va justo debajo.
El texto "Desliza hacia abajo" se desvanece apenas empieza el scroll.

## Publicar en GitHub + Vercel
```bash
# 1. Clona o entra a tu repo local de planchill
git clone https://github.com/ccamachoabril/planchill.git
cd planchill

# 2. Reemplaza el contenido con estos archivos (index.html, assets/, vercel.json)
#    (borra el index.html viejo primero)

# 3. Commit y push
git add .
git commit -m "Intro con video scroll-driven + itinerario"
git push origin main
```

Si el repo ya está conectado a Vercel, el deploy se dispara solo con el push.
Si no, en vercel.com → "Add New Project" → importa `ccamachoabril/planchill`.

## Notas
- El video pesa ~3.2 MB; en 4G carga rápido, pero si quieres optimizarlo más se puede
  recomprimir (bajar bitrate o usar WebM adicional).
- Si en algún momento cambias la duración/resolución del video, no hay que tocar el JS:
  usa `video.duration` dinámicamente.
