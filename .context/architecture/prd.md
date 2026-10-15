# Product Requirement Document (PRD): Cita.ai

> Estado del documento: 15/10/2026. Proyecto existente (Brownfield). Este PRD reconstruye la intención y el estado conocido a partir de la documentación disponible; describir una función no confirma que esté implementada. La especificación funcional v0.3 está desactualizada y no se toma como descripción del producto actual cuando hay evidencia posterior.

## 1. Introducción y objetivos

* **Visión:** ayudar a profesionales independientes de 1 a 3 empleados a organizar sus turnos y permitir que sus clientes reserven sin coordinar por mensajes. El profesional comparte su página pública; Cita.ai no es un marketplace ni busca clientes por él.
* **Objetivo de esta versión:** documentar el comportamiento existente y hacer explícitas las brechas de producto que afectan el valor ya prometido. No hay una definición acordada de un próximo release ni una prioridad de implementación aprobada.
* **Alcance funcional documentado:** cuenta individual de profesional; disponibilidad y agenda; página pública con auto-reserva; gestión de reservas y cancelaciones por enlace; mails transaccionales; plan gratuito con un calendario y hasta 10 clientes únicos. El botón y el plan pago no están resueltos.
* **Fuera de alcance acordado:** marketplace, pagos, sincronización con Google Calendar, servicios múltiples con precios distintos, formularios de admisión, reportes y app móvil nativa. Se requiere que la web funcione en celular, pero no hay criterios de compatibilidad definidos.
* **Límites actuales conocidos:** no admite varios profesionales por cuenta. El recordatorio del día anterior no está implementado y quedó fuera de la siguiente iteración según la transcripción más reciente. El enlace público no se muestra claramente en el panel, según soporte y la reunión de mayo.

## 2. Personas usuarias

* **Profesional independiente:** administra su agenda y comparte su enlace. Trabaja solo o con hasta 3 empleados, cobra por hora y busca reducir coordinación manual. Referencias: Laura (psicóloga) y Carlos (entrenador). Hay necesidades diversas de duración y horario; no se deben generalizar sus casos como reglas universales.
* **Cliente final que reserva:** quiere consultar disponibilidad, confirmar un turno sin esperar respuesta y poder cancelarlo sin escribir al profesional. Sofía es el perfil de referencia digital; David no se consideró representativo.
* **Persona que reserva para otra:** madres/padres que reservan para sus hijos u otra persona que coordina por un tercero. El producto solo registra nombre y mail; qué datos corresponden al asistente y al asistente del turno está sin definir.

## 3. Funcionalidades principales

### Feature 1: Cuenta del profesional
* **Descripción:** registro e ingreso del profesional para administrar su cuenta. El producto actual trata a todos los registros como profesionales.
* **Valor:** habilitar el autoservicio sin configuración técnica compleja.
* **Criterios de éxito documentados:** promesa de poder registrarse y tener el enlace de reservas funcionando en menos de 5 minutos (objetivo de producto, no métrica validada). Seis consultas de soporte indican que profesionales nuevos no encuentran su enlace; mostrarlo y facilitar su copia es una brecha prioritaria identificada, no una función confirmada.

### Feature 2: Disponibilidad, agenda y turnos
* **Descripción:** el profesional define horario de atención, consulta sus turnos y puede administrarlos. La página pública ofrece horarios disponibles para reservar.
* **Valor:** reducir el intercambio de mensajes y el riesgo de superponer horarios.
* **Criterios de éxito:** el cliente puede elegir un horario disponible y obtener una confirmación; el profesional recibe aviso de la reserva. La auto-reserva superior al 60 % de las citas y el ahorro de al menos 30 minutos semanales fueron hipótesis de medición del equipo, sin resultados publicados.
* **Estado y huecos:** hubo dos casos de superposición; uno se atribuyó a zona horaria y se dijo resuelto en abril de 2026, pero la causa del otro no está confirmada. No hay definición acordada sobre reservas concurrentes, anticipación máxima, bloqueo de fechas con turnos existentes, ni duración configurable más allá de lo descrito históricamente.

### Feature 3: Página pública y reserva del cliente
* **Descripción:** cada profesional tiene una URL pública propia que comparte con su audiencia. El cliente consulta disponibilidad y reserva sin crear cuenta, proporcionando nombre y mail.
* **Valor:** permitir reservar cuando el profesional no está disponible para responder y eliminar el ida y vuelta de coordinación.
* **Criterios de éxito documentados:** el cliente obtiene confirmación y puede identificar que el turno quedó reservado. La entrevista de Sofía propone completar una reserva en 30 segundos, pero es una expectativa individual, no un compromiso acordado.
* **Límites:** no hay buscador/marketplace. La dirección efectiva observada es `cita-ai.vercel.app`; `cita.ai` está comprado pero no apuntado. Reservar para otra persona y asociar al asistente real están sin definir.

### Feature 4: Cancelación y comunicaciones por correo
* **Descripción:** el mail de confirmación al cliente contiene un enlace de cancelación. Se documentan también avisos al profesional cuando se reserva y avisos a la otra parte cuando se cancela.
* **Valor:** dar autonomía al cliente y mantener informadas a ambas partes.
* **Estado:** se registró un fallo del enlace durante una semana de marzo de 2026, corregido según la reunión. No se verificó aquí el comportamiento actual. La ventana de cancelación no está definida; la transcripción dice que hoy se permite cancelar hasta un minuto antes.
* **Recordatorio:** solicitado desde el inicio y por usuarios, pero no implementado. Aunque un resumen automático dice incluirlo en la próxima iteración, la transcripción de la reunión aclara que queda afuera. Prevalece la transcripción como fuente primaria.

### Feature 5: Límite del plan gratuito
* **Descripción:** plan gratuito con un calendario activo y hasta 10 clientes únicos. Los clientes existentes pueden seguir reservando; el cliente número 11 se bloquea. El mensaje al alcanzar el límite debía felicitar al profesional.
* **Valor:** validar adopción y servir como mecanismo de conversión futura.
* **Estado y criterios:** el producto debe explicar el límite y qué acción puede tomar el profesional; el texto exacto del mensaje y del botón no está resuelto. El plan Pro, su precio y contenido no existen en la documentación disponible. La hipótesis de más del 15 % de clics entre quienes llegan al límite no tiene resultados publicados.

### Gaps frente a la visión

* No se cumple completamente la puesta en marcha en menos de cinco minutos: el enlace público no es fácil de encontrar.
* Falta el recordatorio prometido, que se presenta como parte central del valor y aparece repetidamente en soporte.
* La demanda de varios profesionales por cuenta (salón y red de consultorios de unos 20 profesionales) excede el modelo actual y no fue incorporada al alcance inicial.
* No se conoce el estado de todas las funciones descritas: el equipo reconoce que la demo exitosa no demuestra cobertura general ni permite determinar qué está terminado.

## 4. User journeys (flujos clave)

* **Alta y publicación:** el profesional se registra, configura su disponibilidad y obtiene su URL pública para compartir. El enlace debería quedar localizable desde el panel; la documentación indica que hoy no lo está de forma clara.
* **Reserva:** el cliente abre el enlace del profesional, revisa horarios disponibles, selecciona uno, ingresa nombre y mail y recibe confirmación con enlace de cancelación. Los detalles de validación y errores no están especificados en fuentes actuales.
* **Cancelación:** el cliente abre el enlace del correo y cancela; la otra parte recibe aviso. La ventana permitida y el tratamiento de turnos que coinciden con un bloqueo del profesional están pendientes.
* **Alcance del plan gratuito:** al intentar incorporar al cliente número 11, el flujo lo bloquea y ofrece una acción de upgrade/interés. El comportamiento exacto del banner y su texto requieren definición.

## 5. Requisitos no funcionales (NFRs)

* **Seguridad y acceso:** el panel no debería quedar accesible sin sesión; el ticket #69 seguía abierto en mayo de 2026 y su estado actual es desconocido. No hay política de autenticación, autorización, privacidad, retención o protección de datos documentada en las fuentes revisadas.
* **Rendimiento y disponibilidad:** no hay objetivos acordados. La especificación v0.3 contiene TBD y las notas técnicas dicen que no son requisitos acordados. Los mails se describen como síncronos y pueden alargar la respuesta de reserva; esto es un estado técnico documentado, no un umbral de rendimiento.
* **Compatibilidad:** se espera uso web en celular; navegadores y dispositivos soportados no están definidos.
* **Ambientes y datos:** al 21/05/2026 había un único ambiente conectado a datos reales, sin copia propia ni forma de restaurar los datos. Las pruebas podían afectar a usuarios y enviar correos reales. Estado posterior no verificado; tratar como riesgo operativo vigente hasta confirmación.
* **Correo:** no está resuelto qué proveedor se usa (SendGrid, Supabase o Resend); los mensajes salen de un dominio de prueba no verificado según la nota técnica de QA. No hay requisito de entrega o tiempo acordado.

## 6. Riesgos y mitigaciones

* **Pruebas sobre datos reales:** confirmar ambientes, respaldo y procedimiento seguro antes de validar flujos; la evidencia disponible describe un único ambiente real sin restauración.
* **Reservas solapadas y zonas horarias:** documentar y verificar concurrencia y zona horaria; una de las causas históricas sigue sin confirmar.
* **Expectativa incumplida:** visibilidad del enlace y recordatorio ausente afectan promesas centrales. Prioridad de corrección requiere decisión del equipo.
* **Demanda multi-profesional:** oportunidad comercial no soportada, con impacto estructural señalado por desarrollo; decidir si queda fuera o se evalúa en una iniciativa aparte.
* **Conversión sin oferta definida:** el límite puede bloquear reservas sin una opción paga definida; resolver experiencia, texto y modelo comercial.
* **Soporte sin guardia:** una incidencia de cancelación tardó dos días en llegar al equipo; no hay objetivo ni cobertura de soporte acordados.

## Fuentes

| Dato / afirmación | De dónde sale |
| :--- | :--- |
| Visión, usuarios, enlace público, reserva sin cuenta, freemium, exclusiones y recordatorio originalmente requerido | `.context/Confluence-corporativo/01-minuta-kickoff.md` · acuerdos de kickoff |
| Necesidades y problemas de profesionales/clientes; perfiles de referencia; reserva para menores por sus padres; demanda multiagenda | `.context/Confluence-corporativo/02-notas-entrevistas.md` |
| Funciones y requisitos originalmente especificados | `.context/Confluence-corporativo/03-especificacion-funcional-v0.3.md` · borrador desactualizado; prevalecen fuentes posteriores |
| Stack, correo y notas técnicas | `.context/Confluence-corporativo/04-notas-tecnicas.md` |
| Alcance del lanzamiento y decisiones de correo/recordatorios | `.context/Confluence-corporativo/05-hilo-mail-cambio-de-alcance.md` |
| Consultas de soporte, enlaces, cancelación, límite y duplicados | `.context/Confluence-corporativo/06-tickets-soporte-resumen.md` |
| Incorporación de QA e interés de red de consultorios | `.context/Confluence-corporativo/documentacion para QA/hilo-mail-alcance-qa.md` |
| URL activa, un ambiente real, riesgos de pruebas y accesos | `.context/Confluence-corporativo/documentacion para QA/nota-ambientes-y-accesos.md` · estado indicado al 21/05/2026; no revalidado |
| Resumen de reunión, incluidas decisiones resumidas que requieren contraste | `.context/Confluence-corporativo/documentacion para QA/resumen-automatico-reunion-2026-05-19.md` · resumen automático |
| Resolución del recordatorio, ambigüedades de agenda, turnos duplicados y áreas de trabajo | `.context/Confluence-corporativo/documentacion para QA/transcripcion-reunion-2026-05-19.md` · fuente primaria frente al resumen automático |
| Estado de la Home y etiqueta «Regístrate gratis» | Observación consignada en `.context/idea/business-model.md` el 15/10/2026; no se hizo una nueva navegación durante esta ejecución |
| Criterios de éxito: 30 minutos ahorrados, retención >40 % a 4 semanas, auto-reserva >60 %, clics >15 % al límite | `01-minuta-kickoff.md` y `05-hilo-mail-cambio-de-alcance.md` · **hipótesis del equipo**, sin métricas de resultados |
| Reducción de soporte al mostrar el enlace, 30 segundos para reservar y corrección de brechas | Inferencia de necesidades expresadas en entrevistas y soporte; **hipótesis**, no requisito acordado |

## Contradicciones detectadas

* **Recordatorio:** kickoff y especificación v0.3 lo requieren; notas y cambio de alcance indican que no se implementó; el resumen automático sugiere incluirlo, pero la transcripción dice explícitamente que queda afuera. Se toma la transcripción como decisión más reciente y fuente primaria: no está implementado y no entra en la siguiente iteración.
* **Ambientes:** notas técnicas y especificación describen UAT/producción separados; la nota posterior de Diego indica un solo ambiente real. Se toma la nota del 21/05/2026 para ese estado; no se verificó si cambió después.
* **URL:** documentos iniciales nombran `cita.ai`; nota técnica de QA y observación del 15/10/2026 indican `cita-ai.vercel.app`, mientras `cita.ai` no apunta al hosting. Se toma la URL efectiva observada.
* **Turnos duplicados:** soporte y resumen automático atribuyen ambos casos a zona horaria; en la transcripción solo el segundo se confirma resuelto por ese motivo y Diego admite que asumió la causa del primero. Se deja el primer caso sin causa confirmada.
* **Proveedor de correo:** documentos mencionan SendGrid, Supabase y Resend. No se elige uno porque las fuentes no resuelven cuál está en uso.
* **Duración del soft launch:** hilo de correo indica ocho semanas; transcripción corrige a once. No se resuelve en este PRD porque la cifra no modifica un requisito funcional.
* **Botón de límite:** distintas fuentes proponen «Solicitar Upgrade», «Ver Opciones» y «Más información sobre el Plan Pro». No hay decisión final verificable.
* **Organización del producto:** resumen automático propone tres áreas; transcripción propone cuenta, agenda, página pública y correos, con límite como área aparte. La organización no se trata como requisito funcional ni se fuerza una estructura definitiva.

## Preguntas abiertas

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
