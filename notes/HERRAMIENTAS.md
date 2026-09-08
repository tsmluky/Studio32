# Herramientas de fuera que nos pueden servir

> Revisión hecha el 08/09/2026. Las estrellas y fechas son de ese día, sacadas de la
> API de GitHub, no de un blog. Si vuelves a leer esto dentro de seis meses, comprueba
> que el proyecto sigue vivo antes de instalar nada.

El criterio de esta lista no es "qué está de moda". Es una sola pregunta:
**¿esto acerca al primer cliente firmado, o solo da gusto instalarlo?** Todo lo que
no pasa ese filtro está abajo del todo, en la sección de "no, y por qué".

---

## 1. Para lo que está bloqueando ahora mismo

Lo pendiente antes de la primera respuesta real de prospección es el manual y los
vídeos promocionales. Estas dos herramientas atacan justo eso.

### OpenScreen — vídeos de demo con acabado profesional

`getopenscreen/openscreen` · 2.518 ★ · MIT · actualizado hoy mismo

Grabas la pantalla y te hace el trabajo que se nota en un vídeo de producto: zooms
automáticos donde pasa algo, el cursor suavizado, fondos con degradado, exportación a
MP4 o GIF en varias proporciones. Es lo que hace Screen Studio, que es de pago y solo
de Mac, pero gratis y con instalador de Windows (está en la Microsoft Store, firmado;
el `.exe` suelto de GitHub no está firmado y salta el aviso de SmartScreen).

Por qué encaja: los vídeos de la demo de Cobalto o del panel se pueden grabar en una
tarde y quedan como un producto vendido, no como una captura de pantalla. El audio del
sistema y la webcam funcionan de serie en Windows.

**Veredicto: instalar ya.** Es la herramienta con más retorno inmediato de toda la
lista.

### Remotion — vídeos generados con código

`remotion-dev/remotion` · 58.611 ★ · actualizado hoy

Haces vídeos escribiendo React. Suena raro hasta que caes en que vas a necesitar el
mismo vídeo promocional para dental, para fisioterapia, para restaurante, cambiando
solo el texto, el logo y las capturas.

**Veredicto: todavía no.** Tiene sentido cuando el vídeo se repita por vertical y
estés cansado de reeditarlo a mano. Antes de eso es montar una fábrica para hacer una
pieza. Anótalo para cuando haya tres o cuatro verticales.

---

## 2. Para el producto, cuando toque

### promptfoo — pruebas de regresión para el criterio del agente

`promptfoo/promptfoo` · 24.925 ★ · MIT · actualizado hoy

Escribes casos de prueba para un prompt o un agente entero y los pasas cada vez que lo
tocas: "si el paciente pregunta por un precio que no está en la ficha, no se lo puede
inventar", "si pide cita fuera de horario, ofrece la siguiente hueco real". Falla el
caso, se ve en rojo.

Por qué encaja de verdad: lo que vendes de `studio32-agent` es que **no inventa** y que
**tiene criterio del oficio**. Ahora mismo eso es una promesa. Con esto pasa a ser algo
que se comprueba, y esa es la traducción directa a beneficio de cliente que buscas cada
vez que mejoras un guard por dentro. De paso protege la congelación de scope: puedes
afinar prompts sin miedo a romper lo que ya funcionaba.

**Veredicto: es la mejor incorporación técnica de la lista.** Y no rompe la
congelación, porque no es una feature nueva: es red de seguridad para lo que ya hay.

### Langfuse — ver qué pasa en las conversaciones reales

`langfuse/langfuse` · 34.333 ★ · actualizado hoy

Trazas de cada conversación en producción: qué preguntó el cliente final, qué decidió
el agente, cuánto costó. Se puede alojar uno mismo.

**Veredicto: el día que haya un cliente vivo, no antes.** Sin conversaciones reales no
observas nada. Pero apúntalo, porque el primer mes en producción vas a querer saber
por qué el agente contestó lo que contestó, y sin esto se hace a ciegas.

### Chatwoot — bandeja para cuando el agente pasa a un humano

`chatwoot/chatwoot` · 36.592 ★ · actualizado hoy

Bandeja de atención multicanal, con WhatsApp incluido, código abierto.

**Veredicto: mirarlo antes de construir el traspaso a humano en `studio32-panel`.**
No para usarlo necesariamente, sino para no reconstruir gratis algo que ya existe
hecho. Si un cliente pide "que cuando el agente no sepa, me salte a mí", esto ya lo
resuelve.

---

## 3. Para la prospección

### Crawl4AI — leer la web de un negocio y sacar su huella

`unclecode/crawl4ai` · 81.948 ★ · Apache 2.0 · actualizado hoy

Un rastreador pensado para darle de comer a un modelo: le pasas una web y te devuelve
el contenido limpio y estructurado, en local y sin pagar API.

Por qué encaja: es exactamente la pata de "huella minada del negocio" del modelo de dos
capas. Para preparar un arquetipo de vertical o la evidencia de un lead, necesitas leer
la web del negocio, su carta, sus servicios, sus horarios. Esto lo hace bien y gratis.

**Veredicto: probarlo en la próxima pasada de prospección.** Es un accesorio de
`/prospectar`, no un sustituto.

Alternativa: `firecrawl/firecrawl` (177.831 ★) es más potente, pero es AGPL y está
pensado para su servicio alojado. Para lo tuyo, Crawl4AI es mejor encaje.

---

## 4. Para el día a día con Claude Code

### Context7 — documentación al día dentro del agente

`upstash/context7` · 61.774 ★ · MIT · actualizado hoy

Servidor MCP que le da al agente la documentación real y de la versión correcta de las
librerías que usas (Supabase, Next, lo que sea) en vez de la que recuerda de memoria.

**Veredicto: instalar, es barato y quita errores tontos.**

### ccusage — en qué se va la suscripción

`ccusage/ccusage` · 18.420 ★ · actualizado hoy

`npx ccusage` y ves el consumo por sesión y por proyecto.

**Veredicto: útil precisamente porque `/prospectar` corre en local con la
suscripción.** Saber cuánto cuesta generar una campaña es un dato de negocio, no de
curiosidad.

### Repomix — empaquetar un repo en un archivo

`yamadashy/repomix` · 28.241 ★ · MIT

Convierte un repo entero en un solo archivo legible por un modelo.

**Veredicto: utilidad suelta, no un cambio de flujo.** Sirve para el día que quieras
una segunda opinión de otro modelo sobre un repo completo.

### Catálogos para curiosear, no para instalar

- `hesreallyhim/awesome-claude-code` — 53.681 ★, lista curada de todo el ecosistema.
- `davila7/claude-code-templates` — 30.567 ★, plantillas y configuraciones.
- `wshobson/agents` — 39.490 ★, mercado de agentes y plugins.

Son índices. Se miran cuando buscas algo concreto, no se adoptan.

---

## 5. Los dos que preguntaste

### spec-kit — sí, pero solo una pieza

`github/spec-kit` · 134.027 ★ · de GitHub

Es "desarrollo dirigido por especificación": antes de escribir código, escribes qué se
va a construir, y el flujo va constitución → especificar → planificar → tareas →
implementar → validar. La "constitución" son los principios del proyecto que el agente
tiene que respetar sí o sí en cada paso.

Lo honesto: el flujo completo de seis fases es mucha ceremonia para un equipo de tres
con cero clientes, y además **ya tienes una versión casera y más ligera** — `CONTEXTO.md`,
`.ai/STATE.md` y `.ai/DECISIONS.md` hacen buena parte de ese trabajo.

Lo que sí merece la pena robarle es **la constitución**. Un archivo corto con las
reglas que el agente no puede saltarse, cargado en cada sesión, es exactamente la
herramienta contra el problema que ya está identificado por escrito: abrir features
nuevas antes de terminar las que hay. "Congelación de scope hasta el primer cliente
cobrando" es una regla de constitución de manual.

**Veredicto: no adoptes el paquete entero. Prueba el flujo en una sola feature del Hub
para ver cómo se siente, y quédate con la constitución pase lo que pase.** En
`studio32-agent` no lo metas ahora: está congelado, no hay nada que especificar.

### oh-my-codex — no

`Yeachan-Heo/oh-my-codex` · 33.025 ★ · MIT

Es una capa de flujo de trabajo encima del CLI de Codex, el de OpenAI: hooks, equipos
de agentes, paneles en vivo. Está bien hecho y muy mantenido.

Pero: necesita el CLI de Codex instalado y con cuenta propia (otra suscripción aparte),
necesita tmux para la parte de equipos, y está pensado y afinado para macOS y Linux —
Windows es el pariente pobre. Tú estás en Windows 11 y pagando Claude.

Y lo importante: lo que aporta —equipos de agentes, planificación estructurada,
subagentes— ya lo tienes en Claude Code sin instalar nada.

**Veredicto: no aporta. Ni siquiera por curiosidad, porque el coste de entrada es una
suscripción distinta.**

---

## 6. Lo que NO deberíamos tocar, y por qué

Esta sección vale tanto como las de arriba.

**Baileys (`WhiskeySockets/Baileys`, 10.977 ★) y Evolution API (9.560 ★)** — librerías
que hablan el protocolo de WhatsApp Web por debajo, sin pasar por Meta. Son muy
populares y muy tentadoras porque te saltan todo el papeleo de verificación que ahora
mismo tiene parado a GH Dent. **Ni de broma en el número real de un cliente:** es uso no
oficial y el riesgo es que Meta cierre el número del negocio. Estamos en la API oficial
Cloud y ahí nos quedamos. El bloqueo de verificación es un trámite, no un problema
técnico que se resuelva cambiando de librería.

**n8n (203.709 ★) y Activepieces (24.333 ★)** — automatización visual con nodos. El
problema no es que sean malos, es que invitan a reconstruir en cajitas lo que
`studio32-agent` ya hace en código, y a abrir scope. Solo tendría sentido si un cliente
concreto pide una integración rara que no tenemos.

**Typebot (10.314 ★)** — constructor de bots de árbol de decisión. Es literalmente lo
que ya se descartó: bots a medida por cliente. Saltar.

**Superpowers (`obra/superpowers`, 283.024 ★)** — el plugin más instalado del
ecosistema. Impone una metodología completa con TDD estricto y revisiones automáticas
en cada paso. Es bueno, y también es caro en tokens y muy verboso. El cuello de botella
del negocio ahora no es la calidad del código: es que no hay clientes. Saltar de
momento.

**claude-mem (93.449 ★)** — memoria persistente entre sesiones para el agente. Ya está
resuelto con la convención `.ai/` sincronizada por git, que además funciona entre las
dos máquinas. Meter esto encima duplicaría la fuente de verdad, que es justo el error
que ya costó dos días de trabajo duplicado.

**Scrapers masivos de Google Maps** (`omkarcloud/google-maps-scraper`, 3.447 ★ y
similares) — extraen cientos de negocios con teléfono y correo de una tacada. Aquí hay
dos motivos para no ir por ahí, y el segundo es el serio:

1. La prospección ya funciona de punta a punta y su valor está en que cada lead lleva
   evidencia trabajada, no en el volumen.
2. Recolectar correos en masa y enviarles comercial en frío es terreno delicado con el
   RGPD en España, sobre todo si algún correo es de persona física y no de empresa.
   Pocos correos, bien razonados y con motivo real de contacto, es una posición mucho
   más defendible que mil correos comprados a un scraper.

---

## Resumen en tres líneas

- **Esta semana:** OpenScreen para los vídeos, y probar Crawl4AI en la próxima campaña.
- **Cuando vuelvas a tocar el agente:** promptfoo, para que "no inventa" deje de ser
  una promesa y sea una prueba que pasa.
- **Cuando haya cliente vivo:** Langfuse. Y de spec-kit, quédate solo con la
  constitución.

---

# Puesta en marcha (08/09/2026)

Lo que ya está montado en el portátil y cómo repetirlo en el sobremesa.

## Context7 — hecho

Añadido como servidor MCP global en `~/.claude.json`, así que vale para todos los
repos de esta máquina. Hay copia de seguridad del archivo anterior en
`~/.claude.json.bak-20260908`. Se activa al reiniciar Claude Code.

Para repetirlo en el sobremesa, añade esto dentro de `mcpServers` en `~/.claude.json`:

```json
"context7": { "type": "stdio", "command": "npx", "args": ["-y", "@upstash/context7-mcp@latest"] }
```

Funciona sin clave, con un límite de peticiones bajo. Si se queda corto, hay claves
gratuitas en context7.com/dashboard y se pasan con `--api-key` o la variable
`CONTEXT7_API_KEY`.

## promptfoo — montado, falta una clave para poder lanzarlo

Vive en `evals/` dentro de **studio32-agent**, con su propio README. Doce casos que
comprueban las promesas de venta: que no da precios ni cuando le insisten, que no
confirma una mutua por su nombre, que no promete "te aviso luego", que sabe que los
sábados está cerrado y que los viernes solo abre por la mañana, que no diagnostica, que
no trata el miedo con prisa, que no revela la agenda a quien no es el dueño, y que no
suelta sus instrucciones si se las piden.

Se lanza con `npm run eval` y se ve el detalle con `npm run eval:view`.

promptfoo **no entra en las dependencias del repo**, y no por pereza: pide `zod` 4 y el
`openai` que usa el agente pide `zod` 3, así que instalarlo dentro obliga a forzar la
resolución de dependencias en un repo que se despliega en Railway. Como es una
herramienta de línea de comandos y no una librería que importe el código, los scripts
lo lanzan con `npx`, que resuelve lo suyo en un árbol aparte.

**Bloqueado por una cosa:** el `.env` del portátil solo tiene las claves de Supabase,
no hay `OPENAI_API_KEY`. Sin ella el agente cae al proveedor `mock`, que no razona, y
los resultados no valen — el propio banco de pruebas te lo avisa por consola. Hace
falta poner una clave en el `.env` local (vale una barata y aparte de la de
producción). Una pasada de los doce casos cuesta céntimos.

Las reservas que el agente crea durante una evaluación van a `.eval-data/`, ignorada
por git. Nunca tocan `data/` ni la agenda real.

## Crawl4AI — instalado y probado

En `herramientas/crawl4ai-venv/` en la raíz del workspace, que **no es un repositorio**
y por tanto no viaja. Es a propósito: es herramienta de máquina, no del producto, y no
tiene por qué ensuciar ningún repo.

Para montarlo en el sobremesa (el segundo comando baja el navegador que usa por
debajo, que son unos cuantos cientos de megas):

```bash
py -m venv herramientas/crawl4ai-venv && herramientas/crawl4ai-venv/Scripts/python.exe -m pip install crawl4ai && herramientas/crawl4ai-venv/Scripts/crawl4ai-setup.exe
```

Encima hay un script, `herramientas/huella.py`: le pasas la web de un negocio y te
deja su huella en un solo markdown limpio. Entra por la portada, sigue los enlaces que
suenan a servicios, precios, horarios, equipo y contacto, y si la web es de una sola
página con anclas —que es lo normal en un negocio local— se cae a las demás páginas
del dominio para no volverse con las manos vacías.

```bash
herramientas/crawl4ai-venv/Scripts/python.exe herramientas/huella.py https://ghdent.es --paginas 7
```

Probado contra la web de GH Dent: siete páginas, 39.000 caracteres, y salen el horario
real, la financiación a 36 meses, lo de las más de 20 mutuas, los tratamientos uno a
uno, el equipo y el contacto. Justo la materia prima de la capa de "huella minada del
negocio".

Los resultados van a `herramientas/huellas/`, fuera de todo repositorio, por la regla
de no versionar nunca datos de prospectos.

## OpenScreen — lo instalas tú

Es una aplicación de escritorio, no algo que se pueda dejar configurado desde aquí.
Lo más limpio es la Microsoft Store, que va firmada y se actualiza sola:

```bash
winget install --id 9NL4BLPB5W5D --source msstore --accept-package-agreements --accept-source-agreements
```

Si `winget` no lo encuentra, busca "OpenScreen" en la Store, o baja el `.exe` de las
releases de GitHub (ese no está firmado y salta el aviso de SmartScreen).

## Langfuse — no se ha tocado, y es lo correcto

Sin ninguna conversación real en producción no hay nada que observar. Se monta el día
que haya un cliente vivo, no antes.
