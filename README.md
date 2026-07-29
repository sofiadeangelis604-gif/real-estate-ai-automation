# Ecosistema de Automatización IA Autónomo

**Caso de uso:** Automatización de la gestión y clasificación de leads inmobiliarios mediante IA.

Sistema construido en n8n que resuelve de extremo a extremo el proceso de captación de leads de una inmobiliaria: captura el lead desde un formulario, lo registra en Airtable, lo procesa con IA (clasifica prioridad y genera resumen), solicita la aprobación de un asesor humano antes de contactar al cliente (Human-in-the-loop) y envía el correo final, todo sin intervención manual en el procesamiento.

---

## Enlaces de la entrega

- 📊 **Dashboard de Control (KPIs y tasa de errores):** https://airtable.com/appegNVHGWIbIGNmc/shrGG98FAhGPsZjdH
- 🗄️ **Base de datos Airtable (modo lectura):** https://airtable.com/appegNVHGWIbIGNmc/shrnitcl1WYNH5885
- 🎥 **Video demostración (máx. 3 min):** https://drive.google.com/file/d/1fcZVI0-iA8mKAIAq_5voG1MrF2SPYOrq/view?usp=sharing

---

## Tecnologías utilizadas

| Componente | Tecnología | Función |
|---|---|---|
| Orquestador | n8n | Motor de flujo que conecta todos los nodos y ejecuta la lógica |
| Base de datos | Airtable (tabla Leads) | Memoria y registro del sistema; guarda datos y estados del lead |
| Procesamiento IA | OpenAI (gpt-5-mini) vía AI Agent | Clasifica prioridad, genera Resumen IA y Acción IA |
| Canal de salida | Gmail | Notificación de aprobación al asesor y correo automático al cliente |

---

## Flujo del sistema

1. El usuario completa un formulario.
2. Se guarda el lead en Airtable (estado inicial: *Pendiente*).
3. OpenAI clasifica el lead: asigna prioridad (Alta / Media / Baja) y genera un resumen y una acción sugerida.
4. Se solicita la aprobación del asesor (Human-in-the-loop) por Gmail.
5. Si el asesor aprueba, se envía un correo automático al cliente y el estado pasa a *Contactado*. Si rechaza, el estado pasa a *Rechazado*.

---

## Estados del lead

| Estado | Cuándo se asigna |
|---|---|
| Pendiente | Al crear el registro, antes de procesar |
| Procesado IA | Tras la clasificación exitosa por la IA |
| Esperando aprobación | Mientras el asesor decide (HITL) |
| Contactado | El asesor aprobó y se envió el correo al cliente |
| Rechazado | El asesor no aprobó el lead |
| Error IA | La API de IA falló; se registra el error sin detener el flujo |

---

## Archivos del repositorio

- 📄 `Arquitectura_Ecosistema_IA.pdf` — Diagrama de arquitectura del sistema.
- 📄 `Matriz_de_Costos.pdf` — Justificación del modelo de IA elegido y ahorro estimado.
- 📄 `Datos_Seguridad_y_Resiliencia.pdf` — Esquemas JSON de datos + seguridad y resiliencia.
- ⚙️ `Automatizacion_Inmobiliaria.json` — Flujo de n8n exportado.
- 📷 `Screenshots.pdf` — Capturas del flujo y del dashboard.

---

*Autora: Sofía De Angelis*
