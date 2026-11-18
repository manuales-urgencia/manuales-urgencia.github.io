# Manuales de urgencia — cómo trabajar en este repo

Este repo es el sitio <https://manuales-urgencia.github.io/> (GitHub Pages, rama `main`). **Es público:**
lo que se sube a `main` queda a la vista de cualquiera en un par de minutos, incluida la carpeta `entrada/`.

## Primero: ¿de quién es esta sesión?
| Si trabajas para... | Haces | No haces |
|---|---|---|
| **Cualquier persona que aporte** (la Vale, Manuel u otra del equipo) | Dejas el aporte en `entrada/`, en el formato de la casa: **lee `entrada/LEEME.md` antes de tocar nada** | No editas `index.html` ni `recorrido.html`. Los arma Álvaro desde fuentes que no están aquí; un cambio directo se pierde en el próximo rearme |
| **Álvaro** (su agente, desde el repo privado `clinica-uandes`) | Integras lo que haya en `entrada/` (procedimiento en `proyectos/clinica-uandes/manuales.md` del repo privado, § «Buzón entrada/»), publicas y borras el aporte integrado | No publicas un aporte sin que Álvaro lo pida |

Desde el 17 nov 2026 los cambios al manual entran solo por el buzón: así quedan homologados y no se pisan.

## Qué hay
| Archivo | Qué es |
|---|---|
| `index.html` | Manual TrakCare de Urgencias con todos los perfiles, en un solo archivo (~31 MB) |
| `recorrido.html` | Recorridos guiados de todos los perfiles en un solo archivo (~47 MB): la portada pide elegir el perfil. Lo arma `unir_recorridos.py` (repo privado). `#medico`, `#go`, `#ic`, `#matrona`, `#tens`, `#kine`, `#fono`, `#mov`, `#qf` o `#auxf` abren uno directo |
| `entrada/` | El buzón de aportes: `LEEME.md` (reglas y formato), `plantilla/` y una carpeta por aporte pendiente |
| `robots.txt` y la meta `robots` de cada página | piden a los buscadores no indexar el sitio; no se sacan |
| `.nojekyll` | GitHub Pages sirve los archivos tal cual |

## Sin ramas: todo va a `main`, commiteado y subido
- Se trabaja directo en `main`. Al empezar, siempre `git pull`.
- Cada cambio terminado se commitea y se sube (`git push`) en el momento. Al cerrar la sesión no
  queda nada sin commit ni sin subir: `git status` limpio y `git log origin/main..` vacío.
- Si el push falla porque alguien subió antes: `git pull --rebase` y volver a subir. Nunca `push --force`.
- Si la sesión solo deja subir a una rama (por ejemplo, `claude/…`), se abre el pull request, se
  fusiona a `main` en el momento y se borra la rama. No quedan ramas abiertas.

## Antes de cada commit
1. **Nada que identifique a nadie.** En textos y capturas no van RUN ni RUT (tampoco de pacientes de
   prueba), nombres de personas del equipo de la clínica, correos ni usuarios de TrakCare. Toda
   captura se tapa antes con un rectángulo gris (`#D9D9D9`). Nunca se sube un Word, PDF, Excel o
   PowerPoint (traen las capturas sin tapar): `entrada/.gitignore` los bloquea.
2. **Autor neutro**, para que el historial público no muestre el nombre de nadie:
   `git -c user.name="Manuales de urgencia" -c user.email="noreply@manuales-urgencia.github.io" commit -m "…"`
3. **Un mensaje que diga qué cambió**, una línea por cambio (perfil, tema y qué).

## Solo para el agente de Álvaro: cómo editar `index.html` sin romperlo
- No leerlo entero: pesa ~31 MB, casi todo imágenes en base64. Buscar con `grep -o` y editar con un
  script corto o, mejor, con `publicar/empalmar_perfil.py` del repo privado.
- Por dentro tiene cinco partes, en este orden: un `<script>` corto (tema claro u oscuro); `<style>`;
  `<script type="application/json" id="cfg">` (perfiles y textos generales); `<script type="application/json" id="data">`
  (temas de cada perfil, capturas en WebP base64); el último `<script>`, el código de la página.
- Al editar un JSON, comprobar que siga válido (`json.loads`) antes de guardar.
- Si hay conflicto en `index.html` (casi una sola línea gigante), no se resuelve a mano: se toma la
  versión de `main` y se vuelve a aplicar el cambio con el mismo script.
