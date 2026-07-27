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

1. **El agente olvida las citas al actualizar el sistema.** Se guardan en un archivo
   que se borra en cada despliegue → riesgo de citar a dos pacientes a la misma hora.
   *Solución:* disco permanente en el servidor + conectar Google Calendar.
2. **Google Calendar sin conectar.** Falta la cuenta técnica de Studio32 y que la
   clínica comparta su calendario con ella. Es lo que además resuelve el punto 1.

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
