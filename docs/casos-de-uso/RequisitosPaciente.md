# CU-P1: Gestionar citas
- Actor: Paciente
- Versión: 1.0.0
- Prioridad: Alta (notificaciones, historial y seguimiento dependen de las citas)
- Descripción: El paciente consulta sus citas programadas y puede: confirmarlas, solicitar un cambio o cancelarlas.
- Flujo principal: 
	1. El paciente inicia sesión y accede a "Mis citas".
  	2. El sistema muestra sus citas programadas.
  	3. El paciente selecciona una cita y elige una acción: confirmar, solicitar cambio o cancelar.
  	4. El sistema registra la acción y avisa a Admisión si requiere su gestión.
  	5. El sistema muestra al paciente el nuevo estado de la cita.
- Criterios de aceptación:
	- El paciente solo ve sus propias citas.
 	- Confirmar, solicitar cambio y cancelar actualizan el estado de la cita.
	- Cada solicitud de cambio o cancelación queda visible para Admisión.
- Estimación: 7h sin IA / 4.5h con IA


# CU-P2: Notificaciones y recordatorios
- Actor: Paciente
- Versión: 1.0.0
- Prioridad: Media (depende de las citas y de los informes)
- Descripción: El paciente recibe avisos de sus citas, de la preparación previa y de la disponibilidad de sus informes.
- Flujo principal:
	1. El sistema detecta un evento que requiere aviso.
	2. El sistema genera la notificación con los datos necesarios.
	3. El sistema envía la notificación al paciente.
	4. El paciente accede a "Mis notificaciones" y la consulta.
	5. El sistema marca la notificación como leída.
- Criterios de aceptación:
	- El paciente solo recibe notificaciones propias.
	- Se genera un recordatorio antes de cada cita programada.
 	- Se avisa al paciente cuando un informe suyo está disponible.
  	- Las notificaciones leídas quedan marcadas como tal.
- Estimación: 3h sin IA / 2h con IA


# CU-P3: Consultar historial de pruebas
- Actor: Paciente
- Versión: 1.0.0
- Prioridad: Media (depende de las citas y de los informes)
- Descripción: El paciente consulta la lista de pruebas diagnósticas que se le han realizado y accede al informe de cada una cuando está disponible.
- Flujo principal:
	1. El paciente accede a "Mi historial".
  	2. El sistema muestra sus pruebas realizadas.
  	3. El paciente selecciona una prueba.
  	4. El sistema muestra el detalle de la prueba y su informe, si existe. Si no existe, enseña un mensaje.
- Criterios de aceptación:
  	- El paciente solo ve sus propias pruebas.
  	- Solo aparecen pruebas ya realizadas, ordenadas de la más reciente a la más antigua.
  	- El informe solo se muestra si está disponible.
- Estimación: 4h sin IA / 2.5h con IA


# CU-P4: Comunicar incidencias y responder encuestas
- Actor: Paciente
- Versión: 1.0.0
- Prioridad: Baja (no bloquea a ningún otro caso de uso)
- Descripción: El paciente comunica incidencias relacionadas con sus citas o pruebas y responde encuestas de satisfacción sobre el servicio recibido.
- Flujo principal:
	1. El paciente accede a "Incidencias y encuestas".
 	2. El paciente elige comunicar una incidencia o responder una encuesta.
 	3. Si comunica una incidencia, describe el problema y lo asocia a una cita o prueba.
	4. Si responde una encuesta, valora la prueba realizada y puede añadir un comentario.
  	5. El paciente envía el formulario.
  	6. El sistema lo registra y confirma al paciente que se ha recibido.
- Criterios de aceptación:
  	- Una incidencia no se puede enviar sin descripción.
  	- El paciente solo puede responder encuestas de pruebas que se le han realizado.
  	- Cada prueba se puede valorar una sola vez.
  	- Las incidencias y las encuestas quedan registradas y visibles para el personal responsable.
- Estimación: 4h sin IA / 2.5h con IA


# CU-P5: Consultar pruebas de seguimiento y revisiones periódicas
- Actor: Paciente
- Versión: 1.0.0
- Prioridad: Media (depende de las citas y de la prescripción del médico)
- Descripción: El paciente consulta las pruebas de seguimiento y revisiones periódicas que su médico le ha prescrito
- Flujo principal:
	1. El paciente accede a "Mi seguimiento".
  	2. El sistema muestra sus pruebas de seguimiento (tipo de prueba y próxima fecha prevista).
  	3. El paciente selecciona una prueba.
  	4. El sistema muestra su detalle.
- Criterios de aceptación:
  	- El paciente solo ve su propio seguimiento.
  	- Cada prueba muestra su próxima fecha prevista.
  	- Se indica si la próxima revisión ya tiene cita asignada o está pendiente de ella.
- Estimación: 5h sin IA / 3h con IA
