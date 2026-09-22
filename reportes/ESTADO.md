# Estado actual · Agente de IA (foco: conseguir el primer cliente)

> La foto de AHORA. Si lees una sola cosa, que sea esta. Última actualización: 22/09/2026.
>
> **La ruta entera, en una página que se va actualizando:**
> https://claude.ai/artifact/NRjfm76oqA5cy7mDbx1xyu

## 🔴 Se borró la base de datos por error, y se ha recompuesto (22/09)

Anoche se borró sin querer el proyecto de Supabase que el 20/09 había pasado a
guardarlo todo: el agente, el panel de clientes y el Hub recién fusionado. Sonó
peor de lo que fue: el agente y las citas **no dependen solo de esa base** —
las conversaciones de WhatsApp y las reservas viven también en un fichero en
Railway, y la agenda real es Google Calendar, no una tabla. Comprobado en vivo:
con la base borrada, el agente seguía respondiendo sin caerse.

**Lo que sí se perdió, sin vuelta atrás:** las cuentas de acceso al panel y al
Hub (recreadas), el registro interno de auditoría, y lo que se tocara en el Hub
entre el 20/09 y anoche (era la única pieza que dependía solo de esa base).

**Dónde estamos ahora:** todo — agente, panel y Hub — vive en un único proyecto
de Supabase que sí sigue en pie, `studio32-hub`. Ya no hay un proyecto de
repuesto: no puede volver a pasar esto dos veces. Detalle completo en
`reportes/2026-09-22-incidente-supabase.md`.

## ⚖️ Datos legales rellenados, y ya no queda nada bloqueando Google (17/09)

El aviso legal y la política de privacidad llevaban desde agosto con el titular, el
NIF y el domicilio como texto de ejemplo. Rellenados con **Juan Manuel Ruiz García**
como titular, autónomo, con su NIF y su domicilio en Torre del Mar (el fuero judicial
pasa de Valencia a Vélez-Málaga, que es el que corresponde de verdad). Se ha añadido
también la sección que exige Google sobre qué se lee del calendario y para qué.

**Comprobado y sin otras faltas legales:** la web no usa ningún analítico ni cookie de
terceros (solo cookies técnicas), así que no hace falta página de cookies aparte.
**Sí falta una que no existe todavía:** condiciones de contratación, para cuando haya
cobro online. No urge hoy, pero hay que prepararla junto con eso, no después.

**Un aviso:** el cambio está subido a GitHub pero, al comprobarlo, la web publicada
(`studio32.pages.dev`) seguía sirviendo la versión vieja. A diferencia del panel, esta
web no tiene un despliegue automático — alguien tiene que mirar en Cloudflare Pages si
hace falta lanzarlo a mano.

## 💶 Precio decidido: 190 €/mes + 300 € de alta (17/09)

Queda por cerrar la promoción de los cinco primeros clientes: la recomendación es
cobrar el alta reducida y regalar solo el primer mes de cuota, no todo gratis, para
filtrar interés real y no fijar un precio de referencia de 0 €.

## 🗣️ El panel ya habla el idioma del dueño, no el nuestro (17/09)

El panel le decía a un dueño de clínica cosas como "aislados mediante RLS" o
"Handoffs pendientes" — nombres de nuestra tecnología interna que no significan nada
para él. Corregido: ahora explica en llano que sus datos están aislados de los de
cualquier otro negocio, y "Asistente"/"Humano" se usa siempre igual. Las etiquetas de
estado (citas, conversaciones) subieron de 8px, casi invisibles, a un tamaño que se lee
en el móvil de una recepción. Comprobado con una sesión real, en móvil.

## 📅 La agenda del cliente ya es de verdad la suya (14–17/09)

El panel enseñaba **una copia**: solo las citas del asistente. Si la clínica apuntaba una
cita en su móvil no aparecía, y **cancelar en el panel no la borraba de su Google**.

Ahora el panel lee Google en directo, cancelar borra también allí, y **la clínica conecta
su calendario con un botón** desde el panel, sin compartir nada a mano. Probado de punta a
punta en producción. Detalle en `reportes/2026-09-17.md`.

**Falta para poder dárselo a un cliente real:** Google tiene que revisar la aplicación
(3–5 días laborables). Mientras tanto, el permiso caduca cada 7 días. Hoy se ha verificado
el dominio y el agente ya tiene dirección propia (`api.studio32.es`); **bloquea** rellenar
los datos del titular en la política de privacidad, que siguen siendo texto de ejemplo.
Pasos y responsables en `notes/VERIFICACION-GOOGLE.md`.

## ✉️ Los correos se presentan y dicen qué ofrecemos (15/09)

Estructura propuesta por Juanma: "Hola, soy [quien aprueba], de Studio32", algo bueno y
concreto del negocio, lo que falla, "es justo lo que montamos" y "¿Os enseño cómo
funciona?". Nunca se prometen llamadas de teléfono, "ejemplo real" ni otros idiomas,
porque no se pueden entregar. Los 63 borradores en cola ya están reescritos así.
Detalle en `reportes/2026-09-15.md`.

## 📬 Desde el 14/09 se envía a diario, con cupo

Decidido con Juanma: más correos, pero **cada día y no a golpes**. 10 al día esta semana,
20 la siguiente y 30 desde la tercera. El Hub ya no deja pasar del cupo del día; lo que no
cabe sigue aprobado y sale mañana. Los motivos, explicados para el equipo, en
`reportes/2026-09-14.md`. Pendiente: dominio aparte para prospección antes de llegar a 30.

Además, **envío automático de lo aprobado** (interruptor en el Hub, apagado de salida: de
lunes a viernes, repartido en el día y se apaga solo si algo falla) y **`/prospectar` con
tres campañas a la vez**. Aprobar sigue siendo de una persona, y es ahora el único paso
que depende del equipo.

## 🧭 Hay un plan escrito: `notes/CAMINO.md`

Desde el 09/09 el orden de trabajo no se improvisa por sesión. Tres decisiones:
**el agente primero y la carta por QR en paralelo**, **se sale a ofrecer en persona**, y
por encima de todo **no se vende lo que no se puede entregar en una semana**.

Eso último pone la verificación del número en Meta —parada desde julio, pendiente de
tener la SIM a mano— por delante de cualquier material de venta.

Detalle de la sesión: `reportes/2026-09-09.md`. Sesión anterior, de herramientas:
`reportes/2026-09-08.md`.

## ✅ El agente ya se comprueba solo (09/09)

Antes, la confianza en que el agente funciona venía de probarlo a mano de vez en cuando.
Ahora hay una prueba que mantiene una conversación completa —reservar, mover, cancelar,
día cerrado, intentar sonsacarle datos de otros— y verifica la agenda de verdad. Siete
de siete, tanto en el ordenador como en lo que está publicado.

El primer día encontró tres fallos serios, ya arreglados: el agente **confirmaba citas
que no había creado**, cualquiera podía **cancelar la cita de otra persona** dando su
teléfono, y en la demo de la web dos visitantes se pisaban. Detalle en
`reportes/2026-09-09.md`.

## 🚨 Lo único urgente: hay 40 correos escritos esperando aprobación

La bandeja de Prospección del Hub tiene **40 correos por revisar**. Once llevan escritos
desde el 16/08.

**Ojo, que esto se había contado mal:** en agosto sí salieron correos. Entre el 12 y el
23/08 se enviaron **19 a negocios reales** (18 desde francisco@ y 1 desde gonzalo@),
más uno de prueba: fisioterapia en Guadalajara, clínicas dentales en Valencia y
Barcelona, y estética en Valencia. Nadie ha pedido la baja. Las respuestas no llegan al
Hub, llegan al buzón de quien firmó, así que hay que mirarlas allí. Comprobado contra la
base de datos del Hub el 13/09.

**El 12/09 se han corregido 29 de los 40**: diagnosticaban bien el problema del negocio
y nunca decían con qué se resolvía, así que terminaban en un cierre vago en vez de una
oferta. Detalle en `reportes/2026-09-12.md`. Ya se pueden leer y aprobar con confianza.

Escribir más correos no mueve el reloj. **Entrar en el Hub, leerlos y aprobar los que
convenzan, sí.** Es la única tarea que separa a Studio32 de tener una conversación
con alguien.

## 🆕 Sesión 04/09 · siete ciudades nuevas

Detalle completo: `reportes/2026-09-04.md`.

Ocho campañas nuevas de clínicas dentales (Málaga, Valencia, Sevilla, Zaragoza, Murcia,
Alicante, Granada, Valladolid) y **dieciséis leads nuevos con el correo escrito**. Solo
queda pendiente Alicante, donde la zona no daba para una tanda decente.

El ángulo que ha funcionado no es la web: es **el horario**. Clínicas con cuatro o cinco
horarios distintos en la misma semana, huecos de tres horas al mediodía, cerradas de
viernes a domingo. Es un dato verificable y lleva directo a la pregunta que interesa:
quién coge el teléfono cuando no hay nadie.

## GH Dent ya no existe

Se les envió el presupuesto y nunca respondieron. **Studio32 está sin ningún cliente.**
No perseguir ese hilo ni tratarlo como cliente activo. Lo que quedaba a medias con Meta y
Google Calendar deja de ser un bloqueo: no hay nadie esperando al otro lado.

## Sesión 23/08 · fisioterapia en Torre del Mar, y una fuente nueva de reseñas

Detalle completo: `reportes/2026-08-23.md`. De ahí salieron cinco de los correos que
siguen sin aprobar (Fisiomar, ACOSTA, Axarclinic, Valenzuela, Fisioesmile).

**Lo que sigue sirviendo:** se encontró una fuente que copia las reseñas de Google
enteras, con nombre y fecha, para negocios que no están en Doctoralia. Hasta entonces
esos negocios se descartaban por no poder citar a nadie. Queda anotado en la
documentación del Hub.

## Sesión 13/08 · el Hub ya se ve y se usa como un sitio terminado

El Hub funcionaba bien pero se veía a medias: mucho blanco, letras pequeñas y una
navegación que se hacía un lío en pantallas de tamaño intermedio. Se ha renovado el
aspecto entero — fondo cálido, verde de Studio32, tarjetas con algo de relieve, texto
más grande — y se ha reordenado cómo se revisan los correos de prospección.

**Lo que se nota al abrirlo:**

- **La cola de correos ya no confunde.** Antes, un correo descartado seguía contando
  en el número de "pendientes" de la portada aunque ya no apareciera en la lista de
  Prospección — el aviso decía uno y la pantalla enseñaba otro. Ahora los dos cuentan
  lo mismo.
- **Las campañas ya probadas (Torrejón, Alcalá, Valencia…) no ensucian la vista.**
  Quedan aparte, en un grupo de pruebas, y la lista principal solo enseña campañas
  reales con trabajo pendiente de verdad.
- **La revisión se organiza por lo que hay que decidir**, no por cómo está guardado
  por dentro: por revisar, listos para enviar, o ya enviados — y aparte, un filtro para
  los que tienen poca evidencia detrás y conviene mirar con más calma.
- **El móvil ya no amontona ocho botones en la barra de abajo.** Quedan los cinco que
  se usan cada día; el resto vive en un menú "Más" con su explicación.

No hay nada nuevo que aprender ni ningún dato que revisar de más: es la misma
información, mejor puesta. Sigue habiendo cuatro correos de fisioterapia esperando
aprobación de la sesión del 12/08.

**Y sigue parado lo de siempre:** GH Dent, con Meta y el Google Calendar. Esto es
pulido de la herramienta de captación, no producto — el reloj del primer cliente no
se ha movido.

## Sesión 12/08 · hay cuatro correos esperando visto bueno

Detalle completo: `reportes/2026-08-12.md`.

La máquina ha buscado clientes sola por primera vez. De una campaña pedida desde el Hub
—fisioterapia en Guadalajara— ha salido con **cuatro correos escritos y en borrador**,
cada uno apoyado en una reseña concreta de un paciente de ese centro.

**Lo que hace falta de nosotros: entrar en el Hub, leerlos y aprobar los que convenzan.**
Nada sale hasta entonces. Antes de dar a enviar, leer la lista de destinatarios que
aparece en la confirmación: en la cola queda material viejo de pruebas.

Se pidieron 10 y hay 4: seis se descartaron por no tener ni una reseña citable, y la
campaña sigue abierta para completarla en otra pasada.

**Y sigue parado lo de siempre:** GH Dent, con Meta y el Google Calendar. Esto es
captación, no producto — el reloj del primer cliente no se ha movido.

## Sesión 05/08 · el Hub ya reparte trabajo comercial

Detalle completo: `reportes/2026-08-05.md`.

Se ha construido la prospección dentro del Hub. Pancho prepara una tanda de negocios a los
que escribir y Juanma entra, los revisa y los envía. Cada correo se apoya en algo real de
ese negocio —lo que dicen sus propios clientes en las reseñas— y **debajo están las citas
literales que lo sostienen**, para que quien revisa pueda comprobarlo y defenderlo.

Probado con una clínica dental de Guadalajara, 22 reseñas leídas. Sus pacientes la adoran
por el trato, y lo único de lo que se quejan es de las esperas y las citas — que es justo lo
que arreglamos. La queja no se menciona en el correo, a propósito. El nombre no se pone aquí
porque este repositorio es público; está en el Hub.

Se puede ver ya, sin tocar el Hub del día a día:
**https://feat-prospeccion-email.studio32-hub.pages.dev**

~~**Falta para poder enviar:** conectar la cuenta de correo y dar permiso desde
Supabase.~~ → **RESUELTO el 11/08.** Se conectó, se probó con una dirección nuestra y el
primer correo salió de verdad. Ver la sección del 11/08 al final.

**Y sigue parado lo de siempre:** GH Dent, con Meta y el Google Calendar.

## ✅ Hecho y probado en vivo

- El agente está **desplegado** y se le puede hablar por WhatsApp (por ahora, por el
  número de pruebas de Twilio).
- **Personalidad a medida:** cercano, entiende el miedo del paciente, ofrece la
  valoración gratuita, no da precios ni confirma mutuas por chat, no diagnostica.
- **Flujos probados de punta a punta:** reservar, cancelar, mover una cita, derivar a
  una persona, captar interesados sin cita, agenda del dueño. Y **no se deja engañar**
  por alguien que dice ser la dueña para sacar datos de pacientes.
- **Avisos por email:** cada reserva dispara un correo desde `citas@studio32.es`.
  Durante las pruebas llega a `soporte.studio32@gmail.com`.
- **Citas para hoy** (urgencias del día): arreglado y verificado el 27/07.
- Las citas **se ven en el panel**.

## 🚨 Bloqueante para entregar

1. ~~El agente olvida las citas al actualizar~~ → **RESUELTO el 27/07.** Se conectó un
   disco permanente al servidor. Verificado: se reserva una cita, se actualiza el
   sistema, y la cita **sigue ahí**. Ya no hay riesgo de citar a dos pacientes a la
   misma hora por este motivo.
2. ~~Google Calendar sin conectar~~ → **RESUELTO el 14–17/09.** La clínica conecta su
   propio calendario desde el panel con un botón, y esa pasa a ser la agenda: el
   asistente y el panel leen y escriben ahí. Queda pendiente la revisión de la
   aplicación por parte de Google (ver arriba).
   ⚠️ **Sigue valiendo preguntar a la clínica dónde lleva su agenda hoy**: el agente
   mira un único calendario, así que las citas que entren por teléfono tienen que
   estar ahí también, o habrá solapamientos.

## ⏳ Pendiente para el go-live real

- **WhatsApp propio de la clínica**: verificar el número en Meta (hoy: número de
  pruebas).
- **Avisos al correo de la clínica** (hoy van a Studio32, a propósito, para no
  molestar con citas de prueba).
- **Nombre del agente**: sin nombre humano. Pendiente de que decida la clínica.
- **Manual de usuario** de la clínica.

## 🔍 A vigilar (no bloqueante)

- Al pedir la agenda, el dueño podría recibir un resumen al que le falte una cita.
- Muy de vez en cuando el agente confunde un día abierto con cerrado. No es la
  herramienta (que responde bien), es el resumen del modelo.

## 🎯 Siguiente gran paso (producto)

- Convertir "investigar negocio → crear personalidad a medida" en una **herramienta
  reutilizable**, para montar cada cliente nuevo en minutos.

## 🆕 Sesión 31/07 – 01/08 · la web ya enseña el agente de verdad

Traspaso completo, con las trampas técnicas: `reportes/2026-08-01-traspaso.md`.

**Lo importante en llano:**

- **studio32.es ya deja hablar con el agente.** No es un vídeo ni una captura:
  el visitante escribe y contesta el mismo agente que atiende WhatsApp, y ve el
  panel del negocio actualizarse mientras habla, con la cita apareciendo de verdad.
- **Tres sectores para elegir**: clínica, restaurante y servicio local. Cada uno
  es un negocio distinto de verdad, con su forma de hablar y sus normas. El del
  restaurante conoce la carta y los alérgenos; el de servicios no da precios a
  ciegas, pregunta lo que haría un técnico y pasa el aviso con todo apuntado.
- **El agente habla mucho mejor.** Antes sonaba a folleto ("contamos con un
  enfoque cuidadoso"). Ahora suena a recepción: *"Tranquilo, aquí entra gente que
  lleva más tiempo. La primera visita es solo mirar y contarte qué hay, sin coste."*
- **La web cambió de aspecto**: era oscura y se veía apagada; ahora es clara.
- **Cada visitante tiene su propia agenda**, así que las pruebas de unos no
  ocupan huecos a otros, y hay topes de uso para que la demo no dispare el coste.

**Lo que sigue parado y es lo único que separa de facturar:** GH Dent, con sus
dos bloqueantes de siempre — verificar el número en Meta y conectar el Google
Calendar. Ninguno de los dos es programar.

## 🆕 Sesión larga 01/08 (tarde) · la web pasa de una página a seis

**Lo nuevo, en llano:**

- **Tres páginas por sector**: clínicas dentales, restaurantes y servicios
  locales. Cada una abre con el agente de ESE sector ya listo para hablar, así
  que se le puede mandar a un prospecto el enlace de lo suyo. Además son las
  páginas que Google puede encontrar cuando alguien busca "agente WhatsApp
  clínica dental", que hasta hoy no existían.
- **Una página del panel** que se puede recorrer entero: resumen, conversaciones,
  calendario de citas, servicios editables y el asistente. Está hecha mirando el
  panel de verdad, no inventada.
- **Una página de precio** que explica cómo se paga y, sobre todo, aclara algo
  que casi nadie cuenta: **WhatsApp no cobra cuando es el cliente quien escribe
  primero**, y las primeras 1.000 conversaciones al mes son gratis. Para una
  recepción eso significa que ese coste, en la práctica, es cero.
- **El pie de la web** ahora lleva a todas esas páginas, que además ayuda a que
  Google las encuentre.
- **Arreglado**: la cabecera de las preguntas frecuentes ya se queda quieta
  mientras bajas, la burbuja de chat de la esquina se ha quitado (estorbaba y
  confundía con la demo), y la web carga más rápido para quien repite visita.

**Lo que sigue igual y sigue siendo lo importante:** GH Dent. Verificar el número
en Meta y conectar el Google Calendar. Nada de esto es programar, y es lo único
que separa de facturar.

---

## 🆕 Sesión 11/08 · ya podemos captar clientes desde el Hub

Detalle completo: `reportes/2026-08-11.md`.

**Hecho y probado con un envío real:**

- **El Hub manda correos a posibles clientes.** Se pide una campaña ("clínicas
  dentales en Alcalá, 20"), la máquina investiga cada negocio y escribe su correo, y
  aparecen en el Hub para aprobar. Se aprueba, se envía.
- **Cada uno firma con su dirección**: juanma@, gonzalo@ y francisco@studio32.es. Si el
  negocio responde, **la respuesta cae en nuestra bandeja de siempre**.
- **Ningún correo sale sin que una persona lo apruebe.** Comprobado.
- **A quien pide la baja no se le vuelve a escribir.** Comprobado: se intentó enviar a
  propósito a una dirección dada de baja y el sistema se negó.

**⚠️ Necesita a alguien:**

- Hay un correo preparado para **Clínica Dental Dr. Garcés** esperando en el Hub, en
  "pendiente de revisar". Alguien tiene que leerlo y decidir si sale.
- Si un negocio responde "BAJA", esa respuesta llega al correo pero **hay que pasarla a
  mano** pulsando "No escribir más" en el Hub.

**Pendiente:** dejar la pantalla bonita (es lo siguiente), una página de bajas, y probar
una campaña completa de verdad.

**Lo que sigue siendo lo importante:** GH Dent. Verificar el número en Meta y conectar
el Google Calendar. Esto de captación avanza en paralelo, pero no mueve ese reloj.
