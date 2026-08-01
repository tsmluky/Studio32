# Estado actual · Agente de IA (foco: GH Dent)

> La foto de AHORA. Si lees una sola cosa, que sea esta. Última actualización: 27/07/2026.

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
2. **Google Calendar sin conectar.** No existe todavía la cuenta técnica de Google.
   Plan acordado: el calendario lo crea Studio32 (uno por cliente) y se invita por
   correo a la clínica, que solo tiene que aceptar.
   ⚠️ **Antes hay que preguntar a la clínica dónde lleva su agenda hoy**: el agente
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
