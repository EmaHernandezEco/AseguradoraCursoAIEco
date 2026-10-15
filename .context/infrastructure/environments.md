# Estrategia de Infraestructura y Entornos: Cita.ai

> Proyecto Brownfield, aplicación web. Actualizado el 15/10/2026 con la evidencia disponible de 2025 y mayo de 2026. No se inspeccionó el repositorio de la aplicación ni la configuración desplegada.

## 1. Tipo de Aplicación y Alcance

* **Plataforma:** Web; Next.js en Vercel, API en rutas de Next.js y Supabase para PostgreSQL y autenticación.
* **Matriz de compatibilidad:** navegadores, sistemas operativos y resoluciones soportados no están documentados. El PRD espera uso web móvil, sin definir matriz ni tamaños. Requiere definición del equipo.

## 2. Mapa de Entornos (Matriz de URLs)

La nota del 21/05/2026 registra Producción como único ambiente en uso. UAT existió, pero llevaba meses sin utilizarse y se desconoce si aún funciona; no se lista como ambiente activo.

| Componente | Local | Producción |
| :--- | :--- | :--- |
| **Frontend** | URL local no documentada | \`https://cita-ai.vercel.app/\` |
| **Backend API** | Host local no documentado; rutas API de Next.js | Rutas bajo \`https://cita-ai.vercel.app/api\` (base derivada, no verificada en ejecución) |
| **Base de Datos** | Instancia local no documentada | Supabase con datos reales; host/conexión restringidos y no documentados |

### Detalles de Acceso

* **Credenciales de prueba:** la nota técnica menciona credenciales en un archivo de texto en la raíz, sin identificar el nombre, que no estaba en \`.gitignore\`. No se leyó ni se debe usar ese archivo. Solicitar cuenta y acceso mediante mecanismo autorizado; no incluir claves aquí.
* **VPN/restricciones:** no hay VPN documentada. No usar la cuenta de Fernando, que contiene datos reales. Altas, reservas y correos en Producción son reales y no hay restauración propia documentada. No probar allí sin procedimiento y autorización acordados.
* **UAT histórico:** \`uat.cita.ai\` y una base separada constan en las notas de 2025. La nota posterior indica que dejó de usarse y desconoce si sigue operativo. Su base se refrescaba desde Producción y conservaba nombres y correos reales de profesionales; no tratarlo como ambiente seguro.

## 3. Pipeline de CI/CD (Integración Continua)

* **Trigger documentado:** push a \`main\` dispara el despliegue a Vercel. Se documenta una sola rama (\`main\`) y variables cargadas manualmente en el panel.
* **Pruebas automáticas:** las notas técnicas dicen que no había GitHub Actions ni tests automatizados. No se inspeccionó el repositorio de aplicación para confirmar si esto sigue vigente.
* **Estado actual:** pipeline y proceso actual de liberación pendientes de confirmación.

## 4. Herramientas de Infraestructura

* **Vercel:** hosting y despliegue documentados.
* **Supabase:** PostgreSQL y autenticación gestionados.
* **Next.js:** aplicación y rutas API.
* Docker/Kubernetes no están documentados.

## 5. Riesgos del Mapa de Entornos

* Producción es el único ambiente activo según la evidencia más reciente; las pruebas pueden alterar datos y enviar correos reales.
* UAT está desactualizado, su disponibilidad no está confirmada y los datos históricos incluían información personal real.
* No hay restauración propia, seed ni migraciones versionadas documentadas.
* El despliegue directo desde \`main\`, sin CI ni tests, está descrito en 2025, pero falta confirmar su vigencia.
* Las credenciales de prueba se guardaban en un archivo de texto que no estaba excluido de Git; se desconoce si se corrigió. No acceder al archivo.
* Falta una matriz acordada de compatibilidad.

## Fuentes

| Dato / afirmación | De dónde sale |
| :--- | :--- |
| Stack, UAT/Producción, push a \`main\`, falta de CI/tests, credenciales, seed y migraciones | \`.context/Confluence-corporativo/04-notas-tecnicas.md\` · 30/10/2025; no verificado contra el repositorio actual |
| URL efectiva, Producción como único ambiente en uso, estado de UAT y riesgos de datos/acceso | \`.context/Confluence-corporativo/documentacion para QA/nota-ambientes-y-accesos.md\` · 21/05/2026 |
| Advertencia de que los datos cargados no se pueden revertir | \`.context/Confluence-corporativo/documentacion para QA/hilo-mail-alcance-qa.md\` · 21/05/2026 |
| Tipo Brownfield | \`.context/idea/business-model.md\` · encabezado |
| Aplicación Next.js y expectativa web móvil; compatibilidad no definida | \`.context/architecture/system-design.md\` y \`.context/architecture/prd.md\` |
| URLs locales y vigencia actual del pipeline | **No documentado/verificado**; no se infieren valores |

## Contradicciones detectadas

* **Entornos:** \`04-notas-tecnicas.md\` (30/10/2025) describe UAT (\`uat.cita.ai\`) y Producción (\`cita.ai\`) separados. La nota del 21/05/2026 dice que UAT dejó de usarse y solo quedaba el ambiente real. Se toma la fuente posterior como último estado conocido; la situación desde entonces no está verificada.
* **URL de Producción:** las notas de 2025 usan \`cita.ai\`; la nota del 21/05/2026 aclara que el dominio no estaba apuntado y que los usuarios usaban \`https://cita-ai.vercel.app/\`. Se toma esta última.
* **CI/despliegue:** las notas técnicas describen deploy automático desde \`main\` y ausencia de CI/tests, sin evidencia posterior que confirme su vigencia. Se registra como documentado, no como verificación actual.

## Preguntas abiertas

* ¿Sigue Producción siendo el único ambiente? ¿UAT volvió con datos sintéticos y aislados?
* ¿Cuál es el procedimiento aprobado para probar, restaurar datos y evitar correos a usuarios reales?
* ¿Se corrigió el almacenamiento de credenciales y quién administra los accesos? No compartir credenciales en claro.
* ¿Siguen el deploy automático desde \`main\` y la ausencia de CI/tests? ¿Dónde está el repositorio de la aplicación para inspeccionar workflows/configuración?
* ¿Qué navegadores, sistemas operativos, dispositivos y resoluciones están soportados?
* ¿Hay restricciones actuales de red, VPN o acceso a Supabase?

