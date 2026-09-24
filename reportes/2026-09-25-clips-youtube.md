# 25/09/2026 · Clips: YouTube ya funciona de principio a fin

**Qué se hizo.** Hasta ayer la web solo aceptaba directos de Twitch. Ahora se puede
pegar un vídeo de YouTube en clip.studio32.es y el sistema lo analiza, propone
momentos, los prepara para revisarlos en vertical en la Mesa y exporta el clip final.

**Cómo se comprobó.** Con un vídeo real de Wooomygaaaad: salieron 12 momentos, los 12
se pueden ver ya en la Mesa como Short vertical con subtítulos, y uno se exportó a un
clip de 1080×1920 listo para subir. En los vlogs el encuadre sigue la cara de quien
habla (en los directos de CS2 sigue siendo webcam arriba y partida abajo).

**Qué había que arreglar.** Tres cosas impedían YouTube aunque la web aceptara el
enlace: la base de datos solo dejaba analizar y exportar Twitch, faltaba una
actualización de la base de datos que el motor necesita para trabajar (por eso los
momentos de CS2 tampoco tenían vídeo preparado; ya lo tienen), y el render final
fallaba porque YouTube ya sirve imagen y sonido por separado.

**Qué hay que saber.**
- El motor corre en el ordenador de sobremesa de Pancho. Si ese ordenador se apaga,
  los vídeos se quedan en cola hasta que vuelva a arrancarse (`ejecutar-worker.ps1`).
- YouTube a veces corta las descargas cuando se hacen muchas seguidas; el sistema ya
  reintenta solo.
- En la prueba se dejó un voto "Sí" y un clip exportado en la cuenta de Luky (gastó
  1 crédito).

**Pendiente.** Que el motor arranque solo al encender el ordenador, y la revisión
ciega del piloto de Wooomygaaaad.
