# Buzón de aportes al Manual TrakCare de Urgencias

**Para el agente (Claude u otro) de quien aporta. Léelo entero antes de convertir o subir nada.**

Tu trabajo: tomar lo que trae tu persona (un Word, notas, capturas, una corrección dictada) y dejarlo
**homologado al formato del manual** en una carpeta de este buzón. No publicas en el manual: Álvaro lo
integra con sus generadores, revisa la privacidad y publica. Si algo de esta guía no calza con lo que
te piden, pregúntale a tu persona antes de inventar una regla nueva.

## 1. Lo primero: este repo es público
Lo que subas a `entrada/` queda visible en internet en minutos, aunque todavía no esté en el manual.
- **Tapa antes de subir** (sección 5). Nada de RUN o RUT (tampoco de pacientes de prueba), nombres de
  personas del equipo, correos ni usuarios de TrakCare, ni en el texto ni en las capturas.
- **Nunca subas el Word, PDF, Excel o PowerPoint original**: traen las capturas sin tapar.
  `entrada/.gitignore` los bloquea; no lo saltes con `git add -f`. Si el aporte es un Word nuevo, ver 3.4.
- Los nombres de pacientes ficticios de la UAT (por ejemplo «Paciente Prueba») pueden quedar.

## 2. Cómo se entrega
1. `git pull` del repo.
2. Copia `entrada/plantilla/` a `entrada/AAAA-MM-DD-<perfil>-<tema-corto>/` (ej. `2026-11-20-enfermeria-curaciones/`).
3. Escribe `aporte.md` siguiendo la plantilla y deja las capturas, ya tapadas, en `capturas/` de esa carpeta.
4. Revisa la lista de la sección 7.
5. Commit con autor neutro y push a `main`:
   `git -c user.name="Manuales de urgencia" -c user.email="noreply@manuales-urgencia.github.io" commit -m "Aporte: <perfil> · <qué>"`
6. Dile a tu persona que avise a Álvaro (correo o Teams) que hay un aporte en el buzón.

**No toques** `index.html`, `recorrido.html`, `CLAUDE.md` ni las carpetas de otros aportes. Cuando
Álvaro integra un aporte, su agente borra la carpeta (queda en el historial de git).

## 3. Tipos de aporte
Se marcan en el encabezado de `aporte.md` (`tipo:`).

### 3.1 `correccion`: cambiar algo que ya está en el manual
Una línea por cambio, con la ubicación exacta tal como se ve en el manual:
`Perfil › Tema › Apartado`, el **texto actual** (copiado) y el **texto nuevo**. Si cambia una captura,
la captura nueva va en `capturas/` y se nombra en la línea.

### 3.2 `tema`: un tema nuevo en un perfil que ya existe
Escrito completo con el formato de la sección 4, indicando después de qué tema va.

### 3.3 `perfil`: un perfil nuevo
El manual completo del perfil con el formato de la sección 4, y su grupo de seguridad en TrakCare.

### 3.4 `word`: una versión nueva de un manual que vive en Word (Enfermería, Matrona, TENS)
Esos tres perfiles se arman directo desde su Word. El Word **no se sube aquí**: tu persona se lo manda
a Álvaro por correo o Teams. En el buzón dejas solo `aporte.md` con la versión, la fecha y la lista de
qué cambió respecto de la versión anterior (temas nuevos, quitados, corregidos), sin capturas.

## 4. Formato del texto
El manual se escribe en Markdown, con esta estructura (mira `plantilla/aporte.md`):

| Nivel | Qué es | Cómo se escribe |
|---|---|---|
| `## Flujo: <nombre>` | el trabajo del perfil, de punta a punta | uno por perfil, casi siempre |
| `### <Tema>` | una tarea que el usuario reconoce | corto, en sustantivo o infinitivo: «Envasar», «Rechazar la receta», «Ingreso y Lista de Farmacia» |
| `#### <Apartado>` | un paso o una pantalla | 2 a 5 palabras: «La ventana de despacho», «Razón de rechazo» |

**Redacción**
- Al usuario se le habla de **usted**, en imperativo: «Haga clic en», «Elija», «Presione», «Complete», «Confirme».
- Cada apartado: 1 a 3 párrafos cortos que dicen **qué hacer y qué pasa después**. Sin relleno, sin «a continuación», sin «como se puede ver».
- Botones, pestañas, campos y menús, en **negrita** y escritos **exactamente** como en pantalla (con sus tildes o la falta de ellas: si TrakCare dice «Diagnosticos», se escribe «Diagnosticos»).
- Si la captura lleva recuadros, el texto los nombra en orden con (1), (2)…: «abra **Retornar desde Hosp/Urg** (1) y elija **Regresar TODO a Stock** (2)».
- Una idea por párrafo; listas solo para opciones que se eligen (motivos, tipos).
- Fechas absolutas («17 nov 2026»), nunca «mañana» o «la próxima semana».

**Capturas**
- Una por apartado, en general; dos solo si la pantalla cambia en el mismo paso.
- Debajo del párrafo que la explica: `![Texto corto](capturas/01-nombre.png)`; el texto entre corchetes es el título que verá el usuario («Pestaña Devolución»).
- PNG de la **pantalla de TrakCare de la UAT**, del navegador en un computador (ancho de 1280 px o más), sin recortar la barra de TrakCare. Nada de fotos de pantalla ni capturas de celular.
- Nombres con número de orden: `01-lista.png`, `02-rechazar.png`…
- **Recuadros rojos:** marcan dónde hacer clic. Dos formas, a elección:
  - sin marcas en la imagen, declarando cada recuadro en píxeles de la imagen original, en el orden de (1), (2): `![Pestaña Devolución](capturas/03-devolucion.png){rect=12,180,140,210; rect=1180,260,1260,290}` (esquina superior izquierda x,y y esquina inferior derecha x,y);
  - o ya pintados en la imagen: rectángulo rojo `#FF0000`, borde de 3 px, sin relleno, con el número en un círculo rojo si son varios.

**Lo que no va nunca**
- «Por verificar», «pendiente», «captura pendiente», «TODO», dobles corchetes `[[ ]]` ni preguntas abiertas. Si algo no está confirmado en la UAT, se deja fuera del aporte y se le dice a tu persona.
- El lugar físico exacto donde imprimir algo (qué impresora, qué mesón).
- Nombres de personas del equipo, ni siquiera como «lo explicó X».
- Contenido clínico que no sea del uso de TrakCare (dosis recomendadas, criterios clínicos).

## 5. Tapar los datos en las capturas
Antes de copiar una captura a `capturas/`, tapa con rectángulos **grises `#D9D9D9`, rellenos y sin borde**:
- el **RUN o RUT** (del paciente y de cualquier usuario), en el banner y en tablas;
- **nombres y apellidos del equipo** (el usuario conectado arriba a la derecha, «registrado por», «médico tratante» si es una persona real, firmas);
- **correos** y **usuarios** de TrakCare.

Con Python y Pillow, por ejemplo:
```python
from PIL import Image, ImageDraw
im = Image.open("original.png").convert("RGB"); d = ImageDraw.Draw(im)
for caja in [(1500, 8, 1890, 36), (210, 52, 330, 74)]:      # x1, y1, x2, y2
    d.rectangle(caja, fill="#D9D9D9")
im.save("capturas/01-lista.png")
```
Después **mira cada captura ampliada al 200 %** y busca a ojo números con formato de RUN, nombres y
arrobas. El original sin tapar se queda en el computador de tu persona, nunca en este repo.

## 6. Decisiones vigentes (no se reabren desde el buzón)
Si tu persona quiere cambiar alguna, que lo hable con Álvaro; no la cambies en un aporte.
- El sitio tiene **dos archivos**: `index.html` (manual) y `recorrido.html` (recorridos de todos los perfiles).
- Interconsultor de Salud Mental y Terapia Ocupacional **no tienen manual** (lo definió la jefatura del proyecto).
- Médico y Médico GO: sin **Revertir Cierre Urg** ni **Solicitud Carro de Paro**.
- Médico GO: sin eclampsia ni preeclampsia, sin antihipertensivo y sin oxitocina en el mortinato; la parte de hospitalización termina en la solicitud de hospitalización.
- Movilizador y Auxiliar de Farmacia: sin aludir al lugar exacto de impresión.
- Ningún perfil publica puntos «por verificar».

## 7. Antes del push
- [ ] La carpeta se llama `AAAA-MM-DD-<perfil>-<tema-corto>` y tiene `aporte.md` (+ `capturas/` si hay).
- [ ] `aporte.md` tiene el encabezado completo y sigue la sección 4.
- [ ] Ninguna palabra prohibida: `grep -niE "verificar|pendiente|todo|\[\[" aporte.md` sin resultados (salvo «pendiente» como nombre de una pestaña de TrakCare).
- [ ] Ningún RUN en el texto: `grep -nE "[0-9]{1,2}\.?[0-9]{3}\.?[0-9]{3}-[0-9kK]" aporte.md` sin resultados.
- [ ] Ningún `@` ni nombre del equipo en el texto.
- [ ] Cada captura revisada al 200 % y tapada.
- [ ] `git status` muestra solo tu carpeta: ni Word, ni PDF, ni `index.html`.

## Perfiles del manual
| Perfil | Clave | Fuente |
|---|---|---|
| Parte I, común a todos (ingreso, inicio, búsqueda, favoritos) | `comun` | Markdown (Álvaro) |
| Médico de Urgencia | `medico` | Markdown (Álvaro) |
| Médico GO | `go` | Markdown (Álvaro) |
| Médico Interconsultor | `ic` | Markdown (Álvaro) |
| Enfermería | `enfermeria` | Word |
| TENS | `tens` | Word |
| Matrona | `matrona` | Word |
| Kinesiología | `kine` | Markdown (Álvaro) |
| Fonoaudiología | `fono` | Markdown (Álvaro) |
| Movilizador | `mov` | Markdown (Álvaro) |
| Químico Farmacéutico | `qf` | Markdown (Álvaro) |
| Auxiliar de Farmacia | `auxf` | Markdown (Álvaro) |
