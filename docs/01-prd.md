# ToAgenda Ecuador — Product Requirements Document (PRD)

**Versión:** 1.0  
**Estado:** Base para validación  
**Mercado:** Ecuador  
**Productos:** ToAgenda, ToAgenda Pro y Panel Administrativo

## 1. Resumen

ToAgenda es un marketplace móvil ecuatoriano que permite descubrir negocios de servicios, consultar su disponibilidad y reservar citas en tiempo real. ToAgenda Pro permite a profesionales, emprendimientos y equipos publicar su oferta y administrar agenda, clientes, personal, locales, recursos y métodos de pago.

Los perfiles de negocios y las reservas existen exclusivamente dentro de la app para consumidores. No se crearán páginas públicas de reserva ni se permitirán reservas desde navegador. Los enlaces compartidos serán enlaces profundos que abrirán la ficha interna o dirigirán a la tienda de aplicaciones.

## 2. Visión, problema y propuesta de valor

### Visión

Convertir a ToAgenda en el punto de encuentro ecuatoriano para cualquier servicio que se presta mediante cita, empezando por Manabí y Guayaquil y expandiéndose a Quito y al resto del país.

### Problemas

- Los consumidores coordinan disponibilidad mediante llamadas o conversaciones repetitivas.
- Los negocios pierden tiempo gestionando mensajes, sufren cruces de horarios e inasistencias y tienen poca visibilidad de su operación.
- Los emprendimientos pequeños carecen de un canal local para ser descubiertos por ubicación y disponibilidad.
- Las plataformas genéricas no siempre representan recursos, varias sucursales, servicios parametrizables o aprobación manual.

### Propuesta de valor

- **Consumidor:** encontrar quién ofrece el servicio, dónde, a qué precio y cuándo puede atenderlo.
- **Negocio:** publicar una oferta profesional y administrar citas sin construir tecnología propia.
- **ToAgenda:** generar una red local donde una mejor densidad de oferta aumenta la utilidad para consumidores y negocios.

## 3. Objetivos y métricas

### Objetivos del MVP

1. Permitir que un negocio aprobado configure y opere su agenda.
2. Permitir que un consumidor encuentre y reserve un servicio usando ubicación o búsqueda manual.
3. Evitar reservas solapadas para profesionales y recursos.
4. Mantener sincronizadas ambas aplicaciones.
5. Validar adopción con negocios reales en Manabí y Guayaquil.

### Indicadores

| Indicador | Definición | Meta del piloto |
|---|---|---:|
| Activación de negocios | Negocios aprobados que publican al menos un servicio, ubicación y horario | >= 75% |
| Actividad semanal | Negocios activados que usan la agenda semanalmente | >= 60% |
| Tiempo a primera reserva | Tiempo entre aprobación y primera cita | Mediana <= 14 días |
| Conversión | Fichas vistas que terminan en reserva creada | Medir línea base |
| Citas completadas | Reservas marcadas como `completed` | Tendencia semanal creciente |
| Inasistencia | `no_show` / citas confirmadas vencidas | Medir línea base |
| Recurrencia | Consumidores con una segunda cita dentro de 60 días | Medir línea base |
| Conflictos | Reservas confirmadas que se solapan | 0 |

Las descargas no serán la métrica principal.

## 4. Alcance

### Incluido

- Cobertura técnica para Ecuador con captación progresiva por zona.
- Cualquier emprendimiento que venda servicios mediante citas.
- Profesionales independientes, negocios desde casa, atención a domicilio, locales, equipos, cadenas pequeñas y consultorios.
- Categorías administradas por ToAgenda y servicios creados por cada negocio.
- Búsqueda por texto, categoría, distancia, ubicación, precio y disponibilidad.
- Vista de lista y mapa.
- Ficha interna del negocio con banner, portafolio, servicios, equipo, locales, pagos y reseñas.
- Reservas automáticas o sujetas a aprobación por servicio.
- Agenda, horarios, excepciones, descansos y recursos físicos.
- Métodos de pago declarados y comprobantes opcionales.
- Moderación previa, verificación sanitaria, favoritos, reseñas y notificaciones.
- Piloto gratuito con capacidades de planes preparadas pero no activadas.

### Fuera del MVP

- Venta de productos sin cita, hoteles, restaurantes, alquileres o reservas de mesas.
- Páginas públicas de negocios o reservas web.
- Procesamiento, custodia o reparto de dinero por ToAgenda.
- Historia clínica, diagnóstico, prescripción o resultados médicos.
- Chat en tiempo real.
- Facturación electrónica, inventario y nómina.
- Publicidad pagada, promociones patrocinadas y programas de fidelización.
- Integraciones de calendarios externos y agentes de IA.

## 5. Usuarios y roles

### Consumidor

Busca, reserva, administra citas, guarda favoritos y califica servicios completados.

### Propietario

Control total sobre organización, sucursales, equipo, catálogo, agenda, clientes, pagos declarados y reportes.

### Administrador de negocio

Administra operación y configuración, excepto propiedad, cierre de cuenta y configuración sensible de suscripción.

### Recepcionista

Gestiona agenda, clientes, llegada, cobros declarados y solicitudes; no accede a configuración sensible ni reportes financieros completos.

### Profesional

Consulta y administra su propia agenda, disponibilidad y estado de citas, de acuerdo con permisos concedidos.

### Administrador de ToAgenda

Gestiona categorías, moderación, verificaciones, denuncias, suspensiones, soporte, planes y auditoría.

## 6. Requisitos funcionales — ToAgenda

### Registro y ubicación

- Registro o acceso con teléfono y OTP; correo opcional y verificable.
- Solicitud de ubicación contextual, explicando su beneficio.
- Si el permiso es rechazado, selección manual de provincia, cantón y sector.
- Cambio de ubicación desde Inicio o Explorar.
- Consentimientos de privacidad y marketing separados.

### Descubrimiento

- Buscar categorías, subcategorías, servicios y nombres de negocios.
- Mostrar únicamente negocios `approved`, activos y con una ubicación publicada.
- Ordenar por relevancia, distancia, disponibilidad próxima y valoración.
- Filtrar por categoría, rango de precio, distancia, fecha, disponible hoy, atención a domicilio, modalidad, valoración, verificación y métodos de pago.
- Alternar entre mapa y lista conservando consulta y filtros.
- No exponer direcciones privadas de atención a domicilio ni negocios desde casa que elijan ocultarlas; mostrar zona aproximada hasta que exista una reserva confirmada.

### Ficha interna del negocio

- Banner, logo, nombre, descripción, categorías, distintivos y portafolio.
- Sucursales o zonas de cobertura, teléfono/WhatsApp según configuración y cómo llegar.
- Servicios con precio, modalidad, duración, preparación, políticas y próxima disponibilidad.
- Equipo elegible y opción “cualquier profesional disponible”.
- Métodos de pago aceptados y política de cancelación.
- Promedio y distribución de reseñas verificadas.
- Compartir mediante Universal Link/App Link sin habilitar reserva web.

### Reserva

1. Seleccionar servicio.
2. Seleccionar modalidad y ubicación.
3. Elegir profesional o cualquiera disponible.
4. Consultar fecha y hora.
5. Completar preguntas configuradas por el servicio.
6. Elegir método de pago declarado y adjuntar comprobante si aplica.
7. Aceptar política de cancelación.
8. Confirmar.

- Un horario se retiene durante cinco minutos al comenzar la confirmación.
- En modo automático, una reserva válida pasa a `confirmed`.
- En modo manual, pasa a `pending`; el espacio se considera ocupado hasta aprobación, rechazo o expiración.
- La pantalla final explica claramente el estado y no presenta una solicitud pendiente como confirmada.

### Gestión de citas

- Listar próximas, pendientes, completadas y canceladas.
- Ver negocio, servicio, profesional, local, fecha, pagos declarados y políticas.
- Reprogramar o cancelar dentro de las reglas del servicio.
- Abrir navegación hacia el local.
- Añadir al calendario del dispositivo.
- Calificar una única vez después de `completed`.

## 7. Requisitos funcionales — ToAgenda Pro

### Incorporación y publicación

- Elegir modalidad: independiente, desde casa, a domicilio, local, equipo, varias sucursales o consultorio.
- Crear organización, identidad visual, contacto, descripción y categorías.
- Crear al menos una ubicación o zona de cobertura.
- Configurar servicios, profesionales, horarios y pagos aceptados.
- Cargar documentos requeridos por categoría.
- Enviar a revisión y ver estado: borrador, enviado, cambios solicitados, aprobado, suspendido o rechazado.
- Ningún negocio será visible antes de aprobación.

### Catálogo parametrizable

Cada servicio incluye nombre, categoría, descripción, imágenes, precio fijo o “desde”, duración, buffers, modalidad, sucursales, profesionales, recursos, confirmación, anticipo externo, cancelación y preguntas personalizadas.

Los tipos de campo permitidos son texto corto/largo, número, fecha, selección única/múltiple, sí/no, archivo y aceptación. No se permitirán campos clínicos en el MVP.

### Agenda y operación

- Vistas diaria, semanal, mensual, por profesional, sucursal y recurso.
- Crear citas manuales respetando conflictos.
- Aprobar, rechazar, reprogramar y cancelar.
- Registrar llegada, inicio, finalización e inasistencia.
- Bloquear tiempo y configurar vacaciones, descansos y excepciones.
- Sincronización en tiempo real cuando las apps estén abiertas.

### Clientes y reportes

- Ficha operacional con contacto, historial de citas, cancelaciones, inasistencias y notas internas no clínicas.
- Reportes de reservas, ventas declaradas, ocupación, cancelaciones, recurrencia, servicios, profesionales, métodos de pago y origen.
- Exportaciones y reportes avanzados quedan fuera del primer piloto salvo necesidad operativa.

## 8. Moderación, salud y confianza

- Todo negocio requiere revisión de identidad, perfil, ubicación y contenido.
- Categorías sanitarias requieren documentos y permisos vigentes antes de publicación.
- Los documentos de verificación son privados y solo accesibles para personal autorizado.
- La app mostrará el tipo y vigencia de verificación, sin publicar documentos completos.
- Reseñas permitidas solo a consumidores asociados a una cita completada.
- Administradores pueden ocultar reseñas, solicitar cambios, suspender negocios y registrar el motivo.
- El diseño seguirá la Ley Orgánica de Protección de Datos Personales de Ecuador y el principio de minimización.

## 9. Reglas de negocio

- Los horarios se almacenan en UTC y se muestran con la zona horaria de la ubicación.
- El precio mostrado conserva moneda USD y si es fijo o “desde”.
- Solo servicios y miembros activos participan en disponibilidad.
- Una reserva confirmada o pendiente ocupa profesional y recursos.
- Rechazo, cancelación o expiración libera el espacio de inmediato.
- Reprogramar crea trazabilidad del horario anterior y valida nuevamente disponibilidad.
- Solo el propietario puede eliminar una organización; la eliminación será lógica y sujeta a retención legal.
- Los consumidores nunca pueden ver notas internas, documentos o información de otros clientes.

## 10. Criterios de aceptación del producto

- Un consumidor completa una reserva sin llamadas externas.
- El flujo sigue funcionando sin permiso de geolocalización.
- No aparecen negocios no aprobados.
- Un consultorio no aparece sin verificación vigente.
- No existen dobles reservas confirmadas o pendientes.
- Cambios relevantes aparecen en ambas apps y generan notificación idempotente.
- Una organización no accede a datos de otra.
- No existe URL web capaz de completar una reserva.

