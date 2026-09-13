# Contexto para arrancar en una máquina nueva

> Esto es lo primero que lee cualquier agente (Claude Code u otro) al abrir el
> workspace de Studio32 en una máquina donde no ha trabajado antes. Si eres un agente
> y acabas de leer esto: no hace falta que releas nada más para "entender el panorama"
> — para trabajar de verdad en un repo concreto, ve a su `.ai/STATE.md`, que es donde
> vive el detalle técnico actualizado.

**Última actualización: 15/08/2026, al preparar el traspaso de portátil a sobremesa.**

---

## Quién eres tú (agente) y con quién hablas

Trabajas con **Pancho**, socio de Studio32. Su nombre real es Francisco; "Pancho" es
como le llama el equipo, y así se referencia en el código (`owner_member_id: "pancho"`
en el Hub) — pero su alias de correo real es **`francisco@studio32.es`**, no `pancho@`
(ese alias no existe). El cruce entre los dos vive en
`repos/studio32/studio32-hub/src/remitentes.json`.

Los otros dos socios son **Juanma** (`juanma@studio32.es`) y **Gonzalo**
(`gonzalo@studio32.es`). Los tres son el equipo entero.

**Cómo trabaja Pancho, para que no tengas que redescubrirlo:**

- Tiende a **añadir features antes de terminar** las que ya tiene en marcha. Cada
  cosa nueva "se siente necesaria para el ecosistema", pero el negocio tiene un
  cliente pagando: cero. Si te propone algo nuevo y no hay ningún cliente vivo en
  producción, pregúntale si de verdad quiere abrir eso ahora o prefiere anotarlo para
  después — no se lo impidas, pero no lo des por sentado tampoco.
- **No sabe explicarse bien con el equipo** — es la razón por la que existe la
  carpeta `reportes/` (ver más abajo): un compañero no se enteró de que algo ya
  estaba hecho, y de ahí salió el conflicto que motivó escribir avances en lenguaje
  llano.
- El tono de cualquier copy o material de cara al equipo o a clientes: **cercano y
  de tú, con palabras normales y completas — nada de slang ni coloquialismos**
  ("reu", "tranqui", "chuleta" le suenan mal, dice "yo no hablo así"). Tampoco tono
  corporativo-frío. El punto medio natural.
- Cuando mejora algo técnico por dentro del agente (un guard, una regla, un matiz),
  quiere que esa mejora se traduzca también a **un beneficio de una frase para el
  cliente**, porque es "su arma de distinción" y no quiere que se quede enterrada en
  un commit. La lista técnica es munición interna, nunca se le enseña al cliente tal
  cual — al cliente se le habla de principios y resultados, no de mecanismos.

---

## Qué es Studio32 y hacia dónde va

Estudio de sistemas digitales para negocios físicos/locales (clínicas, restaurantes,
servicios). No vende páginas web sueltas: vende presencia + automatización +
asistente de IA entrenado, como sistema.

**El producto real hoy es `studio32-agent`**: un asistente que se habla por WhatsApp,
atiende con criterio del oficio (no es un chatbot genérico — sabe de verdad de la
clínica, mira la agenda real, no inventa). Se descartó volver a hacer bots a medida
por cliente: la plataforma ya contiene eso como caso particular (un tenant es
literalmente config).

**Regla de rumbo, vigente:** congelación de scope — cero features nuevas en
`studio32-agent` hasta que el primer cliente esté vivo en producción cobrando.
Cualquier avance en Prospección (captación) se permite en paralelo porque es lo que
trae a ese primer cliente, no porque la congelación se haya levantado.

**No hay ningún cliente. Cero.** GH Dent (clínica dental, Guadalajara) fue el piloto
hasta el 09/09/2026: se le envió el presupuesto y **nunca respondió**. No lo trates
como cliente activo ni persigas ese hilo. Su tenant sigue en disco pero fuera del
control de versiones, y sus dos bloqueadores de siempre —verificar el número en Meta y
conectar su Google Calendar— dejaron de ser bloqueadores de *ese* cliente; siguen
siéndolo de cualquier go-live, que es distinto.

**El piloto hoy es `clinica-cobalto`**, y es un tenant ficticio a propósito: clínica
dental sintética (teléfonos `+3460000001x`, sin credenciales reales) que sirve para
ensayar el flujo entero —WhatsApp, panel, agenda— sin tocar datos de nadie. Todo el
desarrollo hecho para GH Dent se sigue usando aquí: el arquetipo dental es el mismo.
Se siembra con `supabase/seed-demo-cobalto.sql` en `studio32-agent` (idempotente, con
la agenda relativa a hoy para que no caduque), y **reejecutarlo antes de una demo**
borra el rastro de los ensayos y recoloca la agenda en el día. Es también el tenant
contra el que corren las pruebas de criterio (`npm run eval`).

Detalle completo y siempre al día en `reportes/ESTADO.md`, en este mismo repo.

**Competencia a tener en cuenta, sin nombrarla en ningún material:** Meta lanzó un
agente nativo de WhatsApp gratis (más de 1M de negocios ya lo usan). Decisión tomada:
no cambiar de rumbo ni posicionar "nosotros vs Meta" — Studio32 hace más y la mayoría
de dueños de pyme ni sabe que ese agente de Meta existe. Lo que Meta no hace es
conocer precios/agenda real del negocio ni tener criterio del oficio; las demos deben
enseñar eso, no "contesta 24/7", que ya es comodidad de cualquiera.

---

## Mapa del workspace

> ⚠️ **La organización de carpetas NO es la misma en cada máquina, y los nombres de
> las carpetas tampoco.** En el portátil los repos cuelgan de `repos/studio32/`; en el
> sobremesa están repartidos en `repos/interno/`, `repos/web/`, `repos/productos/`,
> `repos/plataforma/` y `repos/clientes/`, y alguna carpeta se llama distinto del repo
> que contiene. Por eso **aquí los repos se nombran por su nombre de repo, nunca por su
> ruta**. Si necesitas localizar uno, búscalo por nombre o mira su `git remote -v`; no
> des por buena ninguna ruta que leas en documentación vieja.

La raíz del workspace (la carpeta `Studio32/` que abres con Claude Code) **no es un
repositorio**: lo que se deje suelto ahí no viaja entre máquinas. Solo viaja lo que
esté dentro de un repo git.

| Superficie viva | Repo | Qué es |
|---|---|---|
| `studio32.es` | `studio32-web` | La web pública, con el agente en vivo |
| `hub.studio32.es` | `studio32-hub` | Workspace interno del equipo (tareas, calendario, **prospección**) |
| `dashboard.studio32.es` | `studio32-panel` | Panel que ve cada cliente (citas, conversaciones) |
| backend del agente | `studio32-agent` | El motor del asistente de WhatsApp |
| bot de Telegram | `studio32-hub-agent` | Notificaciones del Hub, en Railway |

`studio32-hub-live` y `studio32-dashboard-deploy` son **builds generados**: no se
editan a mano, se despliegan desde sus repos gemelos.

El meta-repo `Studio32` (`github.com/tsmluky/Studio32`) es este mismo, el que contiene
`reportes/` y `notes/` — ojo, que su carpeta local puede llamarse distinto según la
máquina. Es donde vive el contexto de negocio compartido, y **es público en GitHub**:
nunca escribir aquí datos de contacto de prospectos reales, credenciales, tokens ni
IDs sensibles.

---

## Cómo está el trabajo activo ahora mismo

**Fuente de verdad siempre actualizada, léela en este orden** (rutas relativas a la
raíz de cada repo, porque la ruta del repo en disco cambia según la máquina):

1. `reportes/ESTADO.md`, en el repo **Studio32** (este mismo) — la foto de negocio:
   qué está hecho, qué falta, qué bloquea. Escrito para personas, no técnico.
2. `.ai/STATE.md`, en el repo **studio32-hub** — el detalle técnico de la prospección
   y del Hub: qué está probado, qué convenciones no se rompen, qué queda a medias.
3. `.ai/DECISIONS.md`, en el repo **studio32-hub** — el porqué de cada decisión no
   obvia, si necesitas entender por qué algo se hizo así y no de otra forma.

En síntesis, a fecha de este traspaso:

- **La prospección funciona de punta a punta**: se pide una campaña desde el Hub, se
  genera en local con `/prospectar` (corre con la suscripción de Claude, por eso es
  local y no un worker en la nube), sube los leads con su evidencia, se aprueba en el
  Hub, y el envío sale por SMTP de Hostinger — con copia verificada en la carpeta
  Enviados del buzón real desde el 12/08.
- **El Hub tuvo una renovación visual completa el 13/08** y se limpiaron
  inconsistencias de la cola de revisión (contador de pendientes desalineado con la
  lista, campañas de prueba ya agotadas ensuciando la vista). Ver la entrada del 13/08
  en `reportes/ESTADO.md` para el resumen en llano, o `DECISIONS.md` del hub para el
  porqué técnico.
- **Hay 40 correos esperando aprobación** en el Hub, de campañas de dental, fisio y
  estética en una decena de ciudades. El 12/09 se corrigieron 29 que diagnosticaban
  bien y no decían con qué se resolvía el problema; la plantilla ya lo exige. Ver
  `reportes/2026-09-12.md`.
- **Los dos bloqueadores de cualquier go-live siguen abiertos**, y ya no son de un
  cliente concreto sino del producto: el número **`+34 694 29 31 66` sigue en
  "Pendiente" en Meta** desde julio (nunca completó el OTP, hace falta la SIM a mano)
  y **Google Calendar no está montado de verdad** — no existe la cuenta técnica, no
  hay `GOOGLE_CREDENTIALS_JSON` en Railway ni `calendar.calendar_id`. Ninguno de los
  dos es trabajo de código, y hasta que estén, *no se puede entregar* lo que se
  venda. Es la regla que manda en `notes/CAMINO.md`.

**Antes de trabajar en el Hub, comprueba en qué rama estás.** En `studio32-hub` la
rama buena es **`main`, siempre**. Hay dos ramas remotas viejas que despistan porque
sus nombres suenan a trabajo activo:

- `feat/prospeccion-email`
- `merge/prospeccion-unificada`

**Las dos están enteramente fusionadas en `main`** (comprobado el 15/08/2026: cero
commits exclusivos en cualquiera de ellas). Son restos de la unificación del 11/08 que
nadie borró. Si te encuentras con el checkout en una de ellas, no hay nada que
rescatar: `git checkout main && git pull --rebase` y a trabajar. Todo lo que describe
este documento —prospección unificada, envío por Hostinger, la renovación visual del
13/08— vive en `main`.

**Cambios estéticos, solo en bloque.** El 13/09 se descartó un experimento a medio
hacer en **studio32-panel** que pasaba el panel del verde al bronce cálido de la web.
No era mala idea, pero Pancho decidió que cualquier mejora visual o de experiencia se
hace **a la vez en todas las herramientas** (web, Hub, panel), nunca en una sola, y no
antes de que haya un cliente. Si alguien lo retoma, la regla que sí vale la pena
conservar: verde, ámbar y rojo indican estado (correcto, atención, error) y no se
tocan al cambiar el color de marca.

---

## Credenciales

**No están en este archivo ni en ningún archivo del repo**, porque el repo es
público. Pancho te las da directamente en el chat cuando las necesites (acceso al
Hub, al panel, a Supabase). Por política, nunca las tecleas tú en un formulario de
login aunque se te autorice — él entra y tú continúas una vez dentro de la sesión.

---

## Reglas que no se rompen en ningún repo de Studio32

- **`git branch -r` y comprobar el esquema real de Supabase antes de tocar
  prospección o cualquier tabla compartida.** Ya ha costado dos días de trabajo
  duplicado por construir lo mismo dos veces en máquinas distintas sin saberlo la una
  de la otra — la última vez fue el propio sistema de prospección.
- **Rutas relativas siempre** en cualquier documentación de contexto. Nunca
  `C:\Users\...` ni nombres de máquina: el usuario del sobremesa no es el mismo que
  el del portátil, y una ruta absoluta se rompe al migrar.
- `git pull --rebase` al empezar en cualquier repo, commit + push al terminar. Los
  repos de Studio32 se trabajan desde dos máquinas.
- Los datos de contacto de prospectos reales **nunca se versionan** — van a la
  carpeta temporal de la sesión, nunca al repo.
- Si algo de `.ai/` o de este archivo ya no es cierto cuando lo leas, **corrígelo tú
  mismo**. Documentación obsoleta es peor que no tener documentación.
