# ToAgenda Ecuador — Flujos de aplicaciones

**Versión:** 1.0  
**FigJam:** [ToAgenda Ecuador — Flujo maestro MVP](https://www.figma.com/board/JLt7Snimw2ebPS3XjCyz60)  
**Prototipo Figma:** Pendiente de creación después de aprobar la fase de descubrimiento visual. Este documento es la fuente funcional; el prototipo no puede contradecirlo.

## 1. Estados oficiales

```mermaid
stateDiagram-v2
    [*] --> pending: Reserva manual
    [*] --> confirmed: Reserva automática
    pending --> confirmed: Negocio aprueba
    pending --> rejected: Negocio rechaza
    pending --> expired: Vence plazo
    confirmed --> checked_in: Cliente llega
    checked_in --> in_service: Inicia atención
    in_service --> completed: Finaliza
    confirmed --> no_show: No se presenta
    pending --> cancelled_by_consumer
    confirmed --> cancelled_by_consumer
    pending --> cancelled_by_business
    confirmed --> cancelled_by_business
```

Una reprogramación conserva el estado aplicable, registra el horario anterior y valida el nuevo espacio. Si una reserva manual cambia de fecha, vuelve a `pending`; una automática permanece `confirmed` después de una transacción exitosa.

## 2. Navegación — ToAgenda

Barra inferior:

1. **Inicio:** buscador, categorías, cerca de ti, disponible hoy y reservar nuevamente.
2. **Explorar:** filtros y alternancia lista/mapa.
3. **Citas:** pendientes, próximas e historial.
4. **Favoritos:** negocios guardados.
5. **Perfil:** cuenta, ubicación, notificaciones, privacidad y ayuda.

## 3. Alta y ubicación del consumidor

```mermaid
flowchart TD
    A[Abrir ToAgenda] --> B[Introducir teléfono]
    B --> C[Solicitar OTP]
    C --> D{OTP válido}
    D -- No --> E[Error y reintento limitado]
    D -- Sí --> F[Aceptar términos y privacidad]
    F --> G[Explicar beneficio de ubicación]
    G --> H{Concede permiso}
    H -- Sí --> I[Detectar coordenadas y confirmar zona]
    H -- No --> J[Elegir provincia, cantón y sector]
    I --> K[Inicio]
    J --> K
```

- No se solicita permiso antes de explicar para qué se utilizará.
- Negar ubicación nunca bloquea búsqueda ni reserva.
- Marketing es opcional y separado de comunicaciones operativas.

## 4. Descubrimiento y ficha

```mermaid
flowchart TD
    A[Inicio o Explorar] --> B[Buscar texto o elegir categoría]
    B --> C[Resultados en lista]
    C --> D{Cambiar a mapa}
    D -- Sí --> E[Mapa con marcadores y tarjetas]
    D -- No --> F[Aplicar filtros u ordenar]
    E --> G[Seleccionar negocio]
    F --> G
    G --> H[Ficha interna]
    H --> I[Elegir servicio]
    H --> J[Guardar favorito]
    H --> K[Compartir enlace profundo]
```

Estados contemplados: sin resultados, ubicación aproximada, negocio sin disponibilidad, red lenta, error recuperable, perfil suspendido y contenido aún no cargado.

## 5. Reserva

```mermaid
flowchart TD
    A[Elegir servicio] --> B[Elegir modalidad y local]
    B --> C[Elegir profesional o cualquiera]
    C --> D[Consultar disponibilidad]
    D --> E[Elegir fecha y hora]
    E --> F[Crear hold de 5 minutos]
    F --> G[Responder campos del servicio]
    G --> H[Elegir método de pago declarado]
    H --> I{Transferencia con comprobante}
    I -- Sí --> J[Adjuntar comprobante]
    I -- No --> K[Continuar]
    J --> L[Aceptar política]
    K --> L
    L --> M[Confirmar]
    M --> N{Modo del servicio}
    N -- Automático --> O[confirmed]
    N -- Requiere aprobación --> P[pending]
    O --> Q[Resumen y notificación]
    P --> Q
```

Fallos:

- Si vence el hold, se informa y se vuelve a disponibilidad.
- Si otro actor tomó el slot, se ofrecen alternativas próximas.
- Si falla la carga de comprobante, no se crea una reserva que lo requiera.
- Repetir una solicitud con la misma clave de idempotencia devuelve el mismo resultado.

## 6. Gestión de una cita

- `pending`: cancelar; esperar aprobación; ver tiempo límite.
- `confirmed`: cancelar o reprogramar según política, navegar y añadir a calendario.
- `rejected`/`expired`: ver motivo permitido y buscar otro horario.
- `completed`: volver a reservar y dejar una reseña.
- `cancelled_*`/`no_show`: consultar historial sin acciones operativas.

Reprogramar ejecuta: elegir nueva disponibilidad → crear hold → confirmar política → validar → liberar horario anterior solo cuando el nuevo quede reservado.

## 7. Navegación — ToAgenda Pro

Barra inferior:

1. **Hoy:** resumen y acciones urgentes.
2. **Agenda:** día, semana, mes y filtros.
3. **Clientes:** búsqueda, historial y notas operacionales.
4. **Equipo:** miembros, servicios y disponibilidad.
5. **Más:** negocio, locales, catálogo, pagos, reportes y soporte.

## 8. Incorporación del negocio

```mermaid
flowchart TD
    A[Registro Pro] --> B[Crear organización]
    B --> C[Elegir modalidad y categorías]
    C --> D[Identidad, banner y contacto]
    D --> E[Local o zona de cobertura]
    E --> F[Crear primer servicio]
    F --> G[Crear profesional y horario]
    G --> H[Configurar métodos de pago]
    H --> I{Categoría sanitaria}
    I -- Sí --> J[Cargar credenciales y permisos]
    I -- No --> K[Revisar resumen]
    J --> K
    K --> L[Enviar a moderación]
    L --> M{Decisión}
    M -- Cambios --> N[Corregir y reenviar]
    M -- Aprobado --> O[Publicar dentro de ToAgenda]
    M -- Rechazado --> P[Mostrar motivo y soporte]
```

El negocio puede operar en modo borrador, pero no recibir reservas del marketplace antes de aprobación.

## 9. Operación diaria Pro

```mermaid
flowchart TD
    A[Abrir Hoy] --> B[Ver próximas y pendientes]
    B --> C{Solicitud pending}
    C -- Aprobar --> D[Validar slot y confirmar]
    C -- Rechazar --> E[Registrar motivo y liberar]
    B --> F[Registrar llegada]
    F --> G[Iniciar servicio]
    G --> H[Completar y registrar pago declarado]
    B --> I[Crear cita manual]
    B --> J[Bloquear horario o ausencia]
```

- Si el slot dejó de ser válido al aprobar, el sistema no confirma y solicita proponer otro horario.
- Las acciones sensibles muestran confirmación y quedan auditadas.

## 10. Moderación administrativa

```mermaid
flowchart TD
    A[Cola de solicitudes] --> B[Revisar identidad y perfil]
    B --> C[Validar ubicación y contenido]
    C --> D{Categoría sanitaria}
    D -- Sí --> E[Validar documentos y vigencia]
    D -- No --> F[Tomar decisión]
    E --> F
    F --> G{Resultado}
    G -- Aprobar --> H[Publicar y notificar]
    G -- Solicitar cambios --> I[Despublicar y enviar observaciones]
    G -- Rechazar --> J[Registrar motivo y apelación]
    H --> K[Monitorear denuncias y vigencias]
    K --> L{Incumplimiento}
    L -- Sí --> M[Suspender y auditar]
```

## 11. Estructura del archivo Figma

1. `00 Cover & changelog`
2. `01 Foundations`
3. `02 Components`
4. `03 FigJam flows`
5. `04 Consumer wireframes`
6. `05 Consumer hi-fi`
7. `06 Pro wireframes`
8. `07 Pro hi-fi`
9. `08 Admin desktop`
10. `09 Prototype`
11. `10 States & accessibility`

El prototipo debe cubrir como mínimo: descubrimiento y reserva automática, reserva manual, onboarding Pro, aprobación administrativa y gestión diaria de una cita.
