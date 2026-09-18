# Guion del vídeo para la verificación de Google

Fecha: 18/09/2026 · Lo graba Pancho · Vídeo guía de referencia:
`guia-conectar-google-calendar.mp4` (1:50, muestra el recorrido de conexión ya hecho)

---

## 1. Qué tiene que demostrar el vídeo

Google no quiere una demo comercial. Quiere ver **que cada permiso que pedimos se usa
para algo concreto**. Son dos:

| Permiso | Lo que hay que ver en pantalla |
|---|---|
| `calendar.calendarlist.readonly` | Que la app lee la lista de calendarios del negocio y elige uno (sale el nombre del calendario al conectar, y el botón "Cambiar calendario") |
| `calendar.events.owned` | Que la app **crea** una cita en ese calendario y luego la **borra** al cancelarla |

Si solo se ve la conexión y no se ve una cita creada y cancelada, lo devuelven.

**La pantalla roja de "Google no ha verificado esta aplicación" tiene que salir en el
vídeo.** Google lo dice expresamente: es normal en una app pendiente de verificar y
esperan verla. No la esquives.

---

## 2. Antes de grabar

1. **Cierra Shop Titans.** En ventana sigue ocupando toda la pantalla y se cuela en la
   grabación (ya pasó).
2. **Cierra o manda al otro monitor la app de Claude.** Si se restaura sola, sale
   nuestra conversación y la lista de títulos de tus sesiones. No la minimices: se
   restaura ella.
3. **Ventana de Brave limpia**, solo con la pestaña del panel. Oculta la barra de
   marcadores con **Ctrl+Shift+B** (salen WhatsApp, Reddit, TraderCopilot…).
4. **Comprueba que el calendario está desconectado.** Ya lo he dejado así. Si dudas,
   en el panel → Citas tiene que verse el botón *"Conectar Google Calendar"*.
5. Graba **solo la ventana del navegador**, no la pantalla completa (así no entra ni la
   barra de tareas ni notificaciones).

---

## 3. El recorrido, paso a paso

Panel: <https://dashboard.studio32.es> (negocio **Clínica Cobalto · Ensayo**)

1. **Resumen** — 2 s, para que se vea de dónde partimos.
2. **Citas** — se ve el aviso *"Conecta tu Google Calendar"*.
3. Clic en **Conectar Google Calendar**.
4. **Selector de cuenta de Google** → elige **Studio32 · soporte.studio32@gmail.com**.
   (Salen tus otras cuentas; acordamos que no importa.)
5. **Pantalla roja** *"Google no ha verificado esta aplicación"* → **Configuración
   avanzada** → **Ir a studio32.es (no seguro)**.
6. **"Iniciar sesión en studio32.es"** → **Continuar**. Aquí ya se ven los enlaces a
   nuestra Política de Privacidad y Términos: deja 2 s para que se lean.
7. **Pantalla de permisos** — la más importante. **Marca las dos casillas una a una**,
   despacio, y deja que se lea el texto de cada permiso. Luego **Continuar**.
8. Vuelve al panel: *"Google Calendar conectado"* y debajo
   *"soporte.studio32@gmail.com · calendario «soporte.studio32@gmail.com»"*.
   **Señala con el ratón el nombre del calendario y el botón "Cambiar calendario"**:
   eso es la prueba del permiso de lectura de calendarios.

### 9. La cita del asistente (la prueba del permiso de escritura)

Sin parar de grabar, en una terminal aparte ejecuta:

```bash
cd ~/Desktop/Studio32/repos/studio32/studio32-agent && node -e "require('dotenv').config();const t=require('./src/tenants'),r=require('./src/store/supabase'),b=require('./src/store/bookings');(async()=>{const T=await r.hydrateTenant(t.cargarTenant('cobalto-ensayo'));const c=await b.crear(T,{nombre:'Lucía Márquez',servicio:'Higiene dental',contacto:'+34 611 24 87 03',telefono_cliente:'+34 611 24 87 03',fecha:'22/09/2026',hora:'10:00',duracion_min:40});console.log('evento en Google:',c.calendar_event_id)})()"
```

Tiene que imprimir un id de evento. **Si imprime `null`, para: no ha llegado a Google
Calendar y el vídeo no sirve.**

10. Recarga el panel → **Citas** → clic en el **día 22**. Se ve:
    `10:00–10:40 · Lucía Márquez · Higiene dental · CONFIRMADA · Reservada por el asistente`.
11. **Opcional pero potente:** abre `calendar.google.com` en otra pestaña y muestra la
    cita ahí. Es la prueba más directa de escritura.
12. Vuelve al panel y pulsa **Cancelar** → **Confirmar**. El día queda *"No hay citas
    este día"*, y el evento desaparece de Google Calendar.
13. Cierra con **Desconectar** → **Confirmar desconexión**: demuestra que el negocio
    puede revocar el acceso cuando quiera.

Duración objetivo: **2 a 4 minutos**. Sin audio hace falta que las pausas dejen leer;
con audio narrado en español es aún mejor.

---

## 4. Lo que NO puede salir

- La app de Claude (nuestra conversación y los títulos de tus sesiones).
- Tu bandeja de `info@studio32.es`.
- La barra de marcadores.
- Shop Titans.
- El banner *"Claude empezó a depurar este navegador"* (solo aparece si lo conduzco yo;
  grabando tú no sale).

---

## 5. Dónde va el vídeo

1. Súbelo a **YouTube como "No listado"** con la cuenta `soporte.studio32@gmail.com`.
2. Pega el enlace en:
   Google Cloud Console → proyecto **studio32-agent** (entra con
   `soporte.studio32@gmail.com`, `authuser=1`) → **Acceso a los datos** → campo
   *"Vínculo de YouTube"* → **Save**.
3. Desde ahí se envía la solicitud de verificación.

---

## 6. Estado dejado listo

- Certificado de `api.studio32.es` funcionando; la pantalla de permisos ya dice
  **studio32.es**, no el dominio de Railway.
- Permisos declarados en la consola; `calendar.events.owned` marcado como sensible.
- App en **Producción**. Privacidad, Condiciones y dominio autorizado (`studio32.es`)
  configurados y verificados en Search Console.
- Secreto del cliente rotado; el anterior, borrado.
- Agenda con una cita real (viernes 18, 10:00) y varias canceladas de pruebas. Si
  quieres el mes más limpio para el vídeo, dímelo y las quito de Supabase.

## 7. Pendiente, por orden

1. Grabar y subir el vídeo → enviar la verificación.
2. Añadir el enlace de Condiciones al pie de la portada (no lo toqué: `site/index.html`
   y las páginas por vertical tienen cambios tuyos sin commitear, y las verticales se
   generan con `generar-verticales.py`).
3. `Demos-Clientes/la-taberna-de-ruzafa/` está publicada con marcadores `{{...}}` sin
   rellenar. Sin enlazar y en noindex, pero accesible por URL.
4. Datos del tenant de ensayo: teléfono de relleno (`+34600000002`) y dirección sin
   definir.
5. Mientras Google no apruebe, **cualquier cliente que conecte ve la pantalla roja**.
   No enseñes el alta a un cliente real hasta entonces.
