# Business Model Canvas: Cita.ai

**Tipo de proyecto:** Brownfield

> Estado a 15/10/2026. Fuentes: los 10 documentos de `.context/Confluence-corporativo/` (incluida la subcarpeta `documentacion para QA`) y la navegación pública de `https://cita-ai.vercel.app/login`. Numeración de documentos usada en este archivo: ver tabla de Fuentes.

## 1. Propuesta de Valor (Value Propositions)
*   Auto-reserva simple para profesionales independientes: el cliente final elige un horario, sin cuenta ni contraseña (solo nombre y mail), y cancela con un enlace en el mail de confirmación (01, 03).
*   Cada profesional tiene su página pública propia, `cita-ai.vercel.app/<slug>`, que comparte en su bio de Instagram, su estado de WhatsApp o su web. "Nosotros no le traemos clientes. Le ordenamos los que ya tiene." (01, 08).
*   Posicionamiento: "Acuity es demasiado complejo y Calendly es demasiado básico" (01).
*   Promesa: registrarse y tener el link de reservas funcionando en menos de 5 minutos (01, 03). **Hoy no se cumple del todo:** el panel no muestra al profesional cuál es su link. Es la consulta número uno de los profesionales nuevos, con 6 consultas registradas (06, 10).
*   **El recordatorio del día anterior, que 01 y 03 presentan como la mitad del valor, no está implementado** (ver contradicción A1).

## 2. Segmentos de Clientes (Customer Segments)
*   **Profesional independiente** de 1 a 3 empleados, cuyo producto es su tiempo (psicólogos, entrenadores, estilistas, tutores). Mercado inicial en español (01). Perfiles de referencia: Laura (psicóloga) y Carlos (entrenador) (02).
*   **Cliente final**, sin cuenta. Perfil de referencia: Sofía, baja tolerancia a la fricción (02).
*   **Oportunidad comercial no soportada:** una red de consultorios de unos 20 profesionales y otras dos reuniones agendadas (07, 10). El producto no admite varios profesionales por cuenta, y Diego dice que no se puede "sin tocar la base entera" (10).

## 3. Canales (Channels)
*   La URL pública del profesional, compartida en los canales donde ya tiene su audiencia (01). No hay buscador ni marketplace; se descartó expresamente (01).
*   Soft launch con 32 profesionales conocidos, conseguidos por Fernando (05).
*   Reuniones comerciales con potenciales clientes, demos hechas por Fernando (07, 10).
*   La Home (`/`) redirige a `/login`: no hay landing pública (observado el 15/10/2026).

## 4. Relación con Clientes (Customer Relationships)
*   Autoservicio, con mails transaccionales de confirmación, aviso de reserva y aviso de cancelación (05, 08).
*   Soporte por casilla de correo, sin guardia. Un incidente de cancelación tardó dos días en llegar al equipo (10).
*   La web ofrece "Regístrate gratis" y el texto "Demo: Registra un usuario nuevo para probar" (observado).

## 5. Fuentes de Ingresos (Revenue Streams)
*   Hoy no hay ingresos. Modelo freemium: plan gratuito hasta 10 clientes únicos por profesional y un solo calendario por cuenta (01, 03).
*   El límite se concibe como el negocio: "lo único que después nos va a dar plata" (10).
*   El plan pago no existe, ni su precio ni su contenido. El botón del banner solo registra interés. **Nombre del botón sin resolver (M2):** "Solicitar Upgrade" (01), "Ver Opciones" (03), "Más información sobre el Plan Pro" (05).

## 6. Recursos Clave (Key Resources)
*   Equipo de 4 personas: Mariana (producto), Diego (desarrollo), Sol (diseño y soporte), Fernando (comercial), más un perfil de QA que se incorpora desde mayo de 2026 (07, 10).
*   Producto desplegado en Next.js, Supabase y Vercel (04).
*   Dominio `cita.ai`, comprado y a nombre de la empresa, pero sin apuntar (08).
*   Entrevistas con 7 profesionales y clientes (02) y resumen de soporte de marzo a mayo de 2026 (06).

## 7. Actividades Clave (Key Activities)
*   Soft launch: **8 semanas (05) / 11 semanas (10), sin resolver (M3)**.
*   Reconstruir la especificación, armar el backlog y probar, con tres semanas para lo primero (07).
*   Organizar la documentación por áreas de trabajo: **tres (09) / cuatro más el límite aparte (10), sin resolver (M5)**.
*   Atender soporte y resolver deuda técnica conocida: recordatorio, concurrencia en la reserva, zonas horarias, URL pública no visible, acceso al panel sin sesión (04, 06).

## 8. Socios Clave (Key Partners)
*   Vercel (hosting) y Supabase (base de datos y autenticación) (04).
*   Proveedor de mails: **Resend (05), servicio de Supabase (04) o SendGrid (01), sin resolver (M1)**. Sin dominio propio verificado (05, 08).

## 9. Estructura de Costos (Cost Structure)
*   Hosting en Vercel y Supabase, mails y tiempo del equipo. **No hay cifras en ningún documento.**
*   Subir al plan de Vercel que permita tareas programadas supone "dos o tres días de trabajo más la plata" (05, 10).
*   Adquisición de usuarios: "conseguir cada usuario cuesta plata" (01). Sin cifra.

## Problem Statement (Resumen)
*   El profesional independiente pierde tiempo coordinando turnos por WhatsApp, Instagram y llamadas. Laura lo estimó en 4 horas semanales, y el resto entre media hora y dos horas (02). Sufre dobles reservas y pierde horarios por cancelaciones de último momento, sin una herramienta simple para evitarlo (01, 02).

## Fuentes
| N.º | Documento | Fecha |
| :--- | :--- | :--- |
| 01 | `01-minuta-kickoff.md` | 14/11/2024 |
| 02 | `02-notas-entrevistas.md` | nov-dic 2024 |
| 03 | `03-especificacion-funcional-v0.3.md` | borrador |
| 04 | `04-notas-tecnicas.md` | 30/10/2025 |
| 05 | `05-hilo-mail-cambio-de-alcance.md` | feb-mar 2026 |
| 06 | `06-tickets-soporte-resumen.md` | mar-may 2026 |
| 07 | `documentacion para QA/hilo-mail-alcance-qa.md` | 20-21/05/2026 |
| 08 | `documentacion para QA/nota-ambientes-y-accesos.md` | 21/05/2026 |
| 09 | `documentacion para QA/resumen-automatico-reunion-2026-05-19.md` | 19/05/2026 |
| 10 | `documentacion para QA/transcripcion-reunion-2026-05-19.md` | 19/05/2026 |

| Dato / afirmación | De dónde sale |
| :--- | :--- |
| Cliente final sin cuenta, cancelación por enlace | `01`, `03` |
| Posicionamiento entre Acuity y Calendly | `01` |
| Plan gratuito de 10 clientes únicos y un calendario | `01`, `03`, `04` |
| 32 profesionales en el soft launch | `05` |
| URL real `cita-ai.vercel.app` y un solo ambiente | `08`; URL confirmada por navegación el 15/10/2026 |
| Link no visible en el panel, 6 consultas | `06`, `10` |
| 4 horas semanales de coordinación (Laura) | `02` |
| Red de consultorios de ~20 profesionales | `07`, `10` |
| Tagline "Gestión inteligente de citas y turnos" y botón "Regístrate gratis" | Observado en `/login` el 15/10/2026 |
| Mercado de ~400 M USD y crecimiento de 11-13 % anual | `01`, estimación de informes públicos que el propio documento no toma como verdad |
| Objetivo de 5.000-10.000 usuarios activos en 2 años | `01`, hipótesis del equipo |
| Hipótesis de ahorrar 30 min semanales, retención a 4 semanas superior al 40 % y auto-reserva superior al 60 % | `01`, `05`, hipótesis sin medición publicada |
| Costos del plan de Vercel, Supabase, Resend y adquisición | **Hipótesis** — no hay documento con cifras |
| Precio y contenido del plan pago | **Hipótesis** — no existe en ningún documento |

## Contradicciones detectadas

### Resueltas (impacto alto)

*   **A1. Recordatorio del día anterior.** `01` y `03` lo declaran requisito. `04` y `05` dicen que no está hecho ni entra en el lanzamiento. `09` lo lista como decisión "incluir en la próxima iteración", pero `10` dice "Queda afuera, por tercera vez". **Tomé `10`:** es la transcripción, fuente primaria, y `09` es un resumen automático que "puede contener errores". Estado: no implementado y fuera de la siguiente iteración. Es el mayor desvío entre la propuesta de valor y el producto.
*   **A2. Ambientes.** `03` y `04` describen UAT y producción con bases separadas. `08` dice que hoy hay uno solo, el de los usuarios reales. **Tomé `08`:** es el más reciente (21/05/2026) y lo escribe Diego, autor de `04`, que se desdice. Todo lo que se pruebe afecta datos reales y no hay forma de volver atrás.
*   **A3. URLs.** `01`, `03` y `04` usan `cita.ai` y `uat.cita.ai`. `08` y la web observada usan `cita-ai.vercel.app`. **Tomé `08` y la web:** es lo que usan los usuarios. `cita.ai` está comprado y sin apuntar.
*   **A4. Turnos duplicados.** `06` (#33) dice "las dos reservaron por el link". `10` dice que una la cargó la profesional a mano. `10` también dice que el segundo caso fue zona horaria, resuelto en abril de 2026, y de Diego sobre el primero: "lo asumí". `09` afirma que ambos están resueltos. **Tomé `10`:** segundo caso resuelto, **causa del primero no confirmada**. No la completé con una hipótesis.

### Planteadas, sin resolver (impacto medio)

*   **M1. Proveedor de mails.** `01`: SendGrid. `04`: servicio de Supabase. `05`: Resend. **Sin resolver.**
*   **M2. Nombre del botón del límite.** `01`: "Solicitar Upgrade". `03`: "Ver Opciones". `05`: "Más información sobre el Plan Pro". **Sin resolver.** No se pudo verificar en la app sin sesión.
*   **M3. Duración del soft launch.** `05`: 8 semanas. `10`: "Once semanas, en realidad". **Sin resolver.**
*   **M4. "Balance positivo".** `09` lo afirma. En `10` nadie da métricas y Mariana dice que "anda" no se sabe. **Sin resolver**, no se afirma el balance.
*   **M5. Áreas de trabajo.** `09`: tres áreas. `10`: Sol propone cuatro, y Fernando pide una quinta aparte, el límite. **Sin resolver.**

### Planteadas por falta de instrucción (contexto)

*   **C1. Éxito esperado.** `01`: 5.000-10.000 usuarios activos en 2 años. `05`: métricas del soft launch. Son horizontes distintos y ninguno tiene resultados.
*   **C2. Multi-profesional.** `01` y `03` lo dejan fuera de alcance. `02`, `06` y `10` muestran demanda real.
*   **C3. Especificación v0.3.** Ya no describe el producto. Se priorizaron `08`, `10`, `05` y `06` sobre ella.
*   **C4. Performance y disponibilidad.** `03` los deja como TBD y `04` aclara que no son requisitos acordados. Se excluyeron del canvas.

## Preguntas abiertas
*   Precio y contenido del Plan Pro.
*   Coste real de Vercel, Supabase, Resend y de la adquisición de usuarios.
*   Resultados del soft launch: ningún documento da métricas de activación, retención ni auto-reserva.
*   Causa del primer caso de turnos duplicados (A4).
*   Cuál de los proveedores de mails está en uso hoy (M1), y si hay dominio verificado.
*   Nombre definitivo del botón del límite (M2) y estado del banner en el panel.
*   Cuántas semanas duró realmente el soft launch (M3) y cuántas áreas de trabajo se adoptan (M5).
*   Si y cuándo se contratará el plan de Vercel o un servicio externo para el recordatorio.
*   Estrategia para redes de consultorios: la demanda existe, pero no hay soporte multi-profesional.
*   Qué ocurre con los turnos ya reservados cuando el profesional bloquea un período, ventana mínima de cancelación y reserva para otra persona: todo sin decidir (10).
*   Si se corrigió el acceso al panel sin sesión (ticket #69, abierto en mayo de 2026).
*   Si el dominio `cita.ai` se apuntará al hosting.
*   Limitaciones de este análisis: la Home redirige a `/login`, sin landing pública, por lo que la propuesta de valor no se extrajo de la web. No se inició sesión, así que panel y banner quedan sin verificar. El MCP de Atlassian no se usó porque el Confluence corporativo no es accesible. Falta la lista de puntos sin definir de Sol, mencionada en `10`.
