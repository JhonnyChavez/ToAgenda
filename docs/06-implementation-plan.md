# ToAgenda Ecuador — Plan de implementación

**Versión:** 1.0  
**Capacidad:** equipo lean de dos desarrolladores, diseño parcial, QA parcial y fundador como Product Owner  
**Duración objetivo:** 24 semanas después de aprobar documentación y prototipo

## 1. Condiciones de inicio

- PRD, TRD, flujos, brief y esquema revisados por fundador y equipo técnico.
- Prototipo Figma probado con usuarios.
- Responsable legal contratado para privacidad, términos y salud.
- Backlog priorizado con criterios de aceptación.
- Cuentas de desarrollo y servicios externos disponibles.

## 2. Equipo y responsabilidades

| Rol | Dedicación | Responsabilidad |
|---|---:|---|
| Fundador / Product Owner | parcial continua | decisiones, entrevistas, captación y aceptación |
| Desarrollador A | completa | Flutter consumidor/Pro y contratos móviles |
| Desarrollador B | completa | NestJS, PostgreSQL, admin e infraestructura |
| Diseñador UI/UX | semanas 1–6 y soporte | investigación, Figma, sistema visual y usabilidad |
| QA | parcial desde semana 15 | estrategia, regresión, dispositivos y tiendas |
| Asesor legal Ecuador | hitos | privacidad, términos, marketplace y salud |

Ambos desarrolladores revisarán código cruzado; ninguna persona será la única capaz de desplegar o restaurar datos.

## 3. Fases

### Semanas 1–3 — Descubrimiento y diseño

- Cerrar los seis documentos y registrar decisiones.
- Entrevistar al menos 10 consumidores y 10 negocios de Manabí/Guayaquil.
- Validar vocabulario, pagos, privacidad de domicilios, confirmación y cancelaciones.
- Crear FigJam, wireframes, sistema visual y primer prototipo.
- Probar los cinco recorridos críticos y corregir problemas de comprensión.

**Salida:** documentos aprobados, Figma enlazado y backlog listo.

### Semanas 4–6 — Fundaciones

- Crear monorepo, CI, convenciones, entornos y Docker local.
- Implementar identidad, OTP/correo, sesiones, consentimientos y perfiles.
- Crear organizaciones, membresías, roles, archivos y auditoría base.
- Integrar Google Maps en sandbox y modelos geográficos.
- Crear shell de ambas apps y panel administrativo.

**Salida:** acceso seguro y organización aislada funcionando en staging.

### Semanas 7–10 — Oferta y moderación

- Implementar onboarding Pro, identidad, ubicaciones y zonas.
- Crear categorías administradas, catálogo, campos parametrizables, equipo, recursos y horarios.
- Implementar carga privada de verificaciones.
- Crear cola administrativa y decisiones de moderación.
- Publicar solo organizaciones aprobadas.

**Salida:** un negocio puede configurarse, ser aprobado y aparecer mediante API.

### Semanas 11–14 — Disponibilidad y reservas

- Implementar reglas, excepciones, bloqueos, vacaciones y buffers.
- Crear disponibilidad, holds y restricciones de exclusión.
- Implementar reservas automáticas/manuales y toda transición autorizada.
- Añadir agenda Pro y actualizaciones WebSocket.
- Ejecutar pruebas de concurrencia y recuperación.

**Salida:** motor de reservas sin cruces bajo carga del piloto.

### Semanas 15–18 — Marketplace del consumidor

- Implementar ubicación opcional y selección manual.
- Crear Inicio, búsqueda, filtros, lista, mapa y ficha interna.
- Completar flujo de reserva, citas, reprogramación, cancelación y favoritos.
- Configurar enlaces profundos sin página de reservas.
- Iniciar QA sistemático en Android/iOS reales.

**Salida:** recorrido completo consumidor-negocio en staging.

### Semanas 19–21 — Operación y confianza

- Push, SMS/correo adaptables, recordatorios e idempotencia.
- Métodos de pago declarados y comprobantes.
- Reseñas verificadas, reportes básicos, denuncias y suspensiones.
- Planes/entitlements en modo piloto sin cobro.
- Observabilidad, dashboards, alertas y runbooks.

**Salida:** producto operable y soportable.

### Semanas 22–24 — Preparación y piloto

- Auditoría de seguridad, privacidad y accesibilidad.
- Pruebas de carga, backups, restauración y fallos de proveedores.
- Importar/configurar 25–40 negocios piloto.
- Preparar fichas de App Store/Google Play, privacidad y revisión.
- Lanzamiento controlado, soporte cercano y seguimiento de métricas.

**Salida:** piloto activo en Manabí y Guayaquil.

## 4. Dependencias externas

- Apple Developer Program y Google Play Console.
- Proyecto Firebase para push y distribución interna.
- Google Maps Platform con cuotas y alertas.
- Proveedor OTP con cobertura ecuatoriana y entorno de prueba.
- Proveedor de correo transaccional.
- PostgreSQL/PostGIS y Redis administrados para staging/producción.
- Almacenamiento S3/CDN.
- Monitoreo de errores, logs, métricas y disponibilidad.
- Figma con integración oficial para diseño.
- Dispositivos Android/iOS y números de prueba.

No se comprometerá un proveedor de pagos en el MVP; los enlaces externos pertenecen a cada negocio.

## 5. Estrategia de Git y entrega

- Rama principal protegida y cambios mediante pull request.
- CI: formato en modo check, análisis estático, pruebas, OpenAPI, migraciones y escaneo de secretos/dependencias.
- Builds internos automáticos desde ramas de release.
- Migraciones compatibles hacia atrás; despliegue de esquema antes del código que lo consume.
- Feature flags para categorías sanitarias, zonas, reseñas, planes y nuevas funciones.
- Versionado semántico de API y releases móviles con changelog.

## 6. Estrategia de pruebas

### Automatizadas

- Dominio: estados, permisos, precios, horarios y políticas.
- Persistencia: PostGIS, rangos, restricciones e aislamiento.
- API: autenticación, idempotencia, paginación y errores.
- Flutter: widgets, navegación, estado y accesibilidad.
- E2E: onboarding Pro, moderación, búsqueda, reserva automática/manual, reprogramación y reseña.
- Concurrencia: al menos 50 intentos simultáneos sobre un slot; máximo una reserva ocupante.
- Notificaciones: reintentos sin duplicar mensajes.

### Manuales

- Android/iOS de gama media y red degradada.
- Ubicación permitida, precisa, aproximada y denegada.
- Background/foreground durante OTP y reserva.
- Carga interrumpida de imágenes/documentos.
- Lectores de pantalla, fuente grande y contraste.
- Revisión de tiendas y deep links.

## 7. Criterios de salida a piloto

- Cero defectos críticos o altos abiertos en reserva, privacidad, pagos declarados o aislamiento.
- Todos los recorridos críticos aprobados en staging.
- Negocio no aprobado imposible de descubrir.
- Consultorio sin verificación imposible de publicar.
- Cero solapamientos en prueba concurrente.
- Restauración de backup demostrada.
- Alertas y runbooks probados.
- Términos, privacidad, consentimientos y retención revisados legalmente.
- 25–40 negocios configurados con oferta útil y horarios reales.

## 8. Operación del piloto

- Despliegue por feature flag y distribución gradual en tiendas.
- Canal de soporte para negocios con horario y SLA definidos.
- Revisión diaria de fallos y reservas durante las primeras dos semanas.
- Revisión semanal de activación, citas, conversión, no-show y retención.
- Entrevistas quincenales con consumidores y negocios.
- No activar cobros hasta validar valor, soporte y disposición de pago.

### Decisiones de expansión

- Expandir a Quito cuando la operación local sea estable, al menos 60% de negocios activados use la agenda semanalmente y no existan incidentes críticos de reservas durante cuatro semanas.
- Activar planes pagados únicamente después de entrevistar negocios activos y fijar límites/precios en una revisión del PRD.
- Integrar pagos solo mediante un TRD específico que cubra conciliación, devoluciones, disputas, impuestos y cumplimiento.

## 9. Riesgos y mitigación

| Riesgo | Mitigación |
|---|---|
| Marketplace con poca oferta | captar y configurar negocios antes de abrir al consumidor |
| Fricción por app obligatoria | onboarding breve, deep links diferidos y valor claro antes del registro |
| Cruces de agenda | restricciones PostgreSQL, transacciones e idempotencia |
| Costos de mapas/OTP | cuotas, caché, alertas y adaptadores sustituibles |
| Negocios falsos | moderación previa y denuncias |
| Exposición de domicilios | ubicación aproximada y reglas de revelación |
| Riesgo sanitario | verificación, minimización y ausencia de datos clínicos |
| Alcance horizontal excesivo | categorías controladas, núcleo universal y funciones avanzadas fuera del MVP |
| Equipo pequeño | monolito modular, servicios administrados y automatización CI/CD |

## 10. Definición de terminado

Una historia está terminada cuando cumple criterios funcionales, pruebas automatizadas, accesibilidad relevante, telemetría, manejo de errores, revisión de seguridad, documentación del contrato y aceptación del Product Owner en staging.

