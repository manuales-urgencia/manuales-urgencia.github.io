# Manuales de urgencia — cómo trabajar en este repo

Este repo es el sitio <https://manuales-urgencia.github.io/> (GitHub Pages, rama `main`). Lo que se
sube a `main` queda publicado en un par de minutos, a la vista de cualquiera que tenga el enlace.

## Qué hay
| Archivo | Qué es |
|---|---|
| `index.html` | Manual TrakCare de Urgencias con todos los perfiles, en un solo archivo (~16 MB) |
| `recorrido-medico.html` | Recorrido guiado del médico de urgencia (~12 MB) |
| `robots.txt` y la meta `robots` de cada página | piden a los buscadores no indexar el sitio; no se sacan |
| `.nojekyll` | GitHub Pages sirve los archivos tal cual |

## Antes de cada commit
1. **Nada que identifique a nadie.** En textos y capturas no van RUN ni RUT (tampoco de pacientes de
   prueba), nombres de personas del equipo de la clínica, correos ni usuarios de TrakCare. Toda
   captura nueva se tapa antes con un rectángulo gris (`#D9D9D9`).
2. **Autor neutro**, para que el historial público no muestre el nombre de nadie:
   `git -c user.name="Manuales de urgencia" -c user.email="noreply@manuales-urgencia.github.io" commit -m "…"`
3. **Un mensaje que diga qué cambió**, una línea por cambio (perfil, tema y qué). El portal también se
   rearma desde fuentes que no están aquí; antes de cada rearme se leen estos mensajes para incorporar
   los cambios y no pisarlos.
4. Abrir la página en un navegador y revisarla en ancho de escritorio y de celular.

## Cómo editar `index.html` sin romperlo
- No leerlo entero: pesa 16 MB, casi todo imágenes en base64. Buscar con `grep -o` y editar con un
  script corto (por ejemplo, en Python) o con reemplazos exactos.
- Por dentro tiene cinco partes, en este orden:
  - un `<script>` corto: el tema claro u oscuro, que se fija antes de pintar;
  - `<style>`: los estilos (las fuentes y el logo van en base64);
  - `<script type="application/json" id="cfg">`: los perfiles y los textos generales;
  - `<script type="application/json" id="data">`: los temas de cada perfil, con las capturas en WebP base64;
  - el último `<script>`: el código de la página.
- Al editar un JSON, comprobar que siga válido (`json.loads`) antes de guardar.
