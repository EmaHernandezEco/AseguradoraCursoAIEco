# Estrategia de Datos de Prueba: Cita.ai

> Proyecto Brownfield. Actualizado el 15/10/2026 con documentos del proyecto y la confirmación de que QA no tiene acceso directo a las bases de prueba.

## 1. Fuentes de Datos

* La nota técnica del 30/10/2025 dice que UAT se refrescaba copiando Producción.
* Según esa nota, solo se reemplazaban nombres y correos de la tabla \`clients\`. Los nombres y correos de \`professionals\` seguían siendo reales.
* La nota operativa del 21/05/2026 dice que UAT dejó de usarse y que se probaba directamente sobre Producción. No confirma si UAT sigue operativo hoy.
* No hay script de seed documentado. En Producción se creaban cuentas propias con correos descartables (por ejemplo, Mailinator); esas cuentas no convierten el entorno en uno de prueba seguro.
* QA confirma que no tiene acceso directo a la base de datos de los entornos de prueba.

## 2. Gestión de Usuarios de Prueba

| Rol | Usuario (Email/ID) | Contraseña (Referencia a Vault/Env) | Propósito |
| :--- | :--- | :--- | :--- |
| Profesional de prueba | No hay usuario fijo documentado | No documentada; no leer ni copiar el archivo de texto mencionado en la nota técnica | La nota operativa instruía crear una cuenta propia; hoy Producción es el único ambiente confirmado en uso |
| Cliente final de prueba | No hay usuario fijo documentado; se indicaban correos descartables | No aplica/documentada | Recibir y revisar correos; no usar datos de personas reales |
| Cuenta de Fernando | **No usar** | No aplica | Contiene profesionales y clientes reales |

No se documentan roles de prueba separados, cuentas fijas administradas ni una ubicación segura confirmada para credenciales. No registrar datos ni enviar correos en Producción como parte de pruebas sin un procedimiento aprobado.

## 3. Generación de Datos Sintéticos

* **Herramientas:** no hay generador, seed o factory documentados.
* **Estrategia actual:** no documentada. La copia de Producción y el uso de correos descartables no equivalen a un conjunto de datos sintéticos aislado.
* **Propuesta (hipótesis):** solicitar un entorno aislado y cargar un seed con profesionales, clientes, turnos y disponibilidad ficticios; no crear dicho seed hasta confirmar entorno, acceso y método de reset.

## 4. Privacidad y Seguridad (PII)

* **Política observada:** UAT se refrescaba desde Producción; por tanto, contenía datos copiados de personas reales.
* **Alcance real de la anonimización:** solo se reemplazaban nombres y emails de \`clients\`. La tabla \`professionals\` conservaba nombres y emails reales para mantener los slugs. La nota técnica confirma explícitamente que UAT tenía emails reales de profesionales.
* **Riesgo de PII:** anonimización parcial e insuficiente en UAT histórico. La nota operativa posterior afirma que las pruebas pasaron a Producción, donde los datos y correos son reales. El estado actual de UAT y cualquier anonimización posterior no están confirmados.
* No se inspeccionaron archivos de credenciales ni se incluyó ningún secreto.

## 5. Limpieza y Reset (Teardown)

No hay procedimiento propio de reset, restauración o seed documentado. La nota del 21/05/2026 dice que los cambios en Producción no podían revertirse y que no había copia propia ni script para reconstruir la base. No ejecutar pruebas que creen o modifiquen datos hasta acordar un entorno aislado y un reset autorizado.

## Fuentes

| Dato / afirmación | De dónde sale |
| :--- | :--- |
| Copia de Producción a UAT; anonimización limitada a \`clients\`; emails reales en \`professionals\`; sin seed; credenciales en TXT | \`.context/Confluence-corporativo/04-notas-tecnicas.md\` · “los datos de UAT”, edición 30/10/2025 |
| UAT sin uso, pruebas en Producción, datos/correos reales y falta de restauración | \`.context/Confluence-corporativo/documentacion para QA/nota-ambientes-y-accesos.md\` · 21/05/2026 |
| QA no tiene acceso directo a bases de prueba | Confirmación del usuario en esta conversación |
| UAT con datos generados para ese fin y personas ficticias | \`.context/Confluence-corporativo/03-especificacion-funcional-v0.3.md\` · §11; especificación v0.3 |
| Seed sintético, entorno aislado y reset autorizado | **Hipótesis/propuesta**; no hay implementación o aprobación documentada |

## Contradicciones detectadas

* **Datos de UAT:** la especificación funcional v0.3 afirma que UAT usa datos generados y personas ficticias. Las notas técnicas del 30/10/2025 dicen que UAT se refrescaba con una copia de Producción y que solo se anonimizaban nombres y emails de \`clients\`, mientras \`professionals\` mantenía PII real. Se priorizan las notas técnicas, que describen el proceso efectivo y su alcance, frente a la afirmación general de la especificación. La nota operativa del 21/05/2026 añade que UAT dejó de usarse y las pruebas ocurrían en Producción.
* **Disponibilidad de UAT:** las notas técnicas describen UAT activo en 2025; la nota posterior informa que llevaba meses sin uso y no se sabía si seguía levantado. Se toma como último estado conocido que no era un entorno operativo confiable; estado actual sin verificar.

## Preguntas abiertas

* ¿Se recuperó UAT u otro entorno aislado? ¿Se alimenta exclusivamente con datos sintéticos?
* ¿Quién puede otorgar a QA acceso autorizado y de mínimo privilegio a una base segura? La respuesta actual es que QA no tiene acceso directo.
* ¿Hay usuarios fijos de prueba? ¿Qué roles deben cubrir y dónde se administran sus credenciales sin exponerlas?
* ¿Cuál es el proceso aprobado para crear, limpiar y restablecer datos tras una prueba?
* ¿Se corrigió la anonimización de \`professionals\` y se regeneran slugs ficticios?
* ¿Qué controles evitan que las pruebas envíen correos o creen turnos reales?

