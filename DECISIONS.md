## D-002 · Estructura Maven multimódulo
Fecha: 22/10 · It. 0 · Acta: 22/10 · Issue: #4
Contexto: hay dos aplicaciones, servidor y cliente, en un mismo repositorio.
Decisión: pom padre radiodiagnostico con dos módulos: servidor y cliente.
Alternativas: dos repositorios; un solo módulo.
Motivo: un mvn verify construye todo y las versiones se fijan una vez en el padre.
Consecuencias: cada módulo con su versión; al cambiar la del padre, actualizar <parent>.

D-003 · Estrategia de ramas: Git Flow
Fecha: 27/10 · It. 0 · Acta: 27/10 · Issue: #
Contexto: el desarrollo es en equipo (7 personas) y cada componente se construye en una iteración distinta.
Decisión: se usa Git Flow (main, develop, feature/*, release/*, hotfix/*). No se hace commit directo en main; la integración se hace mediante pull request aprobado.
Motivo: separa el trabajo de cada iteración y el versionado de las releases.
Consecuencias: toda tarea va en una rama feature/* asociada a un issue; hace falta un revisor por cada PR.

D-004 · Arquitectura cliente-servidor con varios clientes
Fecha: 27/10 · It. 0 · Acta: 27/10 · Issue: #
Contexto: el sistema debe usarse desde distintos dispositivos.
Decisión: un servidor y como mínimo dos clientes en el repositorio: escritorio y web. Cliente móvil opcional.
Alternativas: un único cliente; aplicación monolítica.
Motivo: cumple el requisito de múltiples clientes y mantiene la lógica en el servidor.
Consecuencias: los clientes se comunican con el servidor mediante interfaces bien definidas; el cliente web se añade como nuevo módulo.

D-005 · Autenticación diferenciada por tipo de usuario
Fecha: 27/10 · It. 0 · Acta: 27/10 · Issue: #
Contexto: hay cuatro tipos de usuario (paciente, médico, administrativo, administrador) con distintos permisos.
Decisión: la forma de autenticación depende del tipo de usuario.
Alternativas: mecanismo único para todos.
Motivo: los perfiles clínicos y administrativos requieren más control que los pacientes.

D-006 · Entorno de desarrollo: Java en Visual Studio Code 
Fecha: 27/10 · It. 0 · Acta: 27/10 · Issue: #
Contexto: el enunciado admite varios entornos y agentes de IA.
Decisión: el equipo trabaja con Visual Studio Code y en Java.
Motivo: es el entorno donde solemos trabajar y es el recomendado en el enunciado.
Consecuencias: toda la configuración compartida (formato, extensiones) debe ser compatible con VS Code.

D-007 · Documentación: decisiones en .md y todo en la Wiki
Fecha: 27/10 · It. 0 · Acta: 27/10 · Issue: #
Contexto: el enunciado exige trazabilidad y que la wiki sea la guía de lectura.
Decisión: las decisiones se registran en DECISIONS.md y todo lo que se haga se documenta y enlaza desde la Wiki.
Motivo: facilita la corrección y deja una única fuente de verdad.
Consecuencias: cada decisión nueva exige actualizar DECISIONS.md, la página Decisiones de la wiki y el acta.