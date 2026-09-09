# El camino — de cero clientes a un flujo que aguanta

> Escrito el 09/09/2026, en frío, después de repasar los ocho repos.
> Decisiones que ordenan todo esto: **el agente va primero y el QR en paralelo**, y
> **se sale a ofrecer en persona, puerta a puerta**.

## La regla que manda sobre las demás

**No se sale a vender lo que no se puede entregar en una semana.**

Hoy, si mañana un dueño dice que sí, no se le puede dar el producto: el número de
WhatsApp de Studio32 lleva desde julio en "Pendiente" en Meta, sin verificar. Vender
antes de arreglar eso no es ser valiente, es firmar una promesa que no se cumple, y con
el primer cliente eso no se recupera.

Por eso el orden de abajo no es por dificultad ni por gusto: es por lo que se rompe
primero si sale bien.

---

## Carril 0 · Cerrar lo que quedó abierto

Es media sesión y quita ruido de encima. Nada de esto es construir.

- **Los diez cambios sin commitear de `studio32-agent`**: la skill `montar-demo`, la
  plantilla `templates/estetica/` y el cambio de raíz de tenants al volumen. Es trabajo
  bueno del 08/09 que hoy solo existe en este portátil.
- **`reportes/2026-09-04.md` y `ESTADO.md`** llevan cinco días sin subir. El equipo no
  ve la sesión de las siete ciudades.
- **Rotar los `owner.token`** de `studio32` y `barberia_demo` y sacarlos a variables de
  entorno. El repo es público desde el 25/08 y esos tokens dan permisos de dueño. Sacar
  los archivos del control de versiones no borra lo que ya está en el historial.
- **Poner una `OPENAI_API_KEY` barata en el `.env` local.** Sin ella los doce evals de
  ayer caen al proveedor mock y no valen para nada. Una pasada cuesta céntimos.

---

## Carril 1 · Que el producto aguante

**Hechas las tres primeras capas el 09/09. Queda la cuarta.**

Cuatro capas, de dentro hacia fuera. Cada una responde a una pregunta distinta:

**1. ¿Tiene criterio?** → HECHO. `npm run eval`: quince casos contra el arquetipo
dental versionado (antes iban contra el tenant de un cliente que ya no está, así que
solo funcionaban en una máquina). Estable en tres pasadas seguidas. Comprueba que no
da precios que no tiene y sí da los que sí, que no confirma mutuas, que conoce su
horario, que no diagnostica, que no se cree a quien dice ser la dueña.

**2. ¿Funciona la fontanería?** → HECHO. `npm run test:agent` existe de verdad: siete
casos que mantienen una conversación completa y comprueban **la agenda**, no las
frases. Los cuatro comandos fantasma del `package.json` se han quitado.

**3. ¿Funciona *lo desplegado*?** → HECHO. `npm run test:agent:prod` pasa el mismo
guion contra Railway, y `/health` dice con qué modelo corre, cuántos tenants ve y si
el volumen se puede escribir. Siete de siete en producción.

**4. ¿Nos enteramos antes que el cliente?** → PENDIENTE. `/health` existe pero nadie
lo mira. Si el agente deja de responder un domingo por la tarde, lo sigue descubriendo
el paciente que quería cita. Hace falta algo que lo consulte cada X minutos y avise a
una persona.

**Lo que encontró el carril nada más existir** (los tres arreglados, con prueba propia
para que no vuelvan):

- El agente **confirmaba citas que no había creado**. "Listo, ya tienes tu cita el
  jueves a las 09:30", agenda vacía. Ahora hay un guard en código: si lo dice, tiene
  que existir, y a esa hora.
- **Cualquiera podía cancelar la cita de otro** dando su teléfono por chat.
- En la demo pública, **dos visitantes con el mismo teléfono se pisaban**.

**Cómo se sabe que este carril está hecho:** se puede desplegar un viernes por la tarde
sin miedo. Falta la capa 4 para poder decirlo del todo.

---

## Carril 2 · Que el "sí" no se caiga (esto va antes de salir a la calle)

- **El número de Meta.** `+34 694 29 31 66` está en "Pendiente": nunca completó la
  verificación por OTP y hace falta la SIM a mano. La verificación de empresa sigue "en
  revisión". Hay que cerrar el circuito entero con **nuestro propio número** antes de
  prometérselo a nadie, y dejar escrito cuánto se tarda de verdad.
- **Google Calendar.** No existe la cuenta técnica. El plan ya está acordado (un
  calendario por cliente, creado por Studio32, invitación al negocio). Falta hacerlo una
  vez, de principio a fin, con un calendario de prueba.
- **Los avisos al correo del cliente**, que hoy van a Studio32 a propósito.
- **Precio, contrato y cobro.** La web no publica cifra a propósito, y para correo está
  bien. Para puerta a puerta no: hace falta una horquilla que se pueda decir en voz alta
  sin dudar. Anclas del mercado español que ya tenemos: 200 €/mes + 350 € de alta como
  suelo del sector; el techo, muy por encima.
- **De demo a real.** Hoy `/onboarding` crea el tenant desde plantilla. Falta el paso de
  convertir el tenant de la visita en el cliente de verdad sin rehacerlo.

---

## Carril 3 · El kit de visita

Esto es lo que se lleva encima al entrar por la puerta. Antes de la primera visita tiene
que estar entero, no a medias.

**La huella se unifica, y de ahí sale todo.** Hoy hay dos investigaciones del mismo
negocio hechas por separado: la de `/prospectar` (que sí exige detalle ancla, voz del
cliente con cita literal, huecos digitales y nivel de confianza) y la de `montar-demo`,
que solo lee la web. Es la misma materia prima y tiene que ser un solo trabajo:

> Una investigación por negocio → alimenta el correo **y** el tenant de la demo **y**,
> si firma, su arquetipo de cliente.

Eso es `montar-demo` v2: en vez de leer la web y rellenar, consume la huella completa
(web con Crawl4AI, reseñas con cita y autor, horarios reales, qué le falta) y produce el
tenant. Las reglas duras que ya tiene —precio `null` salvo cifra explícita, solo nombres
publicados, anotar la fuente de cada dato— se quedan tal cual: son lo que permite hablar
con seguridad delante del dueño.

**Lo demás del kit:**

- **La demo en el móvil**, con el tenant de ESE negocio. Y enseñando criterio del
  oficio, no "una IA que contesta 24/7": eso ya lo regala Meta y no impresiona a nadie.
- **Su landing personalizada**, para que la mire luego y se la enseñe al socio.
- **El manual de uso.** No existe. Es post-venta, pero enseñarlo en la visita es lo que
  separa "un chico con una idea" de "un producto".
- **El guion de la conversación**, que ya está decidido: las preguntas de la web —de
  quién es el número, si reserva sobre la agenda real— planteadas como *"pregúntale esto
  a cualquiera, nosotros incluidos"*.

---

## Carril paralelo · Agua Salada (la carta por QR)

Restaurante real en el Cabanyal, con acceso. Es la mejor carta que tenemos: un piloto de
verdad, no una maqueta.

**Primero, y antes de tocar nada: el acuerdo con el dueño.** Trabajar allí no es lo
mismo que tener permiso para cambiar la carta y usar las fotos como portfolio. Hay que
dejar claro si esto es un favor interno o un caso de estudio de Studio32 con derechos de
uso. Si queda ambiguo y luego se quiere enseñar, hay problema.

**Tres platos, no diez.** Los de más margen. Se valida el flujo completo con esos y solo
después se escala.

**Coste cero, y no por apretarse el cinturón.** El efecto que quieres —los ingredientes
cayendo y el plato montándose— es justo lo que peor hacen los modelos de vídeo, y justo
lo que mejor se hace por capas: fotos propias, recorte de cada ingrediente y animación
con GSAP en la propia web app. Es el mismo motor que ya usa `studio32-marketing` para
los vídeos (HTML + CSS + GSAP), así que no hay herramienta nueva que aprender, se
controla fotograma a fotograma y no cuesta un céntimo. Los recortes se hacen en local
con `rembg`, que va sobrado en la 1080. Las APIs de vídeo se quedan para micro-detalles
(vapor, un brillo) el día que haya presupuesto, y con los tiers gratuitos diarios da
para un plato al día.

Lo que sí decide el resultado es **la foto base**: sin una buena fotografía, ninguna
animación arregla nada. Media tarde de luz natural bien aprovechada vale más que
cualquier modelo.

**Se despliega en Cloudflare Pages**, que es donde ya viven el Hub y el dashboard.

**Y se mide antes de escalar:** unidades vendidas de esos tres platos, dos o tres
semanas, contra el periodo anterior. Sin ese número no hay caso de estudio que vender.

---

## Lo que NO se hace hasta que alguien pague

Escrito aquí para poder decir que no señalando un archivo:

Remotion, Langfuse, Chatwoot, el flujo completo de spec-kit, RestaurantOS, verticales
nuevas del agente, y cualquier función nueva del Hub que no sea aprobar correos.

De spec-kit se roba una sola cosa: **la constitución**. Un archivo corto de reglas que no
se saltan, y la primera es esta línea.

---

## Cómo evolucionan las herramientas

Tres reglas, para que crezcan con nosotros en vez de acumularse:

1. **Una herramienta nace de un dolor que ya ha pasado tres veces**, no de una idea
   buena. `/prospectar` nació así. `montar-demo` todavía no ha pasado esa prueba: se
   escribió antes de la primera visita.
2. **Cuando dos herramientas piden el mismo dato, se unen.** La huella es el caso de
   ahora mismo.
3. **Cada mejora interna se traduce a una frase que le dice algo al dueño.** Si no se
   puede, probablemente no tocaba hacerla.

---

## El orden, sin adornos

1. Carril 0 entero. Media sesión.
2. Meta: verificar el número propio de punta a punta. Hasta aquí, no se sale a la calle.
3. Evals por vertical, un smoke que exista de verdad, y un aviso de caída.
4. Kit de visita: huella unificada, `montar-demo` v2, manual, precio.
5. Primera visita en persona. Y con ella, los 32 correos del Hub dejan de esperar.
6. Agua Salada avanza en los huecos, empezando por hablar con el dueño.
