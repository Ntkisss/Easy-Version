# Stumble Cups · El Reto Imposible

Juego web (HTML/CSS/JS puro, sin dependencias) en el que hay que sobrevivir **55 segundos** a una tormenta de proyectiles cada vez más caótica. Un solo golpe = reinicio total. Si lo completas, se desbloquea la imagen del trofeo con animación de confeti.

## Estructura del proyecto

```
worldcups/
├── index.html
└── assets/
    └── trofeo.jpg   ← tu imagen del trofeo
```

Todo es estático: no hay backend ni build step. Funciona directamente abriendo `index.html`, y también funciona perfecto en GitHub Pages.

## Cómo publicarlo en GitHub Pages (paso a paso)

1. **Crea un repositorio nuevo en GitHub**
   - Ve a github.com → botón verde "New repository".
   - Ponle un nombre, por ejemplo `stumble-cups-reto`.
   - Puede ser público o privado (GitHub Pages gratis requiere que sea público, salvo que tengas GitHub Pro/Team).
   - No marques "Add a README" si vas a subir el que ya tienes.

2. **Sube los archivos**
   - Opción fácil (sin terminal): en la página del repo recién creado, haz clic en **"uploading an existing file"**, arrastra `index.html` y la carpeta `assets` (con `trofeo.jpg` dentro) y haz commit.
   - Opción con terminal:
     ```bash
     cd worldcups
     git init
     git add .
     git commit -m "Reto Stumble Cups"
     git branch -M main
     git remote add origin https://github.com/TU-USUARIO/stumble-cups-reto.git
     git push -u origin main
     ```

3. **Activa GitHub Pages**
   - En el repositorio, ve a **Settings → Pages** (menú lateral izquierdo).
   - En "Build and deployment" → "Source", elige **"Deploy from a branch"**.
   - En "Branch", selecciona `main` y la carpeta `/ (root)`.
   - Pulsa **Save**.

4. **Espera 1-2 minutos**
   - GitHub construye la página automáticamente. Verás un mensaje verde con la URL final, con esta forma:
     ```
     https://TU-USUARIO.github.io/stumble-cups-reto/
     ```
   - Esa es tu web ya publicada, funcionando para cualquiera que entre.

5. **Actualizaciones futuras**
   - Cada vez que subas cambios (nuevo commit / nuevo archivo) a la rama `main`, GitHub Pages se actualiza solo en 1-2 minutos. No hace falta repetir la configuración.

## Notas sobre la dificultad

El juego está diseñado para ser extremadamente difícil pero justo (no aleatoriamente injusto):
- El jugador se mueve con precisión total (ratón, dedo o teclado), sin inercia rara.
- La dificultad escala en 4 fases (lluvia de proyectiles → láseres de barrido → perseguidores → caos final con ráfagas radiales).
- Un solo contacto reinicia el intento completo, sin checkpoints ni vidas extra.
- 55 segundos de esquive perfecto es un listón muy alto: pensado para que, de cada ~1000 intentos, muy pocos jugadores lleguen al final. Si notas que se pasa "demasiado fácil" o "demasiado difícil" en pruebas reales, puedes ajustar `WIN_TIME` (segundos requeridos) y las fórmulas `spawnInterval` / velocidades dentro del `<script>` de `index.html`.

## Cómo cambiar la imagen desbloqueable

Sustituye `assets/trofeo.jpg` por la imagen que quieras (mismo nombre de archivo, o cambia la ruta en el `<img>` e `href` del `index.html`).


## Trofeo fuera de GitHub

El repositorio no necesita contener `assets/trofeo.jpg`.

1. Sube `trofeo.jpg` a un servicio de alojamiento de imágenes que te dé una **URL directa pública** al archivo.
2. Abre `index.html`.
3. Busca `const TROPHY_URL = "PEGA_AQUI_LA_URL_DIRECTA_DE_TROFEO.jpg";`.
4. Sustitúyela por la URL directa de tu imagen.
5. Sube a GitHub únicamente `index.html` y `README.md`.

Importante: esto evita que `trofeo.jpg` esté en el repositorio, pero no convierte la imagen en secreta. Como el navegador necesita descargarla después de ganar, una persona puede descubrir su URL inspeccionando la página.
