# ToAgenda Ecuador — UI/UX Design Brief

**Versión:** 1.0  
**Objetivo:** Definir una experiencia coherente para ToAgenda, ToAgenda Pro y el panel administrativo.

## 1. Principios

1. **Encontrar y reservar primero:** búsqueda y próxima disponibilidad dominan la experiencia del consumidor.
2. **Claridad de estado:** “solicitud enviada” nunca se confunde con “cita confirmada”.
3. **Neutral y multiservicio:** la interfaz no debe sentirse exclusiva de belleza, salud o un género.
4. **Progresivo:** mostrar decisiones necesarias para el paso actual y ocultar configuración avanzada hasta requerirla.
5. **Accesible:** ubicación, mapa, color o gestos nunca serán el único medio para completar una tarea.
6. **Confianza local:** precios, ubicación, políticas, verificación y reseñas deben estar visibles antes de reservar.

## 2. Identidad

### Personalidad

Cercana, confiable, moderna, eficiente e inclusiva. El lenguaje será directo, amable y sin tecnicismos.

### Paleta inicial

| Token | Valor | Uso |
|---|---|---|
| `primary` | `#5B4FDB` | acciones principales, selección y marca |
| `primary-dark` | `#4035B5` | interacción y contraste |
| `accent` | `#14B8A6` | disponibilidad, éxito y detalles de marca |
| `background` | `#F7F8FC` | fondos generales |
| `surface` | `#FFFFFF` | tarjetas, hojas y formularios |
| `ink` | `#111827` | texto principal |
| `muted` | `#667085` | texto secundario |
| `border` | `#DDE1EA` | divisores y campos |
| `danger` | `#C9364F` | error y cancelaciones |
| `warning` | `#B56A00` | pendiente y atención |

Los colores semánticos tendrán variantes de fondo y texto que cumplan contraste WCAG AA. Ningún estado dependerá únicamente del color: se acompañará con icono y etiqueta.

### Tipografía e iconografía

- Fuente sans serif variable con soporte latino; Inter será la base mientras no exista tipografía de marca.
- Escala mínima: 12, 14, 16, 20, 24, 32 y 40 px con line-height accesible.
- Iconos de trazo simple y metáforas universales.
- Fotografías auténticas aportadas por negocios; evitar que las imágenes de muestra sesguen el producto hacia una sola categoría.

## 3. Sistema de diseño

- Cuadrícula base de 4 px; espaciado principal 8/12/16/24/32.
- Radio de 12 px en controles y 16 px en tarjetas.
- Áreas táctiles mínimas de 44 × 44 pt en iOS y 48 × 48 dp en Android.
- Botón primario único por zona de decisión.
- Componentes con estados default, pressed, focused, disabled, loading, error y success.
- Formularios preservan información después de errores recuperables.
- Skeletons para carga inicial; indicadores discretos para acciones cortas.
- Hojas inferiores para filtros y decisiones móviles; diálogos solo para confirmaciones destructivas.

### Componentes obligatorios

- App bar y navegación inferior.
- Buscador con sugerencias.
- Chips de categoría y filtros.
- Tarjeta de negocio y carrusel de portafolio.
- Marcador y tarjeta vinculada del mapa.
- Servicio, precio fijo/desde y duración.
- Selector de sucursal, profesional y modalidad.
- Calendario y grilla de slots.
- Contador de retención.
- Stepper de reserva.
- Estado de cita y timeline.
- Tarjeta de método de pago y carga de comprobante.
- Reseña, distribución y distintivo verificado.
- Agenda Pro, cita y bloqueo.
- Formularios parametrizables.
- Tablas, filtros y paneles administrativos.

## 4. Arquitectura de información

### ToAgenda

| Sección | Contenido principal |
|---|---|
| Inicio | ubicación, búsqueda, categorías, disponible hoy, cercanos y repetir cita |
| Explorar | consulta, filtros, lista y mapa |
| Citas | pendientes, próximas e historial |
| Favoritos | negocios guardados |
| Perfil | cuenta, ubicaciones, notificaciones, privacidad y ayuda |

### ToAgenda Pro

| Sección | Contenido principal |
|---|---|
| Hoy | próximas citas, pendientes, espacios y resumen |
| Agenda | vistas, filtros, creación y bloqueos |
| Clientes | búsqueda, historial y notas operativas |
| Equipo | miembros, servicios, horarios y ausencias |
| Más | perfil, locales, catálogo, pagos, reportes, plan y soporte |

### Panel administrativo

Navegación lateral: Resumen, Moderación, Negocios, Categorías, Reseñas, Denuncias, Planes, Auditoría y Configuración.

## 5. Pantallas mínimas — consumidor

1. Splash y actualización requerida.
2. Teléfono, OTP, términos y permisos.
3. Ubicación detectada y selección manual.
4. Inicio con contenido, vacío y error.
5. Búsqueda y sugerencias.
6. Resultados lista/mapa y filtros.
7. Ficha de negocio.
8. Detalle de servicio.
9. Modalidad/local/profesional.
10. Fecha y hora.
11. Datos parametrizados.
12. Método de pago y comprobante.
13. Revisión y retención.
14. Resultado confirmado o pendiente.
15. Detalle y gestión de cita.
16. Reprogramación/cancelación.
17. Favoritos.
18. Reseña.
19. Perfil, notificaciones y privacidad.

## 6. Pantallas mínimas — Pro

1. Acceso y selección/creación de organización.
2. Onboarding por pasos con progreso guardado.
3. Estado de moderación y correcciones.
4. Hoy.
5. Agenda día/semana/mes.
6. Detalle y cambio de estado de cita.
7. Crear cita manual.
8. Bloquear tiempo.
9. Lista y ficha de clientes.
10. Equipo, permisos, servicios y horarios.
11. Negocio, sucursales y zonas a domicilio.
12. Catálogo y editor de servicio/campos.
13. Métodos de pago.
14. Documentos de verificación.
15. Reportes básicos.

## 7. Contenido y tono

- Español de Ecuador, tratamiento de “tú”.
- Moneda: `$12,50` o `$12.50` según validación de investigación; el sistema almacena centavos, no flotantes.
- Fecha visible: `12 ago 2026`; hora configurable por dispositivo, con zona del local explícita si difiere.
- Usar “cita” como término principal y “reserva” como acción comercial cuando resulte natural.
- Mensajes accionables: “Este horario acaba de ocuparse. Elige una de estas opciones”.
- No culpar al usuario ni mostrar errores internos.
- Distinguir “Cancelar cita” de “Volver” y exigir confirmación para acciones irreversibles.

## 8. Ubicación, privacidad y confianza

- Explicar ubicación antes del permiso del sistema.
- Permitir ubicación manual permanente.
- Para negocios desde casa, mostrar zona aproximada si el propietario oculta la dirección; revelar instrucciones solo en una reserva confirmada.
- Documentos sanitarios nunca se muestran completos.
- Un distintivo abre una explicación sobre qué verificó ToAgenda y su vigencia.
- Formularios de servicio no deben solicitar información clínica en el MVP.

## 9. Estados y resiliencia

Cada recorrido debe diseñarse en:

- Carga inicial y actualización.
- Contenido vacío con siguiente acción.
- Sin resultados con relajación de filtros.
- Sin conexión con contenido cacheado identificado.
- Sesión expirada con recuperación.
- Permiso denegado.
- Archivo rechazado o carga interrumpida.
- Negocio en revisión, con cambios solicitados, rechazado o suspendido.
- Hold próximo a vencer y vencido.
- Conflicto de disponibilidad.

## 10. Accesibilidad y validación

- WCAG 2.1 AA en contraste, foco y lectura.
- Lectores de pantalla con etiquetas semánticas y orden lógico.
- Escalado de fuente sin truncar acciones críticas.
- Soporte de reducción de movimiento.
- Teclado completo en panel administrativo.
- Pruebas de usabilidad con al menos cinco consumidores y cinco negocios antes de cerrar hi-fi.
- Tareas de prueba: encontrar un servicio, reservar, entender estado pendiente, configurar un negocio y aprobar una cita.

## 11. Entregable Figma

- FigJam maestro: [ToAgenda Ecuador — Flujo maestro MVP](https://www.figma.com/board/JLt7Snimw2ebPS3XjCyz60).
- Variables/tokens, componentes y variantes.
- Wireframes antes de alta fidelidad.
- Prototipo clicable de los cinco recorridos definidos en `03-app-flows.md`.
- Anotaciones de validación, permisos, estados y contenido.
- Changelog y versión enlazada desde este documento y desde `03-app-flows.md`.
