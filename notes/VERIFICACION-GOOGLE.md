# Verificación de Google · "Conectar Google Calendar"

> Empezado el 14/09/2026. Por qué hace falta: la app pide permisos **sensibles** de
> Calendar, y mientras esté "en prueba" el acceso de cada clínica **caduca a los 7
> días**. Sin verificación no se puede dar el servicio a un cliente real. Google suele
> tardar 3–5 días laborables en revisar, así que va antes que cualquier otra mejora.
>
> Detalle técnico de la conexión: repo `studio32-agent` → `.ai/DECISIONS.md`, 14/09.
> Aquí no hay secretos: el repo es público.

## Lo que falta, y de quién es

| Paso | Quién | Estado |
|---|---|---|
| Dirección propia del agente: `api.studio32.es` (Railway ya la tiene pedida) | Pancho, en Cloudflare: `api` → CNAME → `h495u51o.up.railway.app`, nube **gris** | Pendiente |
| Cambiar la vuelta de Google a `https://api.studio32.es/google/callback` (consola + Railway) | Claude, cuando el dominio responda | Pendiente |
| Verificar `studio32.es` en Google Search Console (propiedad de dominio) | Pancho, con la cuenta dueña del proyecto de Google Cloud | Pendiente |
| Datos del responsable en la política de privacidad (titular, NIF, domicilio) | Pancho (decisión: ¿autónomo o sociedad?) | **Bloquea** |
| Ampliar la política con los datos de Google y el papel de encargado (texto abajo) | Claude | Preparado |
| Rellenar "Branding" en Google Auth Platform (valores abajo) | Pancho o Claude con su visto bueno | Pendiente |
| Grabar el vídeo del flujo (guion abajo) | Pancho, con el ensayo `cobalto-ensayo` | Pendiente |
| Enviar a verificación | Pancho | Pendiente |
| Tras aprobar: rotar `INTEGRATION_SECRET_KEY` y reconectar el ensayo | Claude | Pendiente |

## Branding (Google Auth Platform → Branding)

- **Nombre de la app:** Studio32
- **Correo de asistencia:** soporte.studio32@gmail.com
- **Logo:** mejor sin logo de momento. Subir uno obliga a revisar también la marca y
  alarga el proceso; se puede añadir después.
- **Página principal:** https://studio32.es
- **Política de privacidad:** https://studio32.es/legal/privacidad.html
- **Condiciones del servicio:** https://studio32.es/legal/aviso-legal.html
- **Dominios autorizados:** `studio32.es` — solo ese. Si aparece `railway.app` (se
  añade solo al registrar una vuelta en Railway), hay que quitarlo: no se puede
  verificar y bloquea la revisión.
- **Contacto del desarrollador:** soporte.studio32@gmail.com

## Justificación de cada permiso

Google la pide en inglés. Cada texto explica para qué se usa y por qué no basta uno más
estrecho.

**`https://www.googleapis.com/auth/calendar.events.owned`**

> Studio32 provides a WhatsApp reception assistant for small local businesses such as
> dental clinics. The business owner connects the Google Calendar where they keep
> their appointments. The assistant reads the events on that calendar to know which
> time slots are already taken (including appointments the owner adds from their
> phone), creates an event when a patient books through WhatsApp, moves it when the
> patient reschedules, and deletes it when the patient cancels. The business dashboard
> shows the same calendar so the owner sees one single agenda. We only operate on the
> one calendar the owner selects, and only on calendars they own. Narrower scopes are
> not enough: `calendar.freebusy` / `calendar.events.freebusy` cannot create, update or
> delete appointments, and the read-only scopes cannot write the bookings, which is
> the core feature. `calendar.app.created` only covers calendars created by our app,
> but businesses need us to use the calendar they already use every day.

**`https://www.googleapis.com/auth/calendar.calendarlist.readonly`**

> After connecting, the owner chooses which of their calendars the assistant should
> use (for example, a dedicated "Clinic appointments" calendar instead of their
> personal primary calendar). We read the calendar list only to show that selector and
> keep only calendars the user owns. No other calendar data is read from the list.

**`openid`, `email`** — no son sensibles. Se usan para mostrar en el dashboard con qué
cuenta de Google está conectado el negocio.

## Texto que añadir a la política de privacidad

Va en `studio32-web` → `site/legal/privacidad.html`, como secciones nuevas. Lenguaje
llano, de tú a tú con el negocio. **Conviene que lo revise alguien con conocimiento
legal antes de publicarlo**; esto es un borrador técnico, no asesoramiento jurídico.

> ### Datos de Google Calendar
>
> Si tu negocio conecta su Google Calendar desde el panel de Studio32, nos autorizas a
> acceder a ese calendario con tu cuenta de Google. Lo usamos solo para lo que ves en
> el producto:
>
> - consultar qué horas están ocupadas, para que el asistente no ofrezca una hora que
>   ya tiene una cita (también las que apuntas tú desde el móvil);
> - crear, mover y cancelar las citas que gestionan tus pacientes por WhatsApp;
> - enseñarte en el panel la misma agenda que tienes en Google Calendar.
>
> Solo trabajamos en el calendario que eliges, y solo en calendarios que son tuyos.
> Guardamos el permiso de acceso cifrado, y ningún miembro del equipo de Studio32 lo
> ve. No vendemos estos datos, no los usamos para publicidad ni los compartimos con
> terceros, salvo con los proveedores técnicos imprescindibles para que el servicio
> funcione. Para redactar las respuestas del asistente se usa un proveedor de
> inteligencia artificial que no utiliza esos datos para entrenar sus modelos. No
> leemos el contenido de tu calendario salvo que nos lo pidas para resolver una
> incidencia, o por seguridad u obligación legal.
>
> Puedes desconectar Google Calendar cuando quieras desde el panel (Citas →
> Desconectar) o desde la configuración de tu cuenta de Google. Al desconectar
> borramos el permiso guardado; las citas que ya están en tu calendario no se tocan.
>
> El uso que hace Studio32 de la información recibida de las API de Google se ajusta a
> la [Política de datos de usuario de los servicios de API de Google](https://developers.google.com/terms/api-services-user-data-policy),
> incluidos los requisitos de uso limitado.
>
> ### Datos de los pacientes o clientes de tu negocio
>
> Cuando un negocio contrata el asistente, los datos de las personas que escriben por
> WhatsApp (nombre, teléfono, conversación y citas) los trata Studio32 **por cuenta
> de ese negocio**, que es el responsable. Studio32 actúa como encargado del
> tratamiento: solo los usa para prestar el servicio contratado y según las
> instrucciones del negocio.

**Ojo con una línea que hay que confirmar antes de publicarla:** "un proveedor de
inteligencia artificial que no utiliza esos datos para entrenar sus modelos". Hoy el
agente usa OpenAI por API; confirmar su política vigente de datos de API antes de
afirmarlo. Si no se puede confirmar, se quita la frase y se nombra al proveedor como
encargado.

## Guion del vídeo (2–3 minutos, sin editar)

Google pide ver el flujo real, en inglés o con subtítulos, con el nombre de la app y el
ID de cliente visibles. Grabar con el negocio de ensayo `cobalto-ensayo`.

1. Abrir https://studio32.es y enseñar que describe el producto y enlaza la política
   de privacidad (pie de página).
2. Entrar en https://dashboard.studio32.es → Citas → **Conectar Google Calendar**.
3. En la pantalla de Google, **detenerse en la barra de direcciones** para que se lea
   `client_id=…`, y enseñar la pantalla de permisos entera con el nombre "Studio32" y
   los permisos pedidos. Aceptar.
4. Vuelta al panel: aviso de conectado, cuenta y calendario. Pulsar **Cambiar
   calendario** para enseñar el uso de `calendarlist.readonly`.
5. En Google Calendar (web o móvil), crear una cita a mano. Volver al panel y enseñar
   que aparece como "Apuntada en Google Calendar" (lectura de eventos).
6. Por WhatsApp o en la demo, pedir cita al asistente. Enseñar que aparece en Google
   Calendar y en el panel (crear evento).
7. Cancelar esa cita desde el panel y enseñar que desaparece de Google Calendar
   (borrar evento).
8. **Desconectar** desde el panel.

## Después de la aprobación

- Pasar la app de "Prueba" a "En producción" en Público.
- Rotar `INTEGRATION_SECRET_KEY` (la primera quedó a la vista en una sesión) y
  reconectar `cobalto-ensayo`.
- Cambiar esta tabla a "hecho" y anotarlo en `reportes/ESTADO.md`.
