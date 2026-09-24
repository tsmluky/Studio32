# 24/09/2026 · Clips: seguimos con Jev, y dejamos la puerta abierta

**Qué se probó.** Laya, una alternativa open source a Jev (el "cerebro" que decide
qué momentos de un vídeo merecen ser clip). La idea era tenerlo en casa, poder
entrenarlo con nuestros datos y poder decir que el modelo es nuestro.

**Qué salió.** Funciona en nuestro ordenador y se puede enchufar sin tocar nada más,
pero elige peor que Jev. Sobre 37 vídeos de viajes, Jev acierta momentos mejores que
el reparto al azar en 33 de 37 vídeos; Laya, en 24 sin entrenar y en 27 entrenada con
datos de audiencia de YouTube. Usar los dos a la vez no mejora a Jev solo. Y es mucho
más lento: lo que Jev hace en minutos por API, Laya lo tarda más de una hora en local.

**Qué se decidió.** Seguimos con Jev. Es rápido, casi gratis y no hay que mantener
máquinas. Laya se aparca hasta que tengamos algo que Jev no tiene: cientos de votos
nuestros en la Mesa sobre qué clips publicaríamos.

**Por qué importa.** Ahora cambiar de motor es cuestión de una tarde: el código acepta
cualquier motor compatible con un solo ajuste, y hay una prueba fija que compara
cualquier motor nuevo con Jev con un comando. Si mañana sale algo mejor, lo sabremos
con números, no con impresiones.

**Un límite legal que hay que saber.** El contrato de TypeSafe (quien hace Jev) prohíbe
usar sus respuestas para entrenar un modelo que lo imite. Si algún día tenemos modelo
propio, tendrá que aprender de nuestros votos y de los resultados reales de los clips,
nunca copiando a Jev.

**De paso.** La batería de comprobaciones automáticas del motor se estaba saltando 19
de sus 170 pruebas sin avisar. Arreglado: ahora corren todas y pasan.

**Pendiente.**
- Aprobar el cambio en GitHub (rama `motor-decision-intercambiable`).
- Lo importante de verdad: la revisión a ciegas del piloto de Wooomygaaaad. Hay 108
  propuestas de clips de 7 vídeos preparadas desde el 23/09 y todavía nadie las ha
  votado. Es la prueba que dice si el producto sirve.
