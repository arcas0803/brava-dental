# BRAVA: diseño y desarrollo de una landing dental

## Contexto y objetivo

Proyecto de portfolio para una clínica ficticia en Madrid. El objetivo era dar personalidad a una landing de servicios y facilitar un recorrido desde la primera impresión hasta una solicitud de cita de demostración.

El alcance incluye diseño visual, desarrollo frontend, interacción, responsive, preparación del despliegue y evaluación de calidad. No incluye una clínica operativa, integración con CRM, campañas ni gestión de datos personales.

## Del concepto a la composición

La dirección elegida usa una base oscura y verde lima, inspirada en el fondo de la fotografía. Los titulares amplios dan carácter a la página; las superficies claras ofrecen descanso y facilitan la lectura.

Durante las iteraciones, un recorte horizontal del retrato resultó demasiado agresivo. Se corrigió conservando toda su proporción, y después se reforzó el diseño mediante composición, contraste y ritmo entre secciones. La fotografía y las leyendas tienen espacios independientes.

Los tratamientos se organizan en una retícula de dos columnas de distinta anchura. La primera visita se explica en tres pasos y las dudas se resuelven mediante controles HTML nativos. La misma llamada a la acción acompaña el recorrido.

## Desarrollo e interacción

Astro genera HTML estático. TypeScript se emplea en los comportamientos del menú y del formulario; CSS resuelve el diseño y los estados visuales. No se añade un framework de interfaz para controles sencillos.

El menú expone su estado y se cierra con Escape. La selección de tratamiento llega al formulario. La validación conserva los datos introducidos y dirige el foco al primer campo incorrecto. La confirmación explica que se ha completado una demo, no una reserva real.

## Un detalle de producto: errores sin saltos

Los mensajes de validación tenían altura variable y alteraban la disposición de los campos. Se incorporaron espacios reservados bajo los controles y mensajes breves. El estado inválido cambia el borde, sin cambiar sus dimensiones; el foco combina contraste y un halo suave.

El problema se verificó comparando la posición de campos y controles antes y después de la validación en escritorio y móvil.

## Responsive y accesibilidad

Se revisaron anchos de 320, 375, 768, 1440 y 1920 píxeles. La página incluye etiquetas explícitas, conexión de errores con los campos, estados anunciados, enlaces semánticos, un acceso directo al contenido y estilos para movimiento reducido.

Las comprobaciones automatizadas complementan la revisión manual. Quedan fuera de una certificación completa: pruebas exhaustivas con lector de pantalla, alto contraste y usuarios reales.

## Publicación y evaluación

GitHub Actions compila y publica el sitio en GitHub Pages. La configuración respeta el subdirectorio del repositorio y separa los archivos fuente de los resultados generados.

El [informe de rendimiento](PERFORMANCE.md) documenta mediciones sobre la publicación. Las puntuaciones técnicas no prueban mejoras de captación: estas requerirían tráfico, solicitudes reales y periodos comparables.

## Próximos pasos para un producto real

Verificar identidad, servicios y datos del negocio; integrar un backend con confirmación real; definir privacidad y consentimiento; probar con usuarios; y medir solicitudes cualificadas y asistencia a citas. El prototipo mantiene estas necesidades visibles sin simular resultados.
