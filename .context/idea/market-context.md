# Contexto de Mercado: Cita.ai

> Estado a 15/10/2026. Los números `01` a `10` remiten a los documentos de `.context/Confluence-corporativo/` listados en `.context/idea/business-model.md`. Los precios de competidores se leyeron en sus páginas públicas el 15/10/2026.

## 1. Panorama Competitivo (Competitive Landscape)
| Competidor | Fortalezas | Debilidades | Diferenciador vs Nosotros |
| :--- | :--- | :--- | :--- |
| **Calendly** | Muy conocido y simple (`01`). Plan Free permanente. Standard 10 y Teams 16 USD por usuario al mes (web). | Free limitado a **un tipo de evento**. **Recordatorios solo en planes de pago** (web). Pensado para reuniones: una nutricionista lo dejó porque no permitía lista de pacientes (`02`, entrevista 7). | Cita.ai guarda clientes y tiene página de negocio. **Hoy no tiene recordatorios**, ni gratis ni de pago. |
| **Acuity Scheduling** | Potente (`01`). Prueba de 7 días, desde 16 USD/mes (web). Es de Squarespace (`01`). | Sin plan gratis permanente (web). Configurarlo "es un trabajo" (`01`, opinión del equipo). | Cita.ai es gratis hasta 10 clientes. La puesta en marcha en minutos es una promesa que hoy no se cumple del todo (`06`). |
| **SimplyBook.me** | Plan **gratis permanente de 50 reservas**. Basic 13,9, Standard 29,9 y Premium 59,9 USD/mes. Sin comisión por transacción ni cobro por usuario (web). | "Interfaz vieja" y "features confusos" (`01`, opinión del equipo). | **Mismo modelo freemium, con límite distinto:** ellos por reservas, Cita.ai por clientes únicos. |
| **Google Calendar** | Ya lo usan los profesionales (`02`, `01`). | Sin auto-reserva propia ni página de negocio (hipótesis). | La pelea real es seguir como hoy, no elegir entre apps (`01`). |
| **WhatsApp** | Es donde ya coordinan turnos (`01`, `02`). | "Ping-pong" de hasta ocho mensajes por turno (`02`, Laura). | Cita.ai elimina el intercambio de mensajes. |

## 2. Oportunidad de Mercado
*   **Tamaño/Tendencia:** el mercado global de software de agendamiento ronda los 400 M USD (2024) y crece entre 11 % y 13 % anual (`01`). Es una estimación de informes públicos que el propio documento no toma como verdad, y no se pudo contrastar con una fuente externa.
*   **Gap de Mercado:** simplicidad radical para quien trabaja solo y cobra por hora. Calendly queda corto para un negocio y Acuity resulta complejo de configurar (`01`, `02`). Los competidores gratuitos limitan por volumen (un evento, 50 reservas), no por clientes únicos.

## 3. Nuestra Ventaja Injusta (Unfair Advantage)
*   **Hoy es débil.** Lo defendible es el posicionamiento ("un profesional, una agenda") y el plan gratuito.
*   **Matiz verificado:** en Calendly los recordatorios solo están en planes de pago. Un Cita.ai con recordatorio gratuito sería un diferenciador real, pero **hoy no lo tiene**: no está implementado y quedó fuera de la siguiente iteración (`10`). El ticket #48 afirma que "todas las apps mandan uno" (`06`).

## 4. Riesgos y Supuestos
*   **Adopción:** barreras técnicas bajas, "mucho ruido" y costo alto por usuario conseguido (`01`). Cambiar cuesta porque ya usan algo "suficientemente bueno".
*   **Producto:** el recordatorio, que `01` y `03` presentan como la mitad del valor, es lo más pedido en soporte (`06`, `10`).
*   **Conversión:** el cliente que choca con el límite no entiende qué pasó y el profesional pierde la reserva (`06`, ticket #61).
*   **Oportunidad comercial no soportada:** una red de consultorios de ~20 profesionales exige multi-profesional, que no existe (`07`, `10`).
*   **Supuesto:** que el plan gratuito con límite de 10 clientes lleve a pagar. No hay métricas del soft launch.

## Fuentes
| Dato / afirmación | De dónde sale |
| :--- | :--- |
| Calendly: Free con un tipo de evento, Standard 10 y Teams 16 USD por usuario al mes, recordatorios desde Standard | `calendly.com/pricing`, leído con Playwright el 15/10/2026 |
| Acuity: prueba de 7 días, desde 16 USD/mes | `acuityscheduling.com/pricing`, el 15/10/2026 |
| SimplyBook.me: plan gratis de 50 reservas y planes de 13,9 a 59,9 USD/mes | `simplybook.me/en/pricing`, el 15/10/2026 |
| Los tres competidores principales y el posicionamiento "Acuity complejo, Calendly básico" | `01` · Contra quién competimos |
| Nutricionista que dejó Calendly por falta de lista de pacientes | `02` · Entrevista 7 |
| Competidores no convencionales: Google Calendar y WhatsApp | `01` · Contra quién competimos; `02` |
| Mercado de ~400 M USD y crecimiento de 11-13 % | `01` · El tamaño de la torta. **Hipótesis:** estimación sin fuente verificada |
| Recordatorio no implementado | `04`, `05`, `10` |
| Redes de consultorios y falta de multi-profesional | `07`, `10`, `06` (#22) |
| "Acuity es complicado" e "interfaz vieja" de SimplyBook.me | `01`. **Hipótesis:** opinión del equipo, sin evidencia independiente |
| Google Calendar sin auto-reserva ni página de negocio | **Hipótesis** — no hay documento ni consulta que lo respalde |
| "Todas las apps mandan un recordatorio" | `06` · ticket #48. Dicho por un cliente, no verificado |

## Contradicciones detectadas
*   **Ventaja competitiva frente al estado real.** `01` y `03` venden el recordatorio como la mitad del valor. `04`, `05` y `10` dicen que no existe. **Tomé `10`:** la ventaja no está hoy. Se mantiene la resolución del canvas (`business-model.md`, A1).
*   **SimplyBook.me "tiene plan gratis".** `01` lo afirma sin detalle y la web confirma un límite de 50 reservas. Coinciden, y la web aporta el límite.
*   **Calendly "no tiene clientes ni paquetes".** `01` lo afirma y `02` (entrevista 7) lo respalda, pero solo es verificable por el testimonio de esa usuaria. No se comprobó en el producto actual. Las diferencias de URL, ambientes y turnos duplicados se heredan del canvas y no se repiten aquí.

## Preguntas abiertas
*   Si Acuity y SimplyBook.me incluyen recordatorios y en qué plan.
*   Qué plan de Acuity corresponde a un profesional solo.
*   Cuántos competidores ofrecen recordatorio por defecto: confirmado solo para Calendly (plan Standard, de pago).
*   Tamaño de mercado: no hay fuente externa verificada.
*   Cómo se posicionan Google Calendar y WhatsApp Business frente a Cita.ai: no se investigaron sus sitios.
*   Si Cita.ai está desactualizado frente a las tendencias: no hay evidencia sobre IA para sugerir horarios, que `01` deja como idea a futuro.
*   Datos de adquisición y conversión: ninguno disponible.
*   Competidores no listados en `01`.
