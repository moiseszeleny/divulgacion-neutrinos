# Divulgación de neutrinos · Puertas Abiertas IF-UNAM 2026

Animaciones interactivas que acompañan el cartel **“Neutrinos: las partículas fantasma”**, presentado el 13 de noviembre de 2026 en el día de Puertas Abiertas del Instituto de Física de la UNAM.

Sitio: **https://moiseszeleny.github.io/divulgacion-neutrinos/**

| Página | Qué muestra |
|---|---|
| `/` | Inicio, con acceso a las tres experiencias |
| `/oscilaciones/` | Oscilaciones de tres sabores en el vacío (fórmula exacta, parámetros NuFIT 6.0) con escenarios de reactor, DUNE y neutrinos atmosféricos |
| `/cherenkov/` | Frentes de onda y cono de Cherenkov (hielo, agua y aire) y un evento simulado en IceCube, con los colores según el tiempo de llegada |
| `/via-lactea/` | Comparación entre la Vía Láctea en luz visible y en neutrinos (IceCube, 2023) |

Todo es HTML, CSS y JavaScript sin dependencias ni fuentes externas: cada página pesa menos de 30 KB y funciona con mala señal.

## Códigos QR y redirecciones

Los QR del cartel **no apuntan directo a las animaciones**, sino a páginas cortas de redirección:

| QR (carpeta `qr/`) | URL impresa | Redirige a |
|---|---|---|
| `qr-oscilaciones` | `…/divulgacion-neutrinos/q/osc/` | `/oscilaciones/` |
| `qr-cherenkov` | `…/divulgacion-neutrinos/q/cherenkov/` | `/cherenkov/` |
| `qr-via-lactea` | `…/divulgacion-neutrinos/q/galaxia/` | `/via-lactea/` |

Así puedes cambiar el destino después de imprimir: basta con editar `q/<nombre>/index.html`. **No renombres las carpetas de `q/`**, porque los QR impresos dejarían de funcionar.

Los QR vienen en SVG (vectorial, el mejor para imprimir) y en PNG. Imprímelos de al menos 3 × 3 cm y pruébalos con Android y con iPhone antes de mandar el cartel a la imprenta.

## Subir el repositorio desde WSL

1. Abre WSL y entra a la carpeta. Si la unidad `P:` no aparece en `/mnt/p`, móntala primero:
   ```bash
   sudo mkdir -p /mnt/p && sudo mount -t drvfs P: /mnt/p
   cd "/mnt/p/My_papers/Eventos/Puertas abiertas IFUNAM 2026/divulgacion-neutrinos"
   ```
2. Crea el repositorio y súbelo.

   **Opción A, con GitHub CLI** (si tienes `gh` y ya iniciaste sesión con `gh auth login`):
   ```bash
   git init -b main
   git add .
   git commit -m "Animaciones de neutrinos para Puertas Abiertas IF-UNAM 2026"
   gh repo create moiseszeleny/divulgacion-neutrinos --public --source=. --push
   ```
   **Opción B, solo con git:** crea en github.com un repositorio público vacío llamado `divulgacion-neutrinos` (sin README) y luego ejecuta:
   ```bash
   git init -b main
   git add .
   git commit -m "Animaciones de neutrinos para Puertas Abiertas IF-UNAM 2026"
   git remote add origin git@github.com:moiseszeleny/divulgacion-neutrinos.git   # o https://github.com/moiseszeleny/divulgacion-neutrinos.git
   git push -u origin main
   ```
   Si git marca la carpeta como insegura (pasa en unidades de Windows), ejecuta
   `git config --global --add safe.directory "$(pwd)"`.

## Activar GitHub Pages

1. En GitHub, abre el repositorio y ve a **Settings → Pages**.
2. En **Build and deployment**, elige **Source: Deploy from a branch**.
3. En **Branch**, selecciona **`main`** y la carpeta **`/ (root)`**, y luego **Save**.
4. Espera de 1 a 3 minutos. La página aparecerá en https://moiseszeleny.github.io/divulgacion-neutrinos/.
5. Abre las tres URL de `q/` desde el celular para confirmar que redirigen bien.

El archivo `.nojekyll` evita que GitHub procese el sitio con Jekyll. Cada `git push` a `main` actualiza el sitio en un par de minutos.

## Probar en tu computadora

```bash
python3 -m http.server 8000
# abre http://localhost:8000
```

## Imágenes reales de la Vía Láctea (opcional)

Mientras no haya imágenes, `/via-lactea/` muestra una **ilustración esquemática** generada en el navegador. Para usar las imágenes reales:

1. Descarga la imagen de la Vía Láctea en neutrinos y la versión en luz visible del comunicado de IceCube (junio de 2023).
2. **Revisa su licencia de uso** y el crédito exacto que piden. El crédito publicado con el comunicado es del tipo *IceCube Collaboration / U.S. National Science Foundation (Lily Le & Shawn Johnson) / ESO (S. Brunier)*; verifícalo en la fuente.
3. Guárdalas como `assets/img/via-lactea-optica.jpg` y `assets/img/via-lactea-neutrinos.jpg`, recortadas a la misma proyección y proporción 2:1, de unos 1600 × 800 px y menos de 250 KB cada una.
4. La página las detecta sola. Si cambia el crédito, actualiza el texto en `via-lactea/index.html`.

## Física y fuentes

- Parámetros de oscilación: ajuste global NuFIT 6.0 (2024), ordenamiento normal, valores aproximados. La simulación es en el vacío y no incluye el efecto MSW.
- Cherenkov: cos θ = 1/(nβ), con n = 1.31 (hielo), 1.33 (agua) y 1.0003 (aire).
- IceCube Collaboration, “Observation of high-energy neutrinos from the Galactic plane”, *Science* 380, 1338 (2023), [doi:10.1126/science.adc9818](https://doi.org/10.1126/science.adc9818).
- Premio Nobel de Física 2026: Francis Halzen ([nobelprize.org](https://www.nobelprize.org/prizes/physics/2026/summary/)).

## Pendientes

- [x] Enlace al Departamento de Física Teórica en `index.html`.
- [ ] Agregar las imágenes reales de la Vía Láctea, con su crédito.
- [ ] Probar los QR impresos al tamaño final.

## Licencia

Código bajo licencia [MIT](LICENSE). Textos bajo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es). Las imágenes de terceros conservan su propia licencia.
