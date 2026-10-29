# Casos de uso: Médico

## CU-M1: Solicitar prueba diagnóstica

**Actor:** Médico

**Versión:** 1.0.0

**Prioridad:** Alta (la citación, los informes y el seguimiento dependen de las solicitudes)

**Descripción:** El médico solicita una prueba diagnóstica para un paciente indicando la indicación clínica, la justificación y el nivel de prioridad (urgente, preferente u ordinario).

**Flujo principal:**

1. El médico inicia sesión y accede a "Nueva solicitud".
2. El médico selecciona al paciente.
3. El médico elige el tipo de prueba del catálogo.
4. El médico introduce la indicación clínica, la justificación y el nivel de prioridad.
5. El médico envía la solicitud.
6. El sistema registra la solicitud en estado "pendiente de cita" y la deja disponible para Admisión.
7. El sistema confirma al médico que la solicitud se ha registrado.

**Criterios de aceptación:**

- No se puede enviar una solicitud sin indicación clínica, justificación ni prioridad.
- El médico solo puede solicitar pruebas que se encuentren dentro del catálogo de tipos de prueba.
- La solicitud queda asociada al médico que la prescribe y al paciente.
- Toda solicitud nueva queda visible para Admisión con su prioridad.

**Estimación:** 8h sin IA / 5h con IA

---

## CU-M2: Prescribir pruebas de seguimiento

**Actor:** Médico

**Versión:** 1.0.0

**Prioridad:** Alta (depende de CU-M1 y CU-M5; CU-P5 y las nuevas citas dependen de ella)

**Descripción:** El médico prescribe pruebas de seguimiento con una periodicidad determinada (control de nódulos, revisiones oncológicas, cribados) y el sistema genera automáticamente la necesidad de nuevas citas.

**Flujo principal:**

1. El médico accede a "Seguimiento" y elige "Nuevo seguimiento".
2. El médico selecciona al paciente y el tipo de prueba.
3. El médico indica la periodicidad y la fecha de la primera prueba.
4. El médico confirma la prescripción.
5. El sistema registra el seguimiento.
6. El sistema genera la solicitud de la primera prueba, pendiente de cita.
7. El sistema genera una nueva solicitud cada periodo, mientras el seguimiento siga activo.

**Criterios de aceptación:**

- No se puede prescribir un seguimiento sin periodicidad.
- Cada periodo cumplido genera una nueva necesidad de cita, visible para Admisión.
- Si una prueba de seguimiento termina como Incidente, no se genera la siguiente solicitud hasta que la prueba se repita y se realice.
- El paciente ve el seguimiento en su apartado "Mi seguimiento".
- El médico puede finalizar o modificar un seguimiento que haya prescrito.

**Estimación:** 6h sin IA / 4h con IA

---

## CU-M3: Gestionar y consultar solicitudes y agendas

**Actor:** Médico

**Versión:** 1.0.0

**Prioridad:** Media (depende de las solicitudes y de la gestión de citas de Admisión)

**Descripción:** El médico consulta el estado de sus solicitudes y las agendas de realización disponibles.

**Flujo principal:**

1. El médico accede a "Mis solicitudes".
2. El sistema muestra sus solicitudes con su estado (pendiente de cita, citada, realizada, cancelada).
3. El médico selecciona una solicitud.
4. El sistema muestra el detalle: datos de la solicitud, fecha de la cita si existe y sala o equipo asignado.
5. El médico puede acceder a "Agendas" para consultar los huecos disponibles de realización.
6. El médico puede cancelar o modificar una solicitud que aún no se ha realizado.

**Criterios de aceptación:**

- El médico solo ve sus propias solicitudes, no la de otros médicos.
- Se puede filtrar por estado, por prioridad y por fecha asignada o sin asignar.
- La agenda es de consulta: la asignación de citas la realiza Admisión.
- Una solicitud ya realizada no se puede modificar ni cancelar.

**Estimación:** 6,5h sin IA / 3,5h con IA

---

## CU-M4: Crear y consultar informes e imágenes

**Actor:** Médico

**Versión:** 1.0.0

**Prioridad:** Alta (depende de CU-M5; CU-P2 y CU-P3 dependen de los informes)

**Descripción:** El médico crea el informe de una prueba realizada y consulta los informes y las imágenes de sus pacientes.

**Flujo principal:**

1. El médico accede a "Pacientes" y selecciona uno.
2. El sistema muestra las pruebas realizadas de ese paciente.
3. El médico selecciona una prueba y puede ver las imágenes de ésta.
4. Si la prueba no tiene informe, el médico lo redacta y lo guarda.
5. El sistema registra el informe y lo marca como disponible.
6. El sistema genera el aviso de informe disponible para el paciente.
7. Si el informe ya existe, el médico puede consultarlo.

**Criterios de aceptación:**

- Solo se puede crear un informe de una prueba ya realizada.
- Cada prueba tiene un único informe, que una vez publicado es definitivo.
- Un informe publicado queda asociado a su autor y su paciente, con fecha y hora.
- Cada acceso a informes e imágenes queda registrado (médico, paciente, fecha y hora) para su auditoría.

**Estimación:** 9h sin IA / 5h con IA

---

## CU-M5: Registrar realización de la prueba e incidencias

**Actor:** Médico

**Versión:** 1.0.0

**Prioridad:** Alta (depende de las citas; informes, historial y seguimiento dependen de él)

**Descripción:** El médico registra que una prueba se ha realizado y anota las incidencias ocurridas durante su ejecución, en caso de haberlas.

**Flujo principal:**

1. El médico accede a sus pruebas citadas del día.
2. El médico selecciona la prueba que se va a realizar o se ha realizado.
3. En el caso de no haber incidencias, el médico la marca como realizada e introduce la fecha y hora.
4. Si ha habido incidencias (paciente ausente, fallo de equipo, repetición de la prueba), indica el tipo, las describe y marca la prueba como Incidente, indicando también si es necesario repetir la prueba o no.
5. El médico guarda el registro.
6. El sistema actualiza el estado de la prueba y lo muestra en el historial del paciente.
7. Si hay que repetir la prueba, el sistema genera una nueva solicitud pendiente de cita, con la misma prioridad.
8. El sistema genera el aviso de "Prueba realizada" al paciente en caso de salir bien, o "Incidente en su prueba" en caso de haber algún incidente.

**Criterios de aceptación:**

- Solo se pueden registrar pruebas que tengan cita asignada.
- Una incidencia no se puede guardar sin descripción.
- Una prueba registrada como realizada o como Incidente aparece en el historial del paciente.
- El paciente ve de un Incidente solo el tipo y la fecha. El personal responsable ve además la descripción completa.

**Estimación:** 7h sin IA / 4h con IA

---

## CU-M6: Consultar estadísticas de solicitudes

**Actor:** Médico

**Versión:** 1.0.0

**Prioridad:** Baja (no bloquea a ningún otro caso de uso)

**Descripción:** El médico consulta estadísticas de sus solicitudes: tiempos de espera, uso de recursos y adherencia al seguimiento.

**Flujo principal:**

1. El médico accede a "Mis estadísticas".
2. El médico selecciona un periodo.
3. El sistema calcula y muestra los tiempos de espera, el uso de recursos y la adherencia al seguimiento.
4. El médico puede filtrar por tipo de prueba o por prioridad.

**Criterios de aceptación:**

- El médico solo ve estadísticas de sus propias solicitudes.
- El tiempo de espera se calcula desde la solicitud hasta la realización de la prueba.
- La adherencia al seguimiento es la proporción de pruebas de seguimiento realizadas respecto a las previstas.
- Si no hay datos en el periodo, se muestra un mensaje.

**Estimación:** 4h sin IA / 2h con IA
