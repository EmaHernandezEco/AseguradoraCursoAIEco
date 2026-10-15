# Dudas abiertas de las fases 1 a 3

Consolidado de las secciones **“Preguntas abiertas”** de los entregables principales disponibles en `.context`. Se conserva el contenido y se referencia el archivo de origen y la fase correspondiente.

## Fase 1 — Constitución

### Business Model Canvas
**Origen:** `.context/idea/business-model.md`

* Precio y contenido del Plan Pro.
* Coste real de Vercel, Supabase, Resend y de la adquisición de usuarios.
* Resultados del soft launch: ningún documento da métricas de activación, retención ni auto-reserva.
* Causa del primer caso de turnos duplicados (A4).
* Cuál de los proveedores de mails está en uso hoy (M1), y si hay dominio verificado.
* Nombre definitivo del botón del límite (M2) y estado del banner en el panel.
* Cuántas semanas duró realmente el soft launch (M3) y cuántas áreas de trabajo se adoptan (M5).
* Si y cuándo se contratará el plan de Vercel o un servicio externo para el recordatorio.
* Estrategia para redes de consultorios: la demanda existe, pero no hay soporte multi-profesional.
* Qué ocurre con los turnos ya reservados cuando el profesional bloquea un período, ventana mínima de cancelación y reserva para otra persona: todo sin decidir (10).
* Si se corrigió el acceso al panel sin sesión (ticket #69, abierto en mayo de 2026).
* Si el dominio `cita.ai` se apuntará al hosting.
* Limitaciones del análisis: la Home redirige a `/login`, sin landing pública, por lo que la propuesta de valor no se extrajo de la web. No se inició sesión, así que panel y banner quedan sin verificar. El MCP de Atlassian no se usó porque el Confluence corporativo no es accesible. Falta la lista de puntos sin definir de Sol, mencionada en `10`.

### Contexto de Mercado
**Origen:** `.context/idea/market-context.md`

* Si Acuity y SimplyBook.me incluyen recordatorios y en qué plan.
* Qué plan de Acuity corresponde a un profesional solo.
* Cuántos competidores ofrecen recordatorio por defecto: confirmado solo para Calendly (plan Standard, de pago).
* Tamaño de mercado: no hay fuente externa verificada.
* Cómo se posicionan Google Calendar y WhatsApp Business frente a Cita.ai: no se investigaron sus sitios.
* Si Cita.ai está desactualizado frente a las tendencias: no hay evidencia sobre IA para sugerir horarios, que `01` deja como idea a futuro.
* Datos de adquisición y conversión: ninguno disponible.
* Competidores no listados en `01`.

## Fase 2 — Arquitectura

### Product Requirement Document (PRD)
**Origen:** `.context/architecture/prd.md`

* ¿Cuál es el alcance y la prioridad del próximo release, incluido el recordatorio?
* ¿Cuál es el estado actual de implementación y verificación de cada flujo, especialmente la visibilidad del enlace, acceso al panel y cancelación?
* ¿Qué sucede con turnos ya reservados al bloquear fechas? ¿Hasta cuándo puede cancelar un cliente y con cuánta anticipación se puede reservar?
* ¿Cómo se gestionan reservas concurrentes, zonas horarias y el primer caso de turno duplicado?
* ¿Quién es la persona asistente y quién recibe el turno cuando alguien reserva para otra persona?
* ¿Se soportarán varias agendas/profesionales por cuenta? ¿Qué necesita la red de consultorios?
* ¿Qué proveedor de correo está activo y hay un dominio propio verificado?
* ¿Cuál es el texto y destino definitivos al alcanzar el límite? ¿Cuál será el precio y contenido del plan pago?
* ¿Cuáles son las métricas y resultados reales del soft launch? ¿Cuál fue su duración efectiva?
* ¿Cuáles son los objetivos acordados de seguridad, disponibilidad, rendimiento, compatibilidad y soporte?
* ¿Se restablecieron ambientes separados y respaldos desde la nota de mayo de 2026?
* ¿Se apuntará `cita.ai` al hosting? ¿Se incorporará una landing pública?
* ¿Qué limitaciones de las fuentes siguen vigentes? No se consultó Jira ni Playwright durante esta ejecución; el contexto indica que el Confluence corporativo no es accesible. También falta la lista de puntos pendientes de Sol mencionada en la transcripción.

### Diseño del Sistema y Arquitectura
**Origen:** `.context/architecture/system-design.md`

* ¿Se puede inspeccionar el repositorio y la configuración actuales para confirmar que el stack y las rutas documentadas siguen vigentes?
* ¿Qué proveedor de correo está conectado hoy y qué credencial/flujo autoriza de forma segura las cancelaciones públicas?
* ¿Existe actualmente un ambiente aislado, respaldo restaurable, seed y migraciones versionadas?
* ¿Qué políticas RLS concretas protegen cada operación y qué datos de clientes puede ver cada profesional?
* ¿Qué solución se adoptará para que las reservas concurrentes sean atómicas? ¿Qué índice requiere el conteo de clientes?
* ¿Cuáles son los objetivos aprobados de rendimiento, concurrencia, disponibilidad, recuperación y compatibilidad?
* ¿Qué prioridad tienen rate limiting, monitoreo, manejo de errores, correo asíncrono y soporte de medianoche?
* ¿Qué alcance de pruebas automatizadas se aprobará y dónde podrán ejecutarse sin afectar usuarios ni enviar correos reales?

## Fase 3 — Infraestructura

### Estrategia de Infraestructura y Entornos
**Origen:** `.context/infrastructure/environments.md`

* ¿Sigue Producción siendo el único ambiente? ¿UAT volvió con datos sintéticos y aislados?
* ¿Cuál es el procedimiento aprobado para probar, restaurar datos y evitar correos a usuarios reales?
* ¿Se corrigió el almacenamiento de credenciales y quién administra los accesos? No compartir credenciales en claro.
* ¿Siguen el deploy automático desde `main` y la ausencia de CI/tests? ¿Dónde está el repositorio de la aplicación para inspeccionar workflows/configuración?
* ¿Qué navegadores, sistemas operativos, dispositivos y resoluciones están soportados?
* ¿Hay restricciones actuales de red, VPN o acceso a Supabase?

### Estrategia de Datos de Prueba
**Origen:** `.context/infrastructure/test-data-strategy.md`

* ¿Se recuperó UAT u otro entorno aislado? ¿Se alimenta exclusivamente con datos sintéticos?
* ¿Quién puede otorgar a QA acceso autorizado y de mínimo privilegio a una base segura? La respuesta actual es que QA no tiene acceso directo.
* ¿Hay usuarios fijos de prueba? ¿Qué roles deben cubrir y dónde se administran sus credenciales sin exponerlas?
* ¿Cuál es el proceso aprobado para crear, limpiar y restablecer datos tras una prueba?
* ¿Se corrigió la anonimización de `professionals` y se regeneran slugs ficticios?
* ¿Qué controles evitan que las pruebas envíen correos o creen turnos reales?


