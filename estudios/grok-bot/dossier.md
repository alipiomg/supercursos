# Dossier: Grok Bot (xAI)

**Fecha de investigación:** 7 de noviembre de 2026
**Método:** búsquedas web (no se pudieron abrir las páginas oficiales directamente porque la red de la sesión estaba limitada). Todo lo que viene de una sola fuente de terceros va marcado como *sin confirmar*.

---

## Qué es en una frase

Grok Bot es un **agente de IA de xAI que trabaja por ti en un ordenador en la nube**: inicia sesión en tus aplicaciones, completa tareas aunque cierres el portátil y se detiene a pedirte permiso antes de hacer algo delicado.

> **Ojo con el nombre:** "GrokBot" (todo junto) también es el nombre del **rastreador web** de xAI que recoge páginas para entrenar los modelos Grok. Este dossier trata del agente, no del rastreador.

---

## Mapa conceptual

```
                   ┌──────────────────────┐
                   │   TÚ (desktop/móvil) │  chat · revisión · aprobaciones
                   └──────────┬───────────┘
                              │
                   ┌──────────▼───────────┐
                   │        BOTS          │  cada uno con un trabajo principal
                   │ (pueden formar equipo)│
                   └──────────┬───────────┘
                              │ trabajan en
                   ┌──────────▼───────────┐
                   │ ORDENADOR EN LA NUBE │  persistente, con tus sesiones iniciadas
                   └───┬──────────────┬───┘
                       │              │
          ┌────────────▼──┐      ┌────▼─────────────────┐
          │ USO DEL       │      │ CONECTORES / PLUGINS │  (más fiables)
          │ ORDENADOR     │      │ / SERVIDORES MCP     │
          │ (navegador)   │      └──────────────────────┘
          └───────────────┘
   Lo que aprende se guarda como ──► SKILL ──► se programa como ──► RUTINA
   Todo lo delicado pasa por ──► APROBACIONES
```

| Concepto | Qué es | Relación |
|---|---|---|
| **Bot** | Un "compañero" de IA con nombre y un trabajo concreto | Trabaja en el ordenador en la nube |
| **Ordenador en la nube** | Máquina persistente donde el bot opera apps y navegador | Mantiene tus sesiones iniciadas |
| **Skill** | Receta guardada: pasos, reglas de decisión, resultado esperado y límites de seguridad | Sale de una tarea bien hecha o de una demostración |
| **Rutina** | Ejecución automática de una skill o tarea | Por horario o por evento (Slack, GitHub, Linear, Sentry, PagerDuty) |
| **Conectores / plugins / MCP** | Acceso estructurado a herramientas | xAI recomienda usarlos antes que el "uso del ordenador" |
| **Aprobaciones** | Puntos donde el bot para y te pregunta | Por defecto: mensajes externos, dinero, borrados, cambios en producción |
| **Acceso al ordenador local** | Control aparte para tocar tu propio equipo | Aprobación por cada comando por defecto |
| **Cursor Cloud Agent** | Agente de programación de Cursor | El bot le pasa el trabajo de código |

---

## Hechos verificados

**Lanzamiento y plataformas**
- Beta lanzada el **11 de agosto de 2026**, desarrollada con **Cursor** (en la prensa del lanzamiento la empresa aparece como "SpaceXAI").
- Apps para **Windows, macOS, Linux e iOS**; también Android según la documentación de Cursor. Las apps son sobre todo un cliente: el trabajo real ocurre en la nube.

**Cómo funciona**
- Creas un Bot con **un trabajo principal**, le das acceso a tus apps y le encargas tareas.
- Cuando una tarea sale bien, la guardas como **skill**. También puedes enseñarle una skill mostrándole cómo se hace; esa skill queda como borrador hasta que la revisas.
- Una **rutina** ejecuta una skill de forma programada o cuando ocurre un evento, también con el portátil cerrado. *Sin confirmar:* máximo de 50 rutinas por bot.
- Para código, el Bot puede delegar en un **Cursor Cloud Agent**, que trabaja en un entorno aparte.

**Aprobaciones y seguridad (según la documentación)**
- Por defecto se detiene antes de: enviar mensajes externos, operaciones financieras, borrar datos y cambios en producción.
- Puedes añadir reglas propias en la descripción del bot, en una skill o en una rutina; los administradores también desde el panel de Cursor.
- El contenido externo se marca como "no fiable" al pasárselo al modelo, y hay capas de Auto-review, política de red y aislamiento por usuario.

**Uso recomendado por la documentación oficial**
1. Conecta las apps que ya usas.
2. Convierte cada tarea repetitiva en su propio Bot.
3. Agrupa Bots en un equipo para un objetivo más grande.

Primera tarea sugerida: adjuntar un documento y pedir un resumen sin modificar el original. Roles de ejemplo: ventas, búsqueda de talento, publicidad, gastos, rendimiento de producto, reproducción de bugs, salud de cuentas, "jefe de gabinete".

---

## Conflictos y dudas entre fuentes

| Tema | Lo que se contradice |
|---|---|
| **¿Un ordenador por bot o compartido?** | Webs de terceros dicen que cada bot tiene su máquina. La documentación de Cursor y un tutorial dicen que **todos los bots de tu cuenta comparten un ordenador**, así que ven las sesiones y archivos de los demás. **Asume que es compartido:** no uses bots distintos como barrera de seguridad. |
| **Precio y planes** | Desde el **12 de octubre de 2026**, los clientes nuevos lo obtienen con *The X Subscription*: Premium 30 $/mes, Super 100 $, Ultra 200 $. Las vías anteriores (Cursor Pro 20 $, SuperGrok 30 $, Cursor Pro+ 60 $, SuperGrok Plus 100 $, Cursor Ultra 200 $, SuperGrok Heavy ~300 $) siguen para quien ya estaba suscrito. Las fuentes no coinciden: **revisa la página oficial antes de pagar.** |
| **Límites de uso** | Es lo peor documentado. Hay una **bolsa semanal compartida** con Grok y Cursor, publicada solo como "múltiplos" entre planes. Combinar suscripciones **no suma** límites. |
| **Compras en Amazon** | *Sin confirmar (una sola fuente):* Amazon bloquea pedidos hechos por Grok Bot desde mediados de octubre de 2026. |

---

## Riesgos que conviene entender

- **Inyección de instrucciones (prompt injection):** una web o un correo puede esconder órdenes que el agente acaba obedeciendo. Adversa AI publicó en agosto de 2026 una técnica con instrucciones cifradas que Grok descifra y ejecuta.
- **Demasiada autonomía:** en mayo de 2026, un usuario de X engañó a Grok con un mensaje en código Morse para mover unos 150 000 $ de una cartera cripto vinculada. Fue con Grok, no con Grok Bot, pero muestra el riesgo de dar permisos de dinero a un agente.
- **Entorno compartido:** si un bot lee instrucciones maliciosas, los demás bots de la misma cuenta pueden verse afectados.
- **No es buena opción para:** tareas en tiempo real, revisión de código profunda o trabajo que necesite SSH o conexión directa a bases de datos (*según una guía de terceros*).

**Regla práctica:** no conectes cuentas de dinero ni des permisos de borrado o envío sin aprobación. Empieza con tareas de solo lectura.

---

## Ampliación: caso del alumno — Hermes en un VPS + redes sociales (7 nov 2026)

**Objetivo del alumno:** instalar Hermes en un VPS, dejarlo mantenido y actualizado con Grok Bot, y publicar en redes de forma automática con imágenes y vídeos generados por IA.

### Hermes Agent (Nous Research)
- Agente de IA **de código abierto que tú alojas** (*self-hosted*). Es la pieza que se instala en tu VPS.
- Se instala con un comando oficial de Nous Research y se configura con `hermes setup`, donde eliges el proveedor del modelo (uno en la nube o uno local con Ollama o vLLM; el local necesita un VPS con GPU).
- Para que siga funcionando tras un reinicio se ejecuta como servicio (systemd o el comando `gateway install`). Varias guías recomiendan **un usuario propio, nunca root**.
- Requisitos: 1 vCPU y entre 1 y 2 GB de RAM según la fuente. Como el modelo corre fuera, basta un VPS pequeño (~5 $/mes).
- Alternativa: Docker, con la imagen `nousresearch/hermes-agent:latest`. No funciona en Windows nativo.
- *Conflicto:* las guías no coinciden en la URL de instalación (hay una antigua, hermes-agent.org, que da error). Usa la de la documentación oficial.

### Grok Bot + VPS: son dos máquinas distintas
```
 [Ordenador en la nube de Grok Bot]  ──SSH──►  [TU VPS con Hermes]
   gestionado por xAI/Cursor,                  tuyo, con acceso root,
   compartido por todos tus bots               aquí vive Hermes
```
- El ordenador de Grok Bot tiene navegador, archivos y **terminal**, pero **no es un VPS**: no es tuyo, no lo puedes alojar tú y lo comparten todos tus bots.
- Grok Bot sale a internet desde **IPs fijas compartidas**, así que puedes limitar en el cortafuegos del VPS desde qué IPs se puede entrar por SSH.
- Para servicios privados (como SSH sin exponerlo a internet), la documentación oficial describe usar **cloudflared + Cloudflare Access**.
- Actualizar o reiniciar el VPS cuenta como **cambio en producción**, así que por defecto el bot pide aprobación.
- *Conflicto:* una guía de terceros dice que Grok Bot "no sirve para tareas con SSH", pero la documentación oficial sí describe terminal y conexión a redes privadas. Lo prudente es probarlo con tareas pequeñas.
- *Sin confirmar:* usuarios han entrado por SSH **al propio ordenador de Grok Bot** usando Tailscale. Es un truco no oficial, y no es lo que necesitas.
- **Riesgo clave:** la clave SSH del VPS quedará en un ordenador que comparten todos tus bots. Usa una clave exclusiva, un usuario sin root y comandos limitados.

### Redes sociales, imágenes y vídeo
- Grok Bot **no publica en redes de serie**: necesita un **conector o plugin MCP** de terceros (Postiz, Blotato, PublishQ o WoopSocial; varios cubren 9 plataformas).
- **Grok Imagine** genera imágenes y vídeo. Lo publicas a través del conector.
- Las rutinas pueden preparar y programar publicaciones mientras estás desconectado. Publicar es un "mensaje externo", así que por defecto **pide aprobación**. Los propios proveedores recomiendan mantenerla.
- *Aviso:* casi todo esto sale de páginas comerciales de los propios conectores.

### Pregunta de diseño abierta (para el bloque de síntesis)
Hermes también es un agente que puede programar tareas. ¿Quién debe hacer cada trabajo: Hermes desde dentro del VPS o Grok Bot desde fuera? Tener dos agentes significa dos cosas que vigilar.

---

## Glosario

- **Agente de IA:** IA que no solo responde, sino que ejecuta acciones.
- **Uso del ordenador (computer use):** el agente mueve el ratón, teclea y navega como una persona.
- **MCP (Model Context Protocol):** estándar para conectar herramientas a modelos de IA.
- **Prompt injection:** instrucciones ocultas en contenido externo que secuestran al agente.
- **Rutina:** tarea programada o activada por un evento.
- **Skill:** procedimiento guardado y reutilizable.
- **VPS:** servidor privado virtual que alquilas y controlas tú.
- **SSH:** forma segura de conectarse a la terminal de un servidor remoto.
- **Self-hosted:** software que instalas y mantienes en tu propia máquina.
- **systemd:** gestor de servicios de Linux que arranca programas solos al encender el servidor.

---

## Bloques temáticos propuestos para la tutoría

1. **Qué es y qué no es** — agente vs. chatbot, y la confusión con el rastreador GrokBot.
2. **La arquitectura** — cliente, Bots, ordenador en la nube y conectores.
3. **Skills y rutinas** — de tarea suelta a procedimiento automático.
4. **Aprobaciones y seguridad** — qué para el bot, prompt injection, ordenador compartido.
5. **Precios y acceso** — qué plan, la bolsa semanal, y por qué hay que verificarlo.
6. **Diseñar tu primer Bot** — elegir un caso de uso real, definir sus límites y su primera skill.

---

## Fuentes

Oficiales:
- [Get started with Grok Bot — Cursor Docs](https://cursor.com/docs/grok-bot/get-started)
- [Work with Grok Bot — Cursor Docs](https://cursor.com/docs/grok-bot/work)
- [Skills and routines — xAI Docs](https://docs.x.ai/grok-bot/skills-routines-and-automations)
- [Use cases — xAI Docs](https://docs.x.ai/grok-bot/use-cases)
- [Grok Bot for teams and enterprises — xAI Docs](https://docs.x.ai/grok-bot/teams-and-enterprises)
- [Grok Bot: more plans — xAI News](https://x.ai/news/grok-bot-more-plans)

Guías y análisis:
- [Grok Bot Tutorial: Skills, Routines, and Approvals — DataCamp](https://www.datacamp.com/tutorial/grok-bot-tutorial)
- [A deep dive into Grok Bot — Flavio Copes](https://flaviocopes.com/grok-bot/)
- [A Guide to Grok Bot — Composio](https://composio.dev/content/guide-to-frok-bot)
- [Grok Bot Architecture Explained — codepick.dev](https://codepick.dev/en/guides/grok-bot-architecture/)
- [Grok Bot Use Cases: Eight Roles — Learn Cursor](https://www.learncursor.dev/learn/cursor-agents/grok-bot-use-cases)
- [SpaceXAI Grok Bot launch — GIGAZINE](https://gigazine.net/gsc_news/en/20260812-spacexai-grok-bot/)

Precios:
- [Grok Bot Pricing: Every Route Compared — cellcog](https://cellcog.ai/blog/grok-bot-pricing/)
- [The Grok Subscription Maze — JDB Consulting](https://jdb.net/grok-subscription-comparison/)
- [Grok Bot Pricing and Limits — ToolColumn](https://www.toolcolumn.com/learn/grok-bot-pricing-by-plan)

Caso Hermes + VPS + redes:
- [Grok Bot — xAI Docs](https://docs.x.ai/grok-bot/overview)
- [Connect to private networks — xAI Docs](https://docs.x.ai/grok-bot/private-networks)
- [How to Install Hermes Agent on a VPS — Contabo](https://contabo.com/blog/how-to-install-hermes-agent-on-a-vps-2026-step-by-step-guide/)
- [Self-Host Hermes Agent on a VPS: v0.20 Guide — Virtua](https://www.virtua.cloud/learn/en/tutorials/self-host-hermes-agent-vps)
- [Hermes Agent hosting: a $5 VPS is enough — SSD Nodes](https://www.ssdnodes.com/learn/self-host-hermes-agent-vps)
- [Grok Bot Workspaces and Specs — flocker.md](https://flocker.md/blog/grok-bot-roles-workspace-and-specs/)
- [SSH al ordenador de Grok Bot con Tailscale — post en X](https://x.com/old_pgmrs_will/status/2094217821211464069)
- [Schedule Social Media Posts with Grok Bot — Postiz](https://postiz.com/grok-bot)
- [Grok Bot Social Media MCP Setup — Blotato](https://www.blotato.com/ai-agent/grok-bot)
- [Grok AI Agent for Social Media: 5 Real Jobs Tested — ContentStudio](https://contentstudio.io/blog/can-grok-run-social-media)

Seguridad:
- [Grok Bot phishing email catch exposes AI agent risks — Cybernews](https://cybernews.com/ai-news/grok-bot-phishing-spacexai-invite-scam/)
- [The Grok Morse Code Heist — NeuralTrust](https://neuraltrust.ai/blog/grok-morse-code)
- [Is It Safe to Give Grok Bot Access to Your Company Systems? — RedactSure](https://redactsure.com/research/is-it-safe-to-give-grok-bot-access-to-your-company-systems/)
- [Encrypted Prompt-Injection Attack — Modernizing Tech](https://modernizingtech.com/news/cybersecurity/encrypted-prompt-injection-attack-raises-data-privacy-concerns-for-xais-grok/)
- [GrokBot crawler — Promptwatch](https://promptwatch.com/bots/grokbot)
