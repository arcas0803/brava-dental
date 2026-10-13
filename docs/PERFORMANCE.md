# Evaluación de la publicación

**URL:** https://arcas0803.github.io/brava-dental/

**Fecha:** 13 de octubre de 2026. **Versión evaluada:** `b4dba0d`. **Herramientas:** Lighthouse 13.5.0, Chrome 155, perfil temporal local contra la publicación HTTPS. Se ejecutaron tres mediciones por perfil con las configuraciones de móvil y escritorio de Lighthouse y throttling simulado.

## Resultados finales

| Métrica | Móvil: mediana (rango) | Escritorio: mediana (rango) |
|---|---|---|
| Rendimiento | 100 (100–100) | 100 (100–100) |
| Buenas prácticas | 100 (100–100) | 100 (100–100) |
| Accesibilidad automatizada | 100 (100–100) | 100 (100–100) |
| LCP | 1,506 s (1,506–1,656) | 0,326 s (0,325–0,326) |
| CLS | 0 | 0 |
| TBT | 0 ms | 0 ms |
| SEO | 63 | 63 |

[Resultados estructurados](performance-results.json). Alcance de las mediciones: landing principal. La ruta del caso de estudio se comprobó funcional y visualmente, sin atribuirle estas puntuaciones.

## Qué se detectó y qué se cambió

La primera medición pública dio 99 de rendimiento móvil y un LCP mediano de 1,972 s. Lighthouse detectó imágenes mayores que su tamaño de presentación. Se sustituyeron por variantes WebP generadas durante el build, con srcset y sizes. La fotografía conserva su proporción completa, y la imagen principal se solicita con carga eager y prioridad alta. La imagen del espacio y la captura del caso de estudio se cargan de forma diferida.

La transferencia móvil mediana observada en resource-summary pasó de aproximadamente 286 KiB a 142 KiB, incluyendo las imágenes observadas por Lighthouse. Es transferencia de red, con cabeceras y condiciones de caché; no el tamaño del repositorio ni una garantía de coste para toda sesión. La comparación es indicativa: el estado de la caché/CDN y la variación de red influyen.

## Buenas prácticas

La auditoría no detectó fallos binarios de buenas prácticas ni de accesibilidad. La publicación usa HTTPS, recursos del mismo origen, fuentes locales, imágenes dimensionadas y una salida HTML estática. El JavaScript de los controles se incluye en el documento; cero solicitudes de scripts externos no significa ausencia de JavaScript.

Se verificaron las rutas bajo /brava-dental, la carga de recursos y el acceso al caso de estudio. Las posiciones de nombre, teléfono y selección de tratamiento permanecen iguales antes y después de mostrar errores, tanto en móvil como en escritorio. Se mantienen errores conectados a sus campos y estados anunciados.

Las acciones de despliegue se actualizan a sus versiones oficiales vigentes y el workflow comprueba TypeScript antes de publicar. Agentes, instrucciones locales, skills, dependencias instaladas y archivos de trabajo están excluidos del repositorio.

## Interpretación y oportunidades

- **SEO 63 es deliberado:** noindex evita presentar una clínica ficticia en buscadores. No se elimina para mejorar la puntuación.
- **No hay datos de campo:** LCP y CLS aquí son de laboratorio. INP requiere tráfico real; TBT no lo sustituye.
- **100 no certifica WCAG:** quedan pendientes pruebas exhaustivas con lector de pantalla, alto contraste, zoom nativo y personas usuarias.
- **Dependencias críticas:** Lighthouse señala la cadena de fuentes/estilos como oportunidad de optimización. Sus costes medidos cumplen los objetivos, por lo que no se añaden preloads ni herramientas innecesarias.
- **Captación no demostrada:** el formulario es una demo y no hay leads reales, asistencia ni cohortes de retorno.
- **Repetición futura:** volver a medir tras cambios en fotos, fuentes, contenido o alojamiento; no esperar puntuaciones idénticas en todo equipo y red.

## Reproducir

Tras instalar las dependencias, ejecutar la CLI de Lighthouse contra la URL pública y repetir tres veces por configuración:

```sh
npx lighthouse https://arcas0803.github.io/brava-dental/ --only-categories=performance,accessibility,best-practices,seo --output=json --output-path=mobile.json --chrome-flags="--headless"
npx lighthouse https://arcas0803.github.io/brava-dental/ --preset=desktop --only-categories=performance,accessibility,best-practices,seo --output=json --output-path=desktop.json --chrome-flags="--headless"
```

Guardar cada ejecución con nombre distinto y comparar mediana/rango, versión de las herramientas y condiciones.
