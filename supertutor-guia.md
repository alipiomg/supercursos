# SuperTutor — Guía Completa de Uso
## Tutor Adaptativo Modular (Metodología Salgadoía Profesor)

---

## ¿Qué es SuperTutor?

SuperTutor es una skill de Claude que convierte cualquier sesión de estudio en una tutoría adaptativa de alto rendimiento. No es una enciclopedia: es un **arquitecto del aprendizaje**.

La diferencia clave frente a usar Claude de forma normal:
- **Sin SuperTutor**: "Explícame el tema X" → resumen genérico de calidad media
- **Con SuperTutor**: Diagnóstico de tu nivel → sesión calibrada → informe de progreso → instrucción de retoma

---

## Instalación

La skill vive en este repositorio: `.claude/skills/supertutor/SKILL.md`.

| Dónde quieres usarla | Qué hacer |
|---|---|
| **Claude Code en la web** con este repo | Nada: se carga sola en cada sesión del repo. |
| **Tu PC con Windows, en cualquier carpeta** (global) | Copia la carpeta `supertutor` a `C:\Users\alimu\.claude\skills\supertutor\` |
| **Otro repositorio** | Copia la carpeta a `.claude/skills/supertutor/` de ese repo. |

> No la instales en `~/.claude/skills/` de una sesión en la nube: ese contenedor se borra al reiniciarse y la skill desaparece.

Para invocarla, escribe en Claude Code:
```
/supertutor
```

O en lenguaje natural:
```
Activa el SuperTutor. Quiero estudiar [tema].
```

---

## Los 6 Diales Explicados

El tutor calibra 6 parámetros que controlan CÓMO te enseña, no QUÉ te enseña:

| Dial | ¿Qué controla? | Cuándo subirlo | Cuándo bajarlo |
|------|----------------|----------------|----------------|
| **Densidad** | Cuántos conceptos por turno | Si dominas el tema | Si te sientes saturado |
| **Velocidad** | Ritmo de avance en el temario | Si tienes poco tiempo | Si quieres profundizar |
| **Profundidad** | Nivel de detalle técnico | Si eres experto | Si eres principiante |
| **Modo** | Estilo de explicación | — | — |
| **Ejemplos** | Cantidad de ejemplos concretos | Si el tema es abstracto | Si el tema es muy práctico |
| **Desafío** | Dificultad de las preguntas | Si vas bien | Si estás cometiendo errores |

**Modos disponibles:**
- `Socrático`: El tutor pregunta, tú construyes el conocimiento
- `Expositivo`: Explicación directa y estructurada
- `Analógico`: Todo explicado con analogías del día a día
- `Práctico`: Casos reales, ejercicios, aplicación directa

---

## La Escalera de Calibración

```
NIVEL 4 — EXPERTO     → Debate, síntesis, conexiones nuevas
NIVEL 3 — COMPETENTE  → Casos borde, excepciones, preguntas de trampa
NIVEL 2 — APRENDIZ    → Casos prácticos, preguntas "¿qué pasaría si...?"
NIVEL 1 — INICIADO    → Relaciones entre conceptos, muchos ejemplos
NIVEL 0 — IGNOTO      → Mapa conceptual general, analogías básicas
```

El tutor te evalúa con 3-5 preguntas y te ubica automáticamente.

---

## Flujo de una Sesión Estándar

```
[INVESTIGACIÓN]  (solo si el tema es reciente, de nicho o cambia rápido)
   ↓
SuperTutor busca en la web y guarda estudios/<tema>/dossier.md
con hechos, conflictos entre fuentes y bloques temáticos
   ↓
[INICIO]
   ↓
SuperTutor pregunta: tema, objetivo, tiempo disponible y energía
   ↓
Evaluación inicial: 3-5 preguntas diagnósticas
   ↓
Diagnóstico: nivel detectado + configuración de diales
   ↓
[BUCLE DE APRENDIZAJE]
   ↓
Bloque 1 → comprobación → ajuste de diales si necesario
Bloque 2 → comprobación → ajuste de diales si necesario
...
   ↓
[CIERRE]
   ↓
Re-evaluación express (mismas preguntas del inicio)
   ↓
Informe de sesión: nivel inicial → nivel final, puntos de atención
   ↓
Instrucción de retoma para la próxima sesión
```

---

## Uso para Oposiciones con NotebookLM

Este es el flujo más potente para estudiar temarios cerrados:

### Paso 1 — Preparar NotebookLM
1. Ve a [notebooklm.google.com](https://notebooklm.google.com)
2. Crea un notebook nuevo para tu temario
3. Sube tus documentos: PDFs del temario, apuntes, legislación, BOE...
4. Genera el **Audio Overview** (podcast automático)
5. Escucha el podcast y toma notas esquemáticas del tema

### Paso 2 — Sesión con SuperTutor
1. Activa SuperTutor: `/supertutor`
2. Di: *"Estoy en modo oposición. El temario es [nombre]. No salgas del temario."*
3. Trae tus notas del podcast y las dudas que quedaron sin resolver
4. SuperTutor trabaja SOLO con tu material, no añade información externa
5. Al final de cada bloque, recibirás preguntas tipo examen de oposición

### Paso 3 — Ciclo de revisión
```
Escucha podcast (NotebookLM) → Estudia con SuperTutor → Vuelve a NotebookLM → Siguiente tema
```

### Instrucción de activación para oposiciones:
```
SuperTutor, modo oposición.
Cuerpo: [nombre del cuerpo]
Temario: [tema número X] — [nombre del tema]
Material: [describe brevemente lo que has traído]
Restricción: NO salgas del temario oficial. Solo usa mi material.
Formato de preguntas: [tipo test / desarrollo / ambos]
```

---

## Modos Especiales

### Modo Fatiga (más de 45 min o cansancio)
```
Escribe: "SuperTutor, estoy cansado. Modo fatiga."
```
El tutor reduce la densidad, alarga los ejemplos y propone descansos activos.

### Modo Examen (examen en menos de 48h)
```
Escribe: "SuperTutor, tengo examen mañana. Modo examen."
```
El tutor maximiza la densidad y convierte el 80% del tiempo en preguntas tipo examen.

### Modo Exploración (sin objetivo fijo)
```
Escribe: "SuperTutor, modo exploración. Quiero curiosear sobre [tema]."
```
Sin diagnóstico formal. El tutor sigue tu curiosidad con el método socrático.

---

## Cómo Retomar una Sesión

Al final de cada sesión, SuperTutor genera un mensaje de retoma. Guárdalo y pégalo al inicio de la siguiente sesión:

```
SuperTutor, retomamos.
Tema: [X]
Dossier: estudios/[tema]/dossier.md
Nivel: [N]
Diales: D:[X] V:[X] P:[X] M:[modo] E:[X] Ch:[X]
Empezamos por: [bloque pendiente]
```

Esto elimina el tiempo de diagnóstico y arranca directamente desde donde lo dejaste.

---

## Señales para Ajustar los Diales Manualmente

Puedes pedirle al tutor que ajuste los diales en cualquier momento:

| Si sientes... | Escribe... |
|---------------|------------|
| "Voy muy rápido, no me entera nada" | "Baja velocidad y densidad a 1" |
| "Esto es muy abstracto" | "Más ejemplos, modo analógico" |
| "Esto es muy fácil" | "Sube el desafío, acelera" |
| "Necesito que me preguntes más" | "Modo socrático" |
| "Prefiero que me expliques directamente" | "Modo expositivo" |
| "Estoy agotado" | "Modo fatiga" |

---

## Cómo pedírselo bien (no hace falta un prompt largo)

La skill ya contiene todas las instrucciones. Un prompt largo solo repetiría lo que ya dice y podría contradecirlo. Lo que sí marca la diferencia es darle **contexto sobre ti**:

```
/supertutor Quiero aprender [tema].
Para qué: [trabajo / examen / montar algo / curiosidad].
Lo que ya sé: [una línea].
Tiempo hoy: [minutos]. Energía: [alta / media / baja].
```

Para un tema nuevo o que cambia rápido (una herramienta de IA, una ley reciente), añade:
```
Investiga primero y guarda el dossier antes de empezar.
```

**El modelo** se elige en Claude Code con `/model`, no dentro de la skill. Usa el más capaz que tengas (por ejemplo Fable) para la fase de investigación, que es la más exigente.

### Ejemplo real: Grok Bot
En `estudios/grok-bot/dossier.md` tienes el dossier ya hecho. Para estudiarlo:
```
/supertutor Quiero aprender Grok Bot. Usa estudios/grok-bot/dossier.md.
Para qué: decidir si me sirve para automatizar tareas de mi negocio.
Lo que ya sé: he usado Grok como chat, nada más.
Tiempo hoy: 30 minutos. Energía: media.
```

---

## Preguntas Frecuentes

**¿Puedo usar SuperTutor sin NotebookLM?**
Sí. NotebookLM es opcional y solo necesario para temarios cerrados con documentos propios. Para cualquier otro tema, SuperTutor funciona de forma autónoma.

**¿Qué pasa si me salto la evaluación inicial?**
El tutor la hace igualmente. Nunca arranca sin diagnóstico excepto en Modo Exploración.

**¿Cuánto dura una sesión ideal?**
Entre 25 y 45 minutos por tema. Más de 45 minutos activa automáticamente el Modo Fatiga.

**¿Puedo ajustar los diales yo mismo?**
Sí, en cualquier momento. El tutor también los ajusta automáticamente según tus respuestas.

**¿Funciona para cualquier tema?**
Sí. La metodología es agnóstica al contenido: funciona para oposiciones, idiomas, programación, historia, medicina, o cualquier materia.

---

## Resumen en Una Página

```
SUPERTUTOR — CHULETA RÁPIDA

INVESTIGA:  tema nuevo → dossier en estudios/<tema>/dossier.md
INICIO:     /supertutor  →  describe tema + objetivo + energía
EVALÚA:     3-5 preguntas → ubica tu nivel (0-4)
CALIBRA:    6 diales → D V P M E Ch
APRENDE:    Bucles por bloque + ajuste en tiempo real
CIERRA:     Re-evaluación + informe + mensaje de retoma

MODOS:      Fatiga | Examen | Exploración | Oposición
RETOMA:     Pega el mensaje de retoma al inicio de la siguiente sesión

REGLA DE ORO: Cuanto más activo seas (pregunta, conecta, equivócate),
              mejor aprende el tutor a calibrarte y mejor aprendes tú.
```
