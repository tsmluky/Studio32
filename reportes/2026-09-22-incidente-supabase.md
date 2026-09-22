# 22/09/2026 · Se borró `studio32-agent-platform` y se recompuso todo en `studio32-hub`

## Qué pasó

El 20/09 se había fusionado la base del Hub dentro de `studio32-agent-platform`,
para poder cerrar el proyecto sobrante de Supabase. La noche del 21/09 se borró
por error el proyecto equivocado: no el sobrante, sino `studio32-agent-platform`
mismo — el que acababa de recibir al Hub y donde vivían las tres organizaciones
reales del agente (`studio32`, `gh-dent`, `clinica-cobalto`).

## Por qué no fue un desastre

El agente nunca depende solo de Supabase. Cada escritura de conversación o de
reserva está envuelta en un `try/catch`: si Supabase falla, sigue funcionando
con un fichero en el volumen persistente de Railway (`/app/data`), que es
justo para lo que se montó en julio. La agenda real de citas es Google
Calendar, no la tabla de Supabase — eso también es una decisión de hace
semanas, no un parche de última hora.

Comprobado en vivo el 22/09, con la base todavía borrada: el agente seguía
respondiendo sin caerse; solo fallaba (y seguía sin bloquear nada) la
escritura a Supabase.

GH Dent, además, no es cliente activo desde el 09/09 — nunca respondió al
presupuesto — así que perder sus filas en esa base no afectaba a nadie real.

## Qué se perdió de verdad

- **Las cuentas de acceso**: las del panel (`info@studio32.es`) y las tres del
  Hub. Las contraseñas no se pueden recuperar porque solo se guardaban
  cifradas — hay que fijarlas de nuevo.
- **El registro interno de auditoría** (`audit_logs`) del panel.
- **La actividad del Hub entre el 20/09 y el 21/09** (leads aprobados, correos
  enviados, campañas nuevas, si las hubo en esa ventana): era la única pieza
  del ecosistema que dependía solo de esa base, sin fichero de respaldo.
  Todo lo anterior al 20/09 sigue intacto.

## Qué se hizo para recomponerlo

- El esquema completo del agente (organizaciones, contactos, conversaciones,
  citas, leads, config por tenant, credenciales de integración — 14 tablas,
  RLS en todas) se volvió a aplicar sobre `studio32-hub`, el proyecto que
  sobrevivió porque nunca se tocó.
- Se sembró de nuevo el tenant de demostración `clinica-cobalto` (script
  idempotente, cero trabajo manual) y se dio de alta la organización
  `studio32`.
- El agente en Railway y el Hub en Cloudflare se repuntaron a este proyecto.
- Falta repuntar el panel de clientes en Cloudflare y recrear las cuentas de
  acceso — ver la nota al pie de este reporte o `ESTADO.md`.

## Dónde estamos ahora

`studio32-hub` (ref `wwhinwxedcvpxprmcsta`) es el **único** proyecto de
Supabase de todo el ecosistema: agente, panel y Hub comparten la misma base.
Ya no hay un proyecto de repuesto al que volver si esto se repite — antes de
borrar cualquier proyecto de Supabase, confirmar el nombre y la referencia
dos veces, y preguntar primero si hay dudas.
