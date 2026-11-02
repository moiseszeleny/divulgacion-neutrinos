# Divulgación de neutrinos · Puertas Abiertas IF-UNAM 2026

Animaciones interactivas que acompañan el cartel **“Neutrinos: las partículas fantasma”**, presentado el 13 de noviembre de 2026 en el día de Puertas Abiertas del Instituto de Física de la UNAM.

Sitio: **https://moiseszeleny.github.io/divulgacion-neutrinos/**

| Página | Qué muestra |
|---|---|
| `/` | Inicio, con acceso a las tres experiencias |
| `/oscilaciones/` | Oscilaciones de tres sabores en el vacío (fórmula exacta, parámetros NuFIT 6.0) con cinco escenarios: reactor, DUNE, neutrinos atmosféricos y los dos viajes del cartel (ver abajo) |
| `/cherenkov/` | Frentes de onda y cono de Cherenkov (hielo, agua y aire) y un evento simulado en IceCube, con los colores según el tiempo de llegada |
| `/via-lactea/` | La Vía Láctea vista con neutrinos (IceCube, 2023): luz visible con la emisión de neutrinos en azul |

Todo es HTML, CSS y JavaScript sin dependencias ni fuentes externas: cada página pesa menos de 30 KB (más la imagen de 233 KB en `/via-lactea/`, en total menos de 300 KB) y funciona con mala señal.

### Escenarios de oscilaciones del cartel

- **Desde NGC 1068:** a 47 millones de años luz las oscilaciones son tan rápidas que solo cuenta el promedio, P̄(α→β) = Σᵢ |U_αi|² |U_βi|². La energía y la distancia no cambian el resultado, así que sus deslizadores se desactivan. El botón **Mezcla de origen 1 : 2 : 0** parte de la mezcla que producen los piones (νe:νμ:ντ ≈ 1:2:0) y muestra que llega casi en 1:1:1 (≈ 30 % : 35 % : 34 %).
- **De CU a IceCube:** νμ de 25 GeV a lo largo de la cuerda de 10 400 km entre la Ciudad de México y el Polo Sur (la energía a la que IceCube DeepCore mide esta oscilación). Fórmula en el vacío, sin el efecto MSW.

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

## Imagen real de la Vía Láctea

`/via-lactea/` muestra la composición de IceCube (la Vía Láctea en luz visible con la emisión de neutrinos en azul), incluida en el repositorio: `assets/img/via-lactea-neutrinos.jpg`, 1600 × 800 px, 233 KB.

| Fuente | Crédito | Licencia |
|---|---|---|
| [Comunicado de IceCube, 29 jun 2023](https://icecube.wisc.edu/news/press-releases/2023/06/our-galaxy-seen-through-a-new-lens-neutrinos-detected-by-icecube/) (composición artística) | IceCube Collaboration/U.S. National Science Foundation (Lily Le & Shawn Johnson)/ESO (S. Brunier) | Imagen de prensa, se reproduce con crédito |
| Fondo en luz visible: [ESO eso0932a, “The Milky Way panorama”](https://www.eso.org/public/images/eso0932a/) | ESO/S. Brunier | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es) |

Modificaciones: se recortó a 2:1, se reproyectó ligeramente con una transformación afín (de una versión anterior que la alineaba con la panorámica de ESO), se redimensionó y se comprimió a menos de 250 KB. El crédito aparece al pie de la imagen y en el pie de la página.

## Física y fuentes

- Parámetros de oscilación: ajuste global NuFIT 6.0 (2024), ordenamiento normal, valores aproximados. La simulación es en el vacío y no incluye el efecto MSW.
- Cherenkov: cos θ = 1/(nβ), con n = 1.31 (hielo), 1.33 (agua) y 1.0003 (aire).
- IceCube Collaboration, “Observation of high-energy neutrinos from the Galactic plane”, *Science* 380, 1338 (2023), [doi:10.1126/science.adc9818](https://doi.org/10.1126/science.adc9818).
- IceCube Collaboration, “Evidence for neutrino emission from the nearby active galaxy NGC 1068”, *Science* 378, 538 (2022), [doi:10.1126/science.abg3395](https://doi.org/10.1126/science.abg3395).
- Premio Nobel de Física 2026: Francis Halzen ([nobelprize.org](https://www.nobelprize.org/prizes/physics/2026/summary/)).

## Pendientes

- [x] Enlace al Departamento de Física Teórica en `index.html`.
- [x] Mostrar la imagen real de IceCube en `/via-lactea/` (sin comparador), con su crédito.
- [x] Escenarios del cartel en oscilaciones: «Desde NGC 1068» (promedio y mezcla 1:2:0) y «De CU a IceCube».
- [x] Cherenkov: los neutrinos llegan desde abajo, tras cruzar la Tierra.
- [ ] Probar los QR impresos al tamaño final.

## Licencia

Código bajo licencia [MIT](LICENSE). Textos bajo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es). Las imágenes de terceros conservan su propia licencia.
