---
tipo: tema            # correccion | tema | perfil | word (ver LEEME.md § 3)
perfil: auxf          # clave del perfil (tabla al final de LEEME.md)
fecha: 2026-11-20
aporta: Enfermería    # el área, no el nombre de la persona
ubicacion: después del tema «Despachar»   # dónde va (tema) o «todo el perfil» (perfil); en correccion, va en cada línea
probado_en_uat: 2026-11-19
---

<!-- Borra los ejemplos que no uses. En tipo «correccion» o «word» basta la sección «Cambios». -->

## Cambios

<!-- Solo en tipo correccion. Una línea por cambio. -->
- Auxiliar de Farmacia › Despachar › La pestaña Despachado
  - Texto actual: «La receta pasa a la pestaña **Despachado**.»
  - Texto nuevo: «La receta pasa a la pestaña **Despachado**, donde queda hasta que se administra.»
  - Captura: sin cambio

## Flujo: Despacho de medicamentos

### Procesar devoluciones

#### La pestaña Devolución

En la **Lista de Farmacia**, la receta aparece en la pestaña **Devolución** (1), con **Estado de Farmacia** «Devolución». Para procesarla, haga clic en **Consultar** (2).

![Pestaña Devolución](capturas/01-devolucion.png){rect=12,180,140,210; rect=1180,260,1260,290}

#### Regresar a stock

Se abre la pantalla con los medicamentos a devolver ya seleccionados. En el menú superior, abra **Retornar desde Hosp/Urg** (1) y elija **Regresar TODO a Stock** (2).

![Regresar TODO a Stock](capturas/02-regresar.png)
