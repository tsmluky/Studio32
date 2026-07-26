# Estado actual · Agente de IA (foco: GH Dent)

> La foto de AHORA. Si lees una sola cosa, que sea esta. Última actualización: 26/07/2026.

## ✅ Hecho y probado en vivo

- El agente de GH Dent está **desplegado en producción** y se le puede hablar por
  WhatsApp (por ahora, por el número de pruebas de Twilio).
- **Personalidad a medida:** cercano, entiende el miedo del paciente, ofrece la
  valoración gratuita, no da precios ni confirma mutuas por chat, no diagnostica.
- **Reservas:** el agente crea la cita, comprueba que el hueco existe de verdad, y
  deja una nota para el equipo con el contexto del paciente.
- **Horarios correctos:** respeta el horario real (viernes solo mañanas) y no cita
  en días cerrados ni en fechas pasadas.
- La cita creada **se ve en el dashboard**.

## 🔧 En curso / decisiones que necesito

- **Aviso de reservas: ✅ FUNCIONANDO.** Cada reserva, cancelación o lead dispara un
  email desde `citas@studio32.es`. Durante las pruebas llega a
  `soporte.studio32@gmail.com`; al go-live se apunta al correo de la clínica
  (Gabriela). Probado de punta a punta (email "Delivered").
- **Nombre del agente:** sin nombre humano de momento. Pendiente de que Gabriela
  decida.

## ⏳ Pendiente para el go-live real (no para la demo)

- Verificar el número de GH Dent en **Meta** (para usar su propio WhatsApp, no el de
  pruebas).
- Conectar el **Google Calendar** de la clínica (ahora las citas van al dashboard,
  no a su calendario).

## 🎯 Siguiente gran paso

- Convertir el proceso "investigar negocio → crear personalidad a medida" en una
  **herramienta reutilizable**, para montar cada cliente nuevo en minutos.
